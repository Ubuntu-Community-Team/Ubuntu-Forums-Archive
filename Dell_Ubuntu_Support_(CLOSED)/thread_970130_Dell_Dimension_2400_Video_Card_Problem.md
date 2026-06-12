---
title: "Dell Dimension 2400 Video Card Problem"
date: 2008-11-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Marikawn on 2008-11-03
Greetings,

I am new to the world of Linux but learn quickly. I have just installed the 8.10 Version of Linux on my PC. At first it said that video could not be displayed so I installed it on (f4 option) 'safe mode'. It installed great, but now I can't seem to get the screens resolution above 640 X 480. I have tried modifying /etc/X11/xorg.conf many times and I don't seem to know how to fix it. The generic driver it's stuck on is called 'Vesa'. My graphics card is "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)". Please help me apply the correct video settings.

Thanks,
Jimmy

---

### Post by MarkEveritt on 2008-11-27
I'm having the same problem with this model... Anyone got any ideas on this? I'm not so bothered really because it's an old lab machine but it'd still be nice to give it a new lease on life! :)

---

### Post by MarkEveritt on 2008-11-27
Never mind, I did all the updates and that appears to have fixed it.

---

### Post by poke4christ on 2008-11-27
My mother's system is also a Dimension 2400 and it has been running very slow for a long time.  I just haven't been around to get to it.  I'm wondering if it is a video card problem.  According to the xorg.conf the driver it's using is "intel"

[http://ubuntuforums.org/showthread.php?t=995325](http://ubuntuforums.org/showthread.php?t=995325)

---

### Post by werLd on 2009-01-10
Can you please paste your entire xorg.conf? 

cat /etc/X11/xorg.conf

---

### Post by MIKE SILVA on 2009-09-07
Hi,

I have a similar equipment. I have install the version 9.04.

After make all the installation and updates it works with higher resolution without any problem.

Don't use "vesa". 

But if you try to use without monitor, maybe experience more difficults.

I'm searching a solution to resolve a similar situation.

Maybe you need to eliminate the driver "vesa" from xorg.conf and try to reboot and see what it happens.



Hope it helps

---

