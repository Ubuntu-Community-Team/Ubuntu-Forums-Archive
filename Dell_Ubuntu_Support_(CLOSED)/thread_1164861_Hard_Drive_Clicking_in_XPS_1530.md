---
title: "*Hard Drive Clicking in XPS 1530*"
date: 2009-05-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jheylin on 2009-05-20
I installed Ubuntu 9.04 on my computer recently and am incredibly happy with it (I upgraded from 8.10 which was an upgrade from 8.04).  But an issue that seems to keep cropping up is that the hard drive clicks when the laptop is on battery mode.

I've researched this like nuts and have tried the ugly fixes, the good fixes, messing with the hdparm, etc.  What's interesting is that it used to happen on the other versions until I did a fix but it happened all the time.  Now it just happens when my laptop is on battery power.

I figure the hard drive it told to behave a different way when it's on battery power, probably to save energy, which explains why I only hear it then, but I don't know how to stop it.  Every time I hear a click (about every 5-15 seconds) an image goes through my head of the hard drive getting a nice big scratch on it.

Can someone help me?

---

### Post by Yanisae on 2009-05-20
I have a Dell Inspiron 1525n (n for Ubuntu preinstalled) and it works the same. The HD keeps "clicking" every x seconds. That seems like something perfectly normal.

Afterwards, I installed (an original, genuine and all that crap) Win XP Pro (because I've been forced to) copy at another partition. Guess what ? It's even worse. Nothing new.

It looks like the O.S. keeps working in the background, and "calling" the H.D. That means -in Ubuntu- that you probably have a way to "smooth" it. Maybe buffering more and writing less to H.D. (I guess you've already tried that). **As long as it's OS related that should be fine**. Winbugs would do it 10x more, and PC's don't keep breaking because of that.

There's a straight way to tell: can you keep watching videos, playing MPs and the like **through the H.D.** (files saved on disk) ? If everything goes smooth while HD is clicking, H.D. is working fine. Don't try to play 5 different MPEG movies at the same time, that won't count ! :)

I know when a HD is half dead. It will surely **hang** while trying to access to it. Or even worse, you'll keep losing data.

I bet that clicking means the HD heads are moving from one place to another.

Install gnome-system-monitor and add its applet to your gnome bar, set it to display your HD reads/writes and watch. Half of the time, that click means a high writing operation bar showing clear on your display.

Important: if you feel like HD is having the plates scratched, you ARE losing data. Period. What's more, your HD would be useless in no time, debris getting everywhere... Try to fill most of it. If you can still read things here and there, it's fine.

Hope this helps !

---

### Post by Gausian on 2009-05-21
its actually a good thing to hear that click on battery power.  its a design feature of your hdd to protect it from bumps and to save power.

do a search for head parking for more info.

basically your hdd is parking so that it doesnt get damaged if your computer gets bumped.  it happens on battery power since that is when you probably are moving your computer around.

this happens in vista and xp.  its a feature built into your hdd.

---

