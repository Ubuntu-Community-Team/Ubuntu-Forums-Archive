---
title: "how to view remaining space on disk ?"
date: 2005-11-17
forum: Desktop Environments
---

### Post by jmejedi on 2005-11-17
How do you view the remaining disk space in breezy ??? (in windows, you generally right-click, choose properties, and there it shows on much is used and how much is free)

Thank you for your time,

JME

---

### Post by ubuntu_demon on 2005-11-17
I moved this thread. Don't post questions in the customization section!

There are a couple of ways. The ones I prefer :

this shows the mounted partitions and their free space in human readable numbers in the terminal :

$ df -h

This shows in a graphical way where al the space on your harddisk is going to :

$ xdiskusage 

to install the xdiskusage :
$ sudo apt-get install xdiskusage

---

### Post by Roman27 on 2005-11-17
You can also go to *Applications* -> *System Tools* -> and then click on *System Monitor*.  Once it opens, click on the *Devices* tab.  You should have a graph there.

---

### Post by dragonfoundry on 2005-11-18
Wish i opened System Monitor gives me all the info i need - i had installed and used KDiskFree

---

### Post by philipscard on 2005-11-18
I have kubuntu on a 3GB partition (all I could spare), but having updated to breezy the distro was taking up 2.7 of that, with almost no personally installed apps or documents. Is there any obvious way of regaining some space (I've already taken out openoffice!, all media apps except kaffeine; the only things I use beyond typical terminal and maintenance commands are thunderbird, a java environment, konqueror and kate...). 
I have found over 600MB occupied by .deb files in /var/cache/apt/archives/ - do these need to stay?
Also, the size of the partition has apparently reduced to 2.8GB since the update (acertained by getting properties of an arbitrary folder in konqueror), all the root level directories add up to ~2GB total (995MB in /usr) yet there is only 500MB spare, and the file size view in konqueror (with all the squares and colours) totals 2.8GB by including the contents of my Mac partition (800MB out of 3GB used) which has a root level entry /mac.
All very confusing! So what's really going on?
Thanks for any enlightenment.

---

### Post by ubuntu_demon on 2005-11-18
[QUOTE=philipscard]I have kubuntu on a 3GB partition (all I could spare), but having updated to breezy the distro was taking up 2.7 of that, with almost no personally installed apps or documents. Is there any obvious way of regaining some space (I've already taken out openoffice!, all media apps except kaffeine; the only things I use beyond typical terminal and maintenance commands are thunderbird, a java environment, konqueror and kate...). 
I have found over 600MB occupied by .deb files in /var/cache/apt/archives/ - do these need to stay?
Also, the size of the partition has apparently reduced to 2.8GB since the update (acertained by getting properties of an arbitrary folder in konqueror), all the root level directories add up to ~2GB total (995MB in /usr) yet there is only 500MB spare, and the file size view in konqueror (with all the squares and colours) totals 2.8GB by including the contents of my Mac partition (800MB out of 3GB used) which has a root level entry /mac.
All very confusing! So what's really going on?
Thanks for any enlightenment.[/QUOTE]

I merged these two threads.

Please don't post questions in the customization section!

---

### Post by ubuntu_demon on 2005-11-18
you guys can also look here :

[http://www.ubuntuforums.org/showthread.php?t=91242](http://www.ubuntuforums.org/showthread.php?t=91242)

---

### Post by philipscard on 2005-11-20
thanks, useful info on that thread, and I've noted a couple of disc usage issues there

---

