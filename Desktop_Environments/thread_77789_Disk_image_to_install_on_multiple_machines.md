---
title: "Disk image to install on multiple machines?"
date: 2005-10-17
forum: Desktop Environments
---

### Post by dgermann on 2005-10-17
Hi--

I need to have the same set up on several machines (and this would make it easier to blow the disk away and reinstall if I do something improvident!).

Is there some way I can make an image of my whole disk and just drop that on the dupicate machines?

Thanks!

---

### Post by scorpio2002 on 2005-10-17
try partimage :-)

---

### Post by dgermann on 2005-10-17
scorpio2002--

That looks like exactly what I need. Thanks, scorpio2002!

Say, what's that linuz user number in your sig?

That is a different translation of Goethe from what I have seen before. Did you translate it yourself?

---

### Post by HermanAB on 2005-10-17
Or simply use dd.

Disk drives are so cheap nowadays, I just copy the whole disk and keep it in a desk drawer.

# dd if=/dev/hda of=/dev/hdb

No time wasting software to install - plug the second drive in, change the jumper to make it a slave, boot with Knoppix or Ubuntu Live and there you go.

Cheers,

Herman
[http://www.aerospacesoftware.com/linuxhowtos.html](http://www.aerospacesoftware.com/linuxhowtos.html)

---

### Post by dgermann on 2005-10-18
Herman--

Thanks. Sounds like a good alternative.

> # dd if=/dev/hda of=/dev/hdb

No time wasting software to install - plug the second drive in, change the jumper to make it a slave, boot with Knoppix or Ubuntu Live and there you go.


Herman, two things come to mind: 1. if to me looks like it is calling for a file, and you have specified a device. Looks like some old pro's trick. What is it doing?

2. Let me feed that second part back to you to see if I understand: Install 2nd drive in 1st machine. Do the dd stuff. Remove second drive from 1st machine, put it in 2nd machine. Shouldn't I just be able to boot it up from there? 

Guess I am missing where the live CD stuff comes in. Is that what you need to be able to do the dd stuff? In other words, if you are standing on the rug in hda, you cannot sweep it clean and onto hdb--is that it? How am I doin'? :D

---

### Post by scorpio2002 on 2005-10-27
> That is a different translation of Goethe from what I have seen before. Did you translate it yourself?

Actually, it's from Murray if I'm not mistaken. Anyway yes, I read it on an Italian book and I felt in love with it! So it's translated from an Italian translation - lol :-)

> That looks like exactly what I need. Thanks, scorpio2002!
Well, you know, I do like partimage! Once I used to use Norton Ghost, then I found partimage and I've been using it ever since.

---

