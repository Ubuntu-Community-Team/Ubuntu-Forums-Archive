---
title: "Apache2 GUI Frontend?"
date: 2006-09-14
forum: Desktop Environments
---

### Post by fractalvibes on 2006-09-14
I searched in the packages in synpatic and didn't see anything, so I'll pose a question.  Is there a GUI frontend client for Apache2
(something similar to the IIS console for m$ win server)?  Surely there must be.  I just want to stop and restart Apache2 to see if a php.ini setting will take effect.

thanks,

fv

---

### Post by mexlinux on 2006-09-15
You don't really need a gui for stop start restart apache
Just type
sudo /etc/init.d/apache2 stop (or restart or whatever acction you want)

You can even make shortcuts so you can simply click....

---

### Post by fractalvibes on 2006-09-15
Thanks!  I found that I could do the start/stop in Kubuntu via KDE's
K Menu - System Settings / System Services icon - but all you can do is a start and stop of services.  Seems that it would be handy to have something akin to the IIS console tool.  But it could be that Apache2 is such a different animal from IIS?  i.e. don't have to deal with application pools nor isapi nor com objects?  

fv

---

### Post by marianom on 2006-09-15
There's several things you have to consider but I found them a lot easier to configure with the Apache conf file than in IIS GUI. A good starting point is to read from top to bottom the httpd.conf file where you'll be presented with some conf parameters and then read docs to see how you can extend Apache (specially using modules: [http://httpd.apache.org/docs/2.2/mod/](http://httpd.apache.org/docs/2.2/mod/)). It seems you already know this since you are working with php and for that a minimal interaction with the conf file is required.

Related to the GUI thing: as far as I know there's no official project for an Apache GUI built @ The Apache Software Foundation. There's lot of shareware, freeware and paid developments you can find searching in the web that promise you a GUI to administer the Apache. Check them if you have some time to spare but I suggest invest that time in learning how to use the conf file.

---

