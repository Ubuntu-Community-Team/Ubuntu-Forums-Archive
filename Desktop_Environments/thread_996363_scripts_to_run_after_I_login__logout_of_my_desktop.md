---
title: "scripts to run after I login / logout of my desktop"
date: 2008-11-28
forum: Desktop Environments
---

### Post by boondocks on 2008-11-28
With the standard Ubuntu desktop, I want to:

[INDENT]1.  Run my "/home/me/special_login" shell script after I log into my desktop.

2.  Run my "/home/me/special_logout" shell script after I log out of my desktop.
[/INDENT]
Which files should I add these scripts to?

---

### Post by ibutho on 2008-11-28
For logging in, go to System -> Preferences -> Sessions and add the commands you want to run at start up. I am not so sure about commands at logout.

---

### Post by Coreigh on 2008-11-28
I don't know if this is good practice but I have run login/out scripts using the runlevel system. There are a series of directories in etc named rc.0, rc.1, rc.2, rc.3, rc.4, rc.5, and rc.6 they are used to run the init scripts from /etc/init.d for starting and stopping services depending on runlevel.

---

### Post by boondocks on 2008-11-29
> **ibutho said:**
> For logging in, go to System -> Preferences -> Sessions and add the commands you want to run at start up. ... 

Yeah, this will help.
Thanks.

---

### Post by Whoopie on 2008-11-29
You could also use pam_script for that ([http://linux.bononline.nl/linux/pamscript/01/build.html](http://linux.bononline.nl/linux/pamscript/01/build.html)).

---

