---
title: "MySQL"
date: 2006-08-15
forum: Desktop Environments
---

### Post by statue on 2006-08-15
I'm trying to set up a development environment to be able to test php scripts on my local machine. I have apache and php both installed and working but am unclear in how to set up mysql so the scripts can read and write to a database. The "add/remove programs" gui doesn't seem to have mysql...where do I download it from and how do I install it....also, is the mysql server the same thing as mysql? thanks

---

### Post by meng on 2006-08-15
I thought mysql was part of the standard Ubuntu installation. Anyway, I suggest using Synaptic or the command line to install stuff as you are not limited by the selections in Add/Remove Pgorams. I believe the mysql-server package will give you both a server and client.
[http://www.psychocats.net/ubuntu/installingsoftware.php](http://www.psychocats.net/ubuntu/installingsoftware.php)

---

### Post by statue on 2006-08-15
ok i was following this guide [here]("http://ubuntuguide.org/wiki/Dapper#How_to_install_MYSQL_Database_Server") and got stuck when it came to this step/command..."mysqladmin -h root@local-machine-name -u root password your-new-password". When I tried to enter the command I got the message that root@localhost was unable to connect to mysql. I tried a few more times and it told me to check to make sure the server was running which it was, so finally I got fed up with it and figured I would delete it and reinstall it and proceeded to use the command "sudo apt-get remove mysql-server". It said that it had removed it though the server was still running on port 3306 and continued to do so even after I deleted it. So then I reinstalled it again and proceeded to delete it, this time using the --purge command as well. It said it had removed mysql-server, I checked it again....still running. Basically, I want to know how to completely remove mysql and make the server stop running upon bootup without me having to manually stop it each time I restart and hopefully someone can tell me what I am doing wrong so that I can try to reinstall it yet again and get this thing working, its really frustrating me. thanks

---

### Post by meng on 2006-08-15
Okay, with the proviso that I don't quite follow the logic of what you propose, you could try the following advice:

1) mysql-server is a dummy/meta package, which has mysql-server-5.0 as a dependency. Removing mysql-server will not remove the dependency, mysql-server-5.0, you will have to do that manually.

2) If after doing this, you still notice that the system tries (unsuccessfully) to start mysqld at startup, then go into /etc/rc2.d and rename S20mysql and S21mysql-ndb to _S20mysql and _S21mysql-ndb respectively (then they will no longer start automatically at boot, but at the same time you can easily change things back to how they were if you change your mind).

---

### Post by statue on 2006-08-15
problem solved, thanks for the help

---

