A Few Problems and Solutions
======================
1. There is always namespace errors leading unrecognized tasks. Solution is to call task like 
`task = celery.send_task('app.long_task')`

2. Celery stops support windows after 4.0. It will cause some error like 'ValueError: not enough values to unpack (expected 3, got 0)'. Solution is to install eventlet and specify this in the work run command. `pip install eventlet` then `celery worker -A app.celery --loglevel=info --pool=eventlet`
See below link for details https://github.com/celery/celery/issues/4178#issuecomment-344176336
Using Celery with Flask

3. Remaining issue
The email part still not works for me. Didn't fix.

Original ReadMe
=======================

This repository contains the example code for my blog article [Using Celery with Flask](http://blog.miguelgrinberg.com/post/using-celery-with-flask).

The application provides two examples of background tasks using Celery:

- Example 1 sends emails asynchronously.
- Example 2 launches one or more asynchronous jobs and shows progress updates in the web page.

Here is a screenshot of this application:

<center><img src="http://blog.miguelgrinberg.com/static/images/flask-celery.png"></center>

Quick Setup
-----------

1. Clone this repository.
2. Create a virtualenv and install the requirements.
3. Open a second terminal window and start a local Redis server (if you are on Linux or Mac, execute `run-redis.sh` to install and launch a private copy).
4. Open a third terminal window. Set two environment variables `MAIL_USERNAME` and `MAIL_PASSWORD` to a valid Gmail account credentials (these will be used to send test emails). Then start a Celery worker: `venv/bin/celery worker -A app.celery --loglevel=info`.
5. Start the Flask application on your original terminal window: `venv/bin/python app.py`.
6. Go to `http://localhost:5000/` and enjoy this application!

For details on how this all works, see my article [Using Celery with Flask](http://blog.miguelgrinberg.com/post/using-celery-with-flask).
