# Django + PostgreSQL installation guide (Ubuntu 16.04)

```
$ sudo apt-get update
$ sudo apt-get upgrade

$ sudo apt-get install postgresql postgresql-contrib libpq-dev pgadmin3

$ sudo -u postgres createuser --superuser unixuser # unix username
$ sudo -u postgres psql

postgres=# \password unixuser

$ psql postgres -c "CREATE DATABASE projectname WITH ENCODING='UTF8' OWNER=unixuser CONNECTION LIMIT=-1;"

$ sudo pip3 install --upgrade pip
$ sudo pip3 install --upgrade Django
$ sudo pip3 install --upgrade psycopg2

$ django-admin startproject projectname

$ cd $HOME/projectname

$ python3 manage.py startapp appname
```

```
$ vim projectname/settings.py

DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'HOST': '127.0.0.1',
        'PORT': 5432,
        'NAME': 'projectname',
        'USER': 'unixuser',
        'PASSWORD': '******',
    }
}

...

TIMEZONE = 'America/Argentina/Buenos_Aires'
```

```
$ python3 manage.py migrate

$ python3 manage.py runserver
```


## pgAdmin 3 configuration

Open pgadmin3 > New server registration

- Name: 127.0.0.1
- Host: 127.0.0.1
- Port: 5432
- Maintenance DB: postgres
- Username: unixuser
- Password: ******
- Store password: YES
- Group: Servers

<OK>
