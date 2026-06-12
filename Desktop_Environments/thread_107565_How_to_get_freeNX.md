---
title: "How to get freeNX"
date: 2005-12-23
forum: Desktop Environments
---

### Post by mbailey on 2005-12-23
Any ideas where I can get freeNX? the wiki on the subject directs to a web site which is down & the instructions for setting up keys to use the mirrors are apparently on that site too.

Thanks
Martin

---

### Post by rikai on 2005-12-23
add these lines to your /etc/apt/sources.list

```
# FreeNX stuff
#
deb http://seveas.ubuntulinux.nl/ breezy-seveas freenx
deb-src http://seveas.ubuntulinux.nl/ breezy-seveas freenx
```
and then:
```
sudo apt-get update
```
and you should be able to grab it from synaptic.

---

### Post by tuxy on 2005-12-24
Let me know if you have downloaded without any fuss 'coz I had a problem whenever I tried to apt-get update the cursor simply sits blank. I heard from the forums that 'seveas' site is closed. 

I am badly in need of the FreeNx server. Quick help will be greatley regarded.
Cheers.

---

### Post by mbailey on 2005-12-25
The site closure is the issue - some of the mirrors are still up, but give key problems with apt-update

---

### Post by tuxy on 2005-12-25
Some how I managed to install it. You can read this post for more info:
[http://ubuntuforums.org/showthread.php?t=108018](http://ubuntuforums.org/showthread.php?t=108018)

---

