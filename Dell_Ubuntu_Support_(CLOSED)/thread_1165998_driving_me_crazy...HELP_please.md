---
title: "driving me crazy...HELP please"
date: 2009-05-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mhuxtable on 2009-05-21
So there are 2 issues really.

1. I just did the updates the computer asked me to do...everything is fine EXCEPT now my internet browsers forward and back buttons DONT WORK.  So say if I go to my email and then myspace and then google, the back or forward buttons never become blue and usable, the are always grey and not clickable. WHY? help with a fix please?

and 2.  The partition thing.  I have the DELL mini that come with Ubuntu.  Somehow, i missed the whole partition issue, so my computer says I have used up all the hard drive space even though all I have done is updates and have about 30 pictures.  So how do I fix the screw up that led to only half the HD being available?

Thanks in advance for help

---

### Post by apjone on 2009-05-21
Have you closed firefox or rebooted since the updates ?

---

### Post by mhuxtable on 2009-05-21
Yes I have. In fact, when I went to reboot the second time, my computer took a REALLY long time to shut down...something to do with the disk space being full??

It also takes much longer than usual for the desktop icons & toolbar to appear.

---

### Post by apjone on 2009-05-21
You may be able to get some space back by removing cached debian files
```
sudo rm /var/cache/apt/archives/*deb
```
**[COLOR="Red"]Be careful as This makes you the super user and ubuntu wont ask if you are sure.[/COLOR]**

---

### Post by mhuxtable on 2009-05-21
Thanks I will try that. 

Anyone got any info as to why Firefox is all screwed up now?

And wasn't there a fix for the HD issue? I feel like I remember reading that the minis came partitioned incorrectly and only half the HD was usuable...is there a fix for that?

---

### Post by ugm6hr on 2009-05-21
> **mhuxtable said:**
> Anyone got any info as to why Firefox is all screwed up now?

And wasn't there a fix for the HD issue? I feel like I remember reading that the minis came partitioned incorrectly and only half the HD was usuable...is there a fix for that?

Perhaps fixing the HD space issue will resolve the FF problem.  It may be you have no HD space for the FF cache.  If not, deleting and starting with a new FF profile might sort it.

Check your HD space with:
```
df -h
sudo fdisk -l
```

If you have only half the HD partitioned, you will need to reinstall.  A good time to give 9.04 Netbook Remix a try!

---

### Post by mhuxtable on 2009-05-21
I put in that command in the terminal and this is the message I got.

rm: cannot remove `/var/cache/apt/archives/*deb': No such file or directory


so what now? anyone? pleeeease

---

