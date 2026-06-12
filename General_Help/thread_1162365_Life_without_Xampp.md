---
title: "Life without Xampp"
date: 2009-05-17
forum: General Help
---

### Post by lazman on 2009-05-17
I think maybe the xampp package is what is not allowing netbeans 6.5 to connect to mysql.

Is there a current walk-through for installing everything that xampp installs without installing xampp? I have been searching for a couple of hours now but can't find anything. Do I have to install the server version of Ubuntu?

---

### Post by lovinglinux on 2009-05-17
[https://help.ubuntu.com/community/ApacheMySQLPHP?action=show&redirect=LAMP](https://help.ubuntu.com/community/ApacheMySQLPHP?action=show&redirect=LAMP)

---

### Post by lazman on 2009-05-17
Thank you!

---

### Post by lazman on 2009-05-18
I FINALLY got this working after hours and hours of frustration and loss of a large bald spot on the top of my head! I now have apache2 mysql5 and with php running. And netbeans connected right up to the database when I opened it after installing with add remove. 

**[COLOR="Red"]A warning to future linux noobs.... Never! NEVER NEVER NEVER NEVER NEVER......................NEVER install xampp on Ubuntu!!!!!!!![/COLOR]**

To get rid of this was quite a task for a linux noob. It took hours of searching and head banging, and on top of that when I did remove mysql from xampp and (sqlite so I could run mysql) all of my desktop configureations were lost, it looks like I just installed Ubuntu aggain :/ It seems there are alot of programs that use some type of database mostly sqlite, including gnome-rdp, which took 30min of searching to figure out I needed to rename the database file .gnome-rdp.db in my home directory. Then to remember all the settings I had on it I had to open it in a hex editor and fine the settings... real pain.

Trust me, take the time and follow the directions on installing the lamp stuff for Ubuntu the right way. 

**DO NOT CONFUSE** Xampp with LAMP. It is an easy install if you do it from the start, and should only take a few minutes to follow the directions on this page. [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

lovinglinux, 
OMG Thank you soooo much for posting that! I did not realize this was different from Xampp because the user names for Xampp are lampp.  It is close. I had almost given up and deleted Ubuntu from my machine. I really like it tho so it's worth the effort for me to learn what I'm doing and it's people like you that help folks like me out that keep us going. :)

A huge HELL YEA!! For all the people that take the time to help on here!

---

### Post by cb951303 on 2009-05-18
a simple ```
 sudo tasksel install lamp-server
```
would do the job.

---

### Post by lovinglinux on 2009-05-19
> **lazman said:**
> **[COLOR="Red"]A warning to future linux noobs.... Never! NEVER NEVER NEVER NEVER NEVER......................NEVER install xampp on Ubuntu!!!!!!!![/COLOR]**

To get rid of this was quite a task for a linux noob. It took hours of searching and head banging, and on top of that when I did remove mysql from xampp and (sqlite so I could run mysql) all of my desktop configureations were lost, it looks like I just installed Ubuntu aggain :/ It seems there are alot of programs that use some type of database mostly sqlite, including gnome-rdp, which took 30min of searching to figure out I needed to rename the database file .gnome-rdp.db in my home directory. Then to remember all the settings I had on it I had to open it in a hex editor and fine the settings... real pain.

I never had problems with Xammp, even after removing it. I think the problem is that you also removed sqlite, which is used by several applications like Firefox. Sqlite is a standalone database, which does not require a server to be used. I don't know why you had to remove it. Anyway, as far as I know, Xammp works like a portable server, it is installed on the opt directory and it shouldn't interfere with your other installations. BUt I don't know what happens if you install an application that requires MySQL while Xammp is running.

> **lazman said:**
> 
lovinglinux, 
OMG Thank you soooo much for posting that! I did not realize this was different from Xampp because the user names for Xampp are lampp.  It is close. I had almost given up and deleted Ubuntu from my machine. I really like it tho so it's worth the effort for me to learn what I'm doing and it's people like you that help folks like me out that keep us going. :)

You are welcome. I'm glad that you fixed the problems.

---

