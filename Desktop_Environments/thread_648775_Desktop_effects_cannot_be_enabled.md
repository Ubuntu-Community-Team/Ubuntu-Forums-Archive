---
title: "Desktop effects cannot be enabled"
date: 2007-12-24
forum: Desktop Environments
---

### Post by Mortal Light on 2007-12-24
I am currently running gutsy gibbon on a sony vaio (1.8ghz, 2 gb ram, integrated intel gma x3100) and whenever I try to start up compiz, I get a message saying "desktop effects cannot be enabled." I was wondering if this may have something to do with my graphics chip. I am very new to linux and I'm looking for a little help.

---

### Post by Sef on 2007-12-24
Check System > Administration > Restricted Drivers Management.  You will need restricted drivers in order to use Compiz-Fusion.   If that does not work, then you would need to buy a video card which would enable you to use Compiz-Fusion.

---

### Post by shifty2 on 2007-12-24
I had that issue a while ago, I resolved it after reading this thread: [http://ubuntuforums.org/showthread.php?t=436110](http://ubuntuforums.org/showthread.php?t=436110)

The solution that worked for me was installing xserver-xgl:
```
sudo apt-get install xserver-xgl
```
reboot and hopefully it should work

---

### Post by Mortal Light on 2007-12-26
Thanks, it worked like a charm!

---

