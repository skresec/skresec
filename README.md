1. Prerequisites (don’t skip)

	Docker

	Docker Compose

	Git

	Python 3.9+ (for local scripts/tests)

Check:

docker --version
docker compose version

2. Start Airflow Locally (first time)

docker compose up airflow-init
docker compose up -d

3. Access UI:

http://localhost:8081
username: admin
password: admin

use incognito if not works

4. Testing DAG Parsing (critical)

Before pushing to Git:

docker compose exec airflow-scheduler airflow dags list
docker compose exec airflow-scheduler airflow dags test example_local_dag 2024-01-01

5. Git Workflow (clean)
git checkout -b feature/new-dag
# develop locally
docker compose exec airflow-scheduler airflow dags test your_dag 2024-01-01
git add dags/
git commit -m "Add new DAG"
git push origin feature/new-dag


