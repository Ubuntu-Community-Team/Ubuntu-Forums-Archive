---
title: "No Sound HP DV9000"
date: 2009-06-25
forum: General Help
---

### Post by Loomy on 2009-06-25
I tried Ubuntu a while back but eventually gave up because of hardware issues.  However, I really want to make it work this time.

Everything is working perfectly except that I have no sound.  The weird thing is it used to work the first time I installed but I messed something up and it stopped working.  I tried to reinstall and still no sound :(.

Any help is much appreciated.  I am using the newest version of Ubuntu.  I am sure I have not given enough information so anything you need to know to help me out just ask.

Thanks in advance for your help!

---

### Post by Loomy on 2009-06-25
bump

---

### Post by davidryderuk on 2009-06-25
Hi,
First double check none of your sound settings in the Volume control applet are muted. 

If this doesn't work there is quite a good guide on getting your laptop to work with Linux below (although i wasn't sure if you had the HP DV9000t or HP DV9000z).

[http://www.linlap.com/wiki/hp+pavilion+dv9000t](http://www.linlap.com/wiki/hp+pavilion+dv9000t)

All you should have to do is the following.

1. Edit /etc/modprobe.d/alsa-base.conf file
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```

2. Scroll down to the bottom of the file and add the following
```
options snd-hda-intel model=hp position_fix=1 
```

3. Restart the computer.

A guide to trouble shooting audio problems (including adding options to alsa-base.conf) is shown below.

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

