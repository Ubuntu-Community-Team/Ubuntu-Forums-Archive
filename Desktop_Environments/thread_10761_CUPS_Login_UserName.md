---
title: "CUPS Login UserName"
date: 2005-01-11
forum: Desktop Environments
---

### Post by Jæd on 2005-01-11
Hi,

What is the CUPS login name when using the web interface to manager CUPS? Or how do I assign a username to CUPS so that I log in...?

---

### Post by hardcandy on 2005-01-11
First "sudo passwd root" in a console, follow the dialogue and make a root password. Then "su" to change to root (a # will be shown in the console)then " adduser cupsys shadow" then reboot or "sudo /etc/init.d/cupsys restart"  and  then use "root" as the user name and root's password .

---

### Post by Jæd on 2005-01-11
Thanks! This has done the trick!  =D>

---

### Post by TACtech on 2006-08-09
:mrgreen: Yey it worked nice nice !

---

### Post by cosine7 on 2006-08-11
Thanks worked great

---

### Post by albaine on 2006-08-15
Still a good fix in August 2006.  

[cupsys password]

---

### Post by jis on 2006-09-06
hardcandy, at least in Xubuntu there is no need to create a separate root user, nor to use the su command. If you do not, type "sudo adduser cupsys shadow" instead of "adduser cupsys shadow". The login user name is the "first" user and you could use its password. See also [https://help.ubuntu.com/xubuntu/desktopguide/C/printer-configuration.html](https://help.ubuntu.com/xubuntu/desktopguide/C/printer-configuration.html)

---

