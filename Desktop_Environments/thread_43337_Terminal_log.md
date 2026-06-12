---
title: "Terminal log"
date: 2005-06-21
forum: Desktop Environments
---

### Post by Dave_is_sexy on 2005-06-21
I'd like terminal to log everything for 24 hours in a text file somewhere. I just keep loosing info that I need as a newbie.

Can I tell it to do that?

Mythtv said this:

E: mythtv-database:  subprocess post-installation script returned error exit status 1
E: mythtv:  dependency problems - leaving unconfigured

and i missed the "show terminal" button and clicked the "autoclose" button and it closed, and now i don't know what's wrong.

---

### Post by Dave_is_sexy on 2005-06-21
I got the log by re-installing. It wont let me copy the text of course.

The gist is:

"you probably typed your root sql account password wrong" 

now, i typed my root password right... does it mean that?
```

dave@D5:~$ mythtv
2005-06-21 20:47:50.896 Unable to read configuration file mysql.txt
2005-06-21 20:47:50.897 Writing settings file /home/dave/.mythtv/mysql.txt
2005-06-21 20:47:50.904 Switching to square mode ()
2005-06-21 20:47:50.918 Unable to connect to database!
2005-06-21 20:47:50.963 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user: 'mythtv@localhost' (Using password: YES)

couldn't open db
2005-06-21 20:47:50.964 Switching to square mode (blue)
Segmentation fault
dave@D5:~$
```

---

### Post by hw-tph on 2005-06-21
Your root password has nothing to do with the mysql password. If Ubuntu mysql-server setup is like most others (root doesn't have a password - generally a bad idea) you can set a mysql password for root using **sudo myslqadmin -u root password (new-password)**, where (new-password) is the the new password you want.

You can then enter the mysql console by typing **mysql -u root -p mysql** and then create a new user for daily use. I prefer keeping root out of mysql as much as possible and create different users for specific tasks, in case something goes wrong.

Håkan

---

### Post by Dave_is_sexy on 2005-06-21
```
Password:
sudo: myslqadmin: command not found
dave@D5:~$
```

Darn. I dont think i have my SQL. Wouldn't Synaptic have noticed that tho?

---

### Post by hw-tph on 2005-06-21
Sorry, bad typo on my behalf: Of course it should be "mysqladmin", not anything else.

```
Access denied for user: 'mythtv@localhost' (Using password: YES)
```
That's most likely MySQL talking right there, so I'd wager you have it installed.

Håkan

---

### Post by Dave_is_sexy on 2005-06-21
OK that went with no errors. Re-installed mythtv (just right click > reinstall) but we get:

```
dave@D5:~$ mythtv
2005-06-21 22:24:33.759 Switching to square mode ()
2005-06-21 22:24:33.766 Unable to connect to database!
2005-06-21 22:24:33.766 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user: 'mythtv@localhost' (Using password: YES)

couldn't open db
2005-06-21 22:24:33.767 Switching to square mode (blue)
Segmentation fault
dave@D5:~$
```

meh. Also it didn't ask for a password on install this time.

---

