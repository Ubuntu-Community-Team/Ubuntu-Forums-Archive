---
title: "GDM group 'gdm' does not exist. Please correct GDM configuration and restart GDM."
date: 2011-09-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mokshus on 2011-09-23
So I was on my dell inspiron 910 mini computer, running Hardy Heron at work. I left for a minute, came back, and a coworker had pressed a button or something, and the panel normally at the top was at the right. To fix it, I had to remove some of the objects to right click it since they were in the way. While trying to put them back on after moving it back, the computer froze and I restarted it. When restarting, I get the following message:

The GDM group 'gdm' does not exist. Please correct GDM configuration and restart GDM. 

After a few minutes, a login window appears, and I try to log in, but it doesnt seem to work. It just keeps telling me my password is incorrect. Any help would be greatly appreciated. Thanks for your time everyone.

---

### Post by mokshus on 2011-09-23
The login prompt reads like this:

Ubuntu 8.04.1 jeremy tty1
jeremy login:

(if I press enter the clause repeats)

if I type anything, it says :

enter password:

and I do, and nothing happens, so I press enter, and it says wrong password

---

### Post by garvinrick4 on 2011-09-23
ctrl/alt/F1
You are typing in your login name and then password.
These are choices with gdm

To reinstall.
```
sudo apt-get install --reinstall gdm
```To restart```
sudo /etc/init.d/gdm restart
``` To reconfigure
```
sudo dpkg-reconfigure gdm
``` Take your choice of which ones to use do not no quite where you are at.

---

### Post by mokshus on 2011-09-23
I attached some images of the screens im getting. I tried the commands, but got no response at all. And now, I am getting a new message:

chown: invalid group: 'syslog:adm'
chown: invalid group: 'syslog:adm'
chown: invalid group: 'syslog:adm'
chown: invalid group: 'syslog:adm'
chown: invalid group: 'klog:klog'
chown: invalid group: 'klog:klog'
chgrp: invalid groupL 'messagebus'
Timeout reached while waiting for return value
Could not recieve return value from daemon process.
         * Can't start Hardware abstraction later - please ensure dbus is running

---

### Post by garvinrick4 on 2011-09-23
If you got into a tty and you got no results from any of the gdm commands then something is real amiss.
You cannot get a new gdm package because your version of Ubuntu is not supported anymore.
When you did the install --reinstall something had to happen.
either error messages or maybe you had a package gdm cached I do not know.
It would be like you have no gdm at all.
If you have aptitude installed in a tty can
aptitude show gdm
will say if installed.

Not knowing what your co-worker did and not a supported version to get new packages it is a rough one.

---

### Post by mokshus on 2011-09-26
yeah...

In the terminal I am getting zero response from sudo commands, not even error messages. I think I'll just wipe it and reinstall a newer version. Bummer, though. Thanks for all your help, I appreciate it even though we couldn't figure it out.

---

