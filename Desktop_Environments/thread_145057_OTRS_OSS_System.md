---
title: "OTRS OSS System"
date: 2006-03-15
forum: Desktop Environments
---

### Post by WoodyMahan on 2006-03-15
I have installed the OTRS system and I am trying to follow the instructions provided by them.  But I have run into a sloght snag.  When I load the default webpage for OTRS I get a message stating:

Kernel/Config.pm isn't writable!
If you want to use the Web Installer set the Kernel/Config.pm writable for the webserver user.

I searched for Config.pm to see if I can find one in a Kernel Directory but did not find one.  Is anybody out there familiar with using this OSS?

---

### Post by WoodyMahan on 2006-03-15
I am also seeing this when I try to restart my Apache server.

woody@ubuntu:~$ /etc/init.d/apache2 restart
 * Forcing reload of web server  (Apache2)... httpd (pid 7213?) not running
                                                                         [fail]
woody@ubuntu:~$

---

