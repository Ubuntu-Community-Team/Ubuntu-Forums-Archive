---
title: "Inspiron 1501 wireless help?"
date: 2007-12-19
forum: Dell  Ubuntu Support
---

### Post by roseysdaddy on 2007-12-19
ok, ive been a linux user for about an hour now.  here is the situation...

Ubuntu 7.10  installed....wifi is lit, it sees local networks, but it wont connect, can only get on the net with the cat 5 cable. r 

also, how to i updaye the 43broadcom restricted driver?  the ati radeon driver update immediately but then it gives me an error with that one.  thanks in advance for all your help!

roseysdaddy

---

### Post by saru411 on 2007-12-19
[http://ubuntuforums.org/showthread.php?t=405990&highlight=1390](http://ubuntuforums.org/showthread.php?t=405990&highlight=1390)

the search button is your friend.

---

### Post by jan quark on 2007-12-19
I have also an Inspirion 1501. Had to do following two steps. 

Get this two files:
1.  bcm43xx-fwcutter_006-1_i386.deb
2.  bcmwl5.sys

try to google them, you should find them if not i must use my memory.

Then install the bcm43xx-cutter by simply double clicking on the deb package.
During the installation i t will ask you to fetch firmware. Dont do this. Just install it.

Then go to the restricted drivers. System> Administration.> Restricted Drivers

Click on Enable drivers for firmware for broadcom. A screen should appear and you navigate to the second file to bcmwl5.sys.

Save the two file on the desktop its easier to navigate. Once the driver is installed you may delete the file from the desktop.

Hope this will help. Worked for me. And its the shortest way out there so far... :)

---

