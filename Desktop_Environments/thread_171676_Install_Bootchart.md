---
title: "Install Bootchart"
date: 2006-05-07
forum: Desktop Environments
---

### Post by opticyclic on 2006-05-07
What with Dapper being released very soon I wanted to compare my Breezy boot times with the Dapper boot times once I upgraded.

However, I am having problems installing bootchart.

I downloaded the deb file from here [http://packages.debian.org/testing/admin/bootchart](http://packages.debian.org/testing/admin/bootchart)

Then installed it with ```
sudo dpkg -i bootchart_0.9-1_all.deb
```
However, there is no /var/log/bootchart/ directory on my system. :confused: 

Am I missing something?

---

### Post by ranf on 2006-05-07
You're definitely missing something.
This looks good:
[http://cvs.sourceforge.net/viewcvs.py/bootchart/bootchart/INSTALL?view=markup](http://cvs.sourceforge.net/viewcvs.py/bootchart/bootchart/INSTALL?view=markup)

---

### Post by opticyclic on 2006-05-07
This page gave a link to 0.8.3 which seemed to work (rather than 0.9.1)
[https://wiki.ubuntu.com/BootCharting](https://wiki.ubuntu.com/BootCharting)

However, I did have to modify my grub list as in your link.

I still don't get a /var/log/bootchart/ directory with png files in though.

I am having to rely on the web form on this page to convert the bootchart log tarball (/var/log/bootchart.tgz)
[http://www.bootchart.org/download.html](http://www.bootchart.org/download.html)

---

### Post by ranf on 2006-05-07
At the time I was using bootchart I always did upload my .tgz and let them render the graphics. I don't want to install Java on my box.

---

### Post by jazzgossen on 2006-10-16
Digging up an old thread here...

I'm also having trouble installing bootchart. I installed it via aptitude, but nothing new happens when I boot. I have a /var/log/bootchart directory, but it's empty. I have no other bootchart log files in /var/log. 

I manually appended init=/sbin/bootchartd to my kernel line in menu.lst, as per the instructions on bootchart's web page, but then I get a busybox prompt when I boot, telling me that it can't access the tty. 

Any ideas?

---

### Post by opticyclic on 2006-10-16
You probably should have created your own thread...
Did you try installing the 0.83 deb?

---

### Post by jazzgossen on 2006-10-16
Now I've tried installing the 0.83 deb, and that works much better, thanks.

---

