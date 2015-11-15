#### Change Python Environment
```
source activate keweemedia
```

#### Start MySQL (if not launched at start)
```
mysql.server start
```
#### Move to project directory
```
cd Sites/myproject
```
#### Start lightweight web server
```
python manage.py runserver
```
Access the website at [http://127.0.0.1:8000/](http://127.0.0.1:8000/)

## Django commands

### Projects

```
python django-admin.py startproject <projectname>
```

Creates a `projectname` directory (which can be freely renamed) with the following file structure:

- manage.py
- projectname/
	- \_\_init\__.py
	- settings.py
	- urls.py
	- wsgi.py

### Apps

```
python manage.py startapp <appname> [<destination>]
```

### Migrations
Migrations are how Django stores changes to your models (and thus your database schema) - they’re just files on disk.

#### makemigrations
Use `makemigrations` to tell Django that changes have been made to the models of an app and that you’d like to **store the changes as a migration**.

```
python manage.py makemigrations <appname>
```
#### sqlmigrate
Use `sqlmigrate` to **observe the SQL** that a migration would run.

```
python manage.py sqlmigrate <appname> <migrationname>
```

#### migrate
Run `migrate` to **synchronize the changes on models (and migrations) with the database state**.

* No arguments: All migrated apps have all of their migrations run, and all unmigrated apps are synchronized with the database,
* `<appname>`: The specified app has its migrations run, up to the most recent migration. This may involve running other apps’ migrations too, due to dependencies.
* `<appname> <migrationname>`: Brings the database schema to a state where the named migration is applied, but no later migrations in the same app are applied. This may involve unapplying migrations if you have previously migrated past the named migration. Use the name zero to unapply all migrations for an app.

```
python manage.py migrate [<appname>] [<migrationname>]
```