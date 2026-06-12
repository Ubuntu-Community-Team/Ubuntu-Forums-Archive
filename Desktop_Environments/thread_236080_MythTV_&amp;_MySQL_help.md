---
title: "MythTV &amp; MySQL help"
date: 2006-08-14
forum: Desktop Environments
---

### Post by phenolholic on 2006-08-14
Hello, I'm trying to install mythtv as per Hyams HOWTO, and when running mythtv-setup, I get the Database Configuration menu, and I entered my phpmyadmin login/password (along with hostname, database, database type, etc) , and it quits and displays the following error. I also verified that the login/password is indeed correct by logging in via localhost on firefox. The error is:

2006-08-14 06:59:44.324 Unable to connect to database!
2006-08-14 06:59:44.324 Driver error was [1/1049]:
QMYSQL3: Unable to connect
Database error was:
Unknown database 'mythconverg'

2006-08-14 06:59:44.324 Failed to init MythContext, exiting.



Anyone know what I'm doing wrong? Thanks in advance

---

### Post by Titus A Duxass on 2006-08-14
Normally during the installation you are asked for the admin password and nothing more.

Did you really have to enter all that other data, did it give you a separate screen or just one?

---

### Post by phenolholic on 2006-08-14
I entered the admin password during the installation. However, the login to my phpmyadmin is "root" not "admin" ...so when I ran mythtv-setup, it brought up the database configuration (by default it had admin as the login and the password i entered in the installation). i changed the login to "root" and entered the password (which is the same login/password i used to access phpmyadmin through localhost). in a nutshell, the login/passwd used in phpmyadmin (via localhost) doesnt work on the database configuration in mythtv-setup. the error message i get after termination of the database configuration was posted above.

---

### Post by mjziegle on 2006-08-14
The database can't be found which is most likely due to your backend not running.  Trying running mythbackend in a separate terminal.  If that gives an error post it here.  



> **phenolholic said:**
> Hello, I'm trying to install mythtv as per Hyams HOWTO, and when running mythtv-setup, I get the Database Configuration menu, and I entered my phpmyadmin login/password (along with hostname, database, database type, etc) , and it quits and displays the following error. I also verified that the login/password is indeed correct by logging in via localhost on firefox. The error is:

2006-08-14 06:59:44.324 Unable to connect to database!
2006-08-14 06:59:44.324 Driver error was [1/1049]:
QMYSQL3: Unable to connect
Database error was:
Unknown database 'mythconverg'

2006-08-14 06:59:44.324 Failed to init MythContext, exiting.



Anyone know what I'm doing wrong? Thanks in advance

---

### Post by phenolholic on 2006-08-14
I logged into the mythtv user account. This is what mythbackend reported when ran in the terminal:

2006-08-14 21:52:33.998 New DB connection, total: 1
2006-08-14 21:52:34.003 Unable to connect to database!
2006-08-14 21:52:34.004 Driver error was [1/1049]:
QMYSQL3: Unable to connect
Database error was:
Unknown database 'mythconverg'

2006-08-14 21:52:34.004 Failed to init MythContext, exiting.

apparently, it has something to do with mythconverg. Thanks in advance.

---

### Post by Titus A Duxass on 2006-08-15
I do not understand what you are entering, the requirement is only for the passwd, although the setup procedure has changed now.  There is no link to passwd, you have to click on the adminstration link:

Fire up Firefox and in the address bar, type "localhost". 
Click the "phpmyadmin" directory. 
Type in "root" in the login form, and no password. 

Find the link for editting localhost setup.
Look down the resulting page for the password field; type in what you want your MySQL password to be. 

After the password is set, click the "Back" link (not the Back button in your browser). Click on the "Reload MySQL" link. Now, to verify that you password works, login again, using "root" as the user and your MySQL password that you just set; it should work. Logout from phpMyAdmin. Now try to log back in to phpMyAdmin using "root" and this time, no password. It should not let you in; done. 

At this point, make sure you have logged out of phpMyAdmin. 

Then when you carry out the install MythTV steps:
During this install process, you will be prompted for the MySQL password. For this, type in the password that you have in the phpmyadmin configuration step that you completed a couple of steps ago. The installer will also try to start mythbackend, but don't worry if it does not start; we still have work to do.

---

### Post by phenolholic on 2006-08-15
Hello. I fixed the problem. I needed to create the mythconverg database through mysql. I did that and it finally worked. Ok here's another problem, I FINALLY got mythbackend and mythfrontend to load. However, when I try to go into View TV in myth's main menu, I get a menu saying

WARNING: something is already using /dev/dsp, retrying.

with two options, continue without audio & return to menu. i click 'continue without audio' and all of a sudden I get logged out of X (i see the CLI login). also, something to note, when I run mythbackend in a terminal, I get:

2006-08-15 03:57:57.776 New DB connection, total: 1
Starting up as the master server.
2006-08-15 03:57:57.785 New DB connection, total: 2
Error getting inputs for the capturecard.  Perhaps you have
forgotten to bind video sources to your card's inputs?
2006-08-15 03:57:57.797 New DB scheduler connection
bttv is defined, but isn't attached to a cardinput.
2006-08-15 03:57:57.799 mythbackend version: 0.18.1.20050510-1 [www.mythtv.org](www.mythtv.org)
2006-08-15 03:57:57.800 Enabled verbose msgs : important general
2006-08-15 03:57:59.799 Reschedule requested for id -1.
2006-08-15 03:57:59.806 Scheduled 0 items in 0.0 = 0.00 match + 0.00 place
2006-08-15 03:57:59.808 Seem to be woken up by USER


Notice the 'Error getting inputs for the capturecard.  Perhaps you have
forgotten to bind video sources to your card's inputs?' and the 'bttv is defined, but isn't attached to a cardinput.' ..maybe that's the reason. Any info would be greatly appreciated!

---

### Post by Titus A Duxass on 2006-08-15
Did you run mythtv-setup from the CLI first?

---

### Post by phenolholic on 2006-08-15
Yes I did. I added my capture cards, created a a video sources profile, and exited.

---

