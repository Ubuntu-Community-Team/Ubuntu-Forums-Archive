---
title: "Auto start with init.d"
date: 2005-06-09
forum: Desktop Environments
---

### Post by gallagher_niall on 2005-06-09
Hi All,

I am new to Ubuntu and so far it has been a real pleasure to use and setup. However, I have previously been using Redhat and when I had a new service, such as a new web server, I would create a startup script and copy it to /etc/init.d and symlink to it from /etc/rc5.d and it would enable me to start that service when the system rebooted.

So far I have not been able to discover how this can be done for Ubuntu/Debian, does anyone have any suggestions? I am trying to start Tomcat and James every time the system restarts. Any help would be appreciated!

Regards
Niall

---

### Post by Alexander Kirillov on 2005-06-09
[QUOTE=gallagher_niall]Hi All,

I am new to Ubuntu and so far it has been a real pleasure to use and setup. However, I have previously been using Redhat and when I had a new service, such as a new web server, I would create a startup script and copy it to /etc/init.d and symlink to it from /etc/rc5.d and it would enable me to start that service when the system rebooted.

So far I have not been able to discover how this can be done for Ubuntu/Debian, does anyone have any suggestions? I am trying to start Tomcat and James every time the system restarts. Any help would be appreciated!

Regards
Niall[/QUOTE]
 Ubuntu uses initlevel 2 by default - otherwise, you can do all the same things. But there is a script that automatically manages creation of symlinks: update-rc.  For more info, read  
[http://www.debian.org/doc/debian-policy/ch-opersys.html#s-sysvinit](http://www.debian.org/doc/debian-policy/ch-opersys.html#s-sysvinit)

---

### Post by dabear on 2005-06-09
Please read [This post](http://www.ubuntuforums.org/announcement.php?f=58)  before asking questions

---

### Post by felipe on 2005-06-09
same thing for ubuntu, except the default runlevel in debian/ubuntu is rc2, so you have to link your /etc/init.d/scripts to /etc/rc2.d/

anyway take a moment to learn update-rc.d, it automates the task

have fun

---

### Post by theQmaster on 2005-07-31
[QUOTE=gallagher_niall]Hi All,

I am new to Ubuntu and so far it has been a real pleasure to use and setup. However, I have previously been using Redhat and when I had a new service, such as a new web server, I would create a startup script and copy it to /etc/init.d and symlink to it from /etc/rc5.d and it would enable me to start that service when the system rebooted.

So far I have not been able to discover how this can be done for Ubuntu/Debian, does anyone have any suggestions? I am trying to start Tomcat and James every time the system restarts. Any help would be appreciated!

Regards
Niall[/QUOTE]
 There are 2 ways one is using init.d and I don't think that is good - security wise and second there is a package from jakarta project(common-daemon) that would allow a tomcat to run as a low priviledge user - this is prefered but so far I was't succesful. ( exits with return code 1)

Anyone can share ?

---

### Post by theQmaster on 2005-08-02
Check you classpath. That will fix it. I spend 2 days to get it working but still there is a problem in tomcat 5.5.9 - the bootstrap that runs as root is trying to access tomcat-users.xml and that belongs to tomcat:tomcat and fails.

Closely watch the logs folder and read them out...

---

