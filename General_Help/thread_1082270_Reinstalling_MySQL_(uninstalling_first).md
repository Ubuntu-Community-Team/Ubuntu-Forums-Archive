---
title: "Reinstalling MySQL (uninstalling first)"
date: 2009-02-27
forum: General Help
---

### Post by BramWillemsen on 2009-02-27
Hello everybody,

Yesterday i finally recieved my laptop that i intend to use for programming. I installed Ubuntu, but I'm not good at it yet. I use guides for every step that i make in the terminal. In the end i do manage to get most things working, but mysql is an exception.

The mysql book that I'm using suggested me to download the most recent server and client rpm files. when i did this i found out that ubuntu cannot treat these. A website suggested to convert them into .deb using alien. Afterwards sudo could be used to install them. Well i did this, and i try to log in into mysql but i get some strange error concerning files.

I suddenly found out that ubuntu already had (parts ?) of mysql installed. But mysql is really messed atm. So now i'm trying to find a way to get rid of all the mysql stuff to do a clean install after (maybe use a tar file instead so i dont have to use alien). The synaptic package manager does show anything mysql related though (when i type mysql nothing appears). When i tried to use apt-get remove i think i only managed to remove a part of it.

Does anyone know how i can get rid of all the mysql remnants on the system? Both the stuff that was already installed and the stuff that i tried to install? I guess that's a requirement before I can do a clean install again. I don't even know how much is left on my system and how i can find that out. This is probably a dumb question, but I am really stuck. Linux is really an interesting environment, but the learning curve is very steep.

Thanks for the help and kind regards :)

Bram

---

### Post by BramWillemsen on 2009-02-27
the post dropped down to the second page. Still hoping for some guidance. Thanks !!

---

### Post by geirha on 2009-02-27
First of all, always search the repositories for software before installing from other places. The versions of mysql-client and mysql-server in the repositories aren't the newest, but they should be new enough for your book, and any security holes and bugs that are found will be corrected by updates. RPM packages should be avoided at all cost. The systems that use RPM packages are usually differently set up than systems that use deb packages, and that can really mess things up. 

repositories > deb-package > build from source > rpm

This terminal command should list all installed mysql-packages: 
```
aptitude search '~i mysql'
```

Synaptic should show them too, but I'm not sure how the quick search works. You'll probably find them if you use the "full search" (the quick search was added in Intrepid, I'm using the previous release, Hardy, so I'm not sure where you find the "full search" in Intrepid)

From the terminal, you can remove the packages and also purge any configuration they may have stored with the command:
```
sudo aptitude purge *package-name*
```
Of course, you can do that in synaptic as well.

Purge the mysql-package you installed from the aliened rpm, then reinstall mysql-client with ```
sudo aptitude reinstall mysql-client
``` and then install mysql-server.

After installing the mysql-server package, running ```
mysql -u root
``` as an admin user should connect you to the server as root. (If a user can run commands sudo, it's an admin user)

---

### Post by BramWillemsen on 2009-02-27
Thanks so much!!! It appears that i used the quick search all the time. I removed all installed parts in synaptic and then installed mysql-client and server again. Its 5.0.6 though and not 5.1 , but i guess i'll try to update it again when i have some more linux experience.

I've been struggling with it for hours and it appears to be that simple ;) Thanks a lot for taking the time to point it out.

kind regards, 

Bram

edit:

It seems like there is one problem left though. I can use mysql -u root -p etc to modify databases, but i cannot start mysqld. Whenever i type mysqld i get

InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log fil

etc etc, endless iteration. When i go to the system monitor i do not see any mysql process running in the background. The problem remains the same after rebooting. I'm used to having mysqld in the background in windows, the behavious i just described seems to be wrong.


I killed mysqld and restarted it. I guess it does not show up in my process list for some reason.

---

### Post by geirha on 2009-02-27
It is started by an init script when you boot (and also when you (re)install the package). The proper way to stop and start it is 
```

sudo /etc/init.d/mysql stop
sudo /etc/init.d/mysql start
# or both at once
sudo /etc/init.d/mysql restart

```

/etc/init.d/mysql is a script, so open it in a text editor and have a look. It does some checks to see if mysqld is already running, then runs /usr/bin/mysqld_safe in when you give the start argument.

---

### Post by asadqamber on 2009-07-13
i tried restarting the mysql Database. it stops OK but starting fails.
I am unable to install mysql 5.1 on Ubuntu 9.04
Every time I try installing mysql the database just does not start.

any idea what I should do to get mysql working?

---

