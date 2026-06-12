---
title: "Video Speed too fast"
date: 2005-12-02
forum: Desktop Environments
---

### Post by dawhippersnapper on 2005-12-02
When opening a video in Xine, totem, or inside browser, even a flash animation, it plays too fast.  It is a compaq laptop v2405 and has an amd sempron processor with 256mb of ram and ati x200 shared video.  

Any suggestions?

---

### Post by dawhippersnapper on 2005-12-02
I should also note I have the ATI proprietary driver installed.  This laptop doesnt work with the opensource driver unless you use -noaccel option, but still crashes often with that option.

---

### Post by dawhippersnapper on 2005-12-03
It has become much more strange and now the whole system seems to be running too fast, including the system time.  Any ideas anyone?

---

### Post by meborc on 2005-12-03
wow... i always have had problems with comps that are too slow... :D i've never seen such a miracle that a comp is running too fast... it seems that the problem is somewhere in the x... when did this start? did you install/remove smth or did it just start doing it (highly unlikely)?

---

### Post by dawhippersnapper on 2005-12-03
Actually I just bought the laptop a couple days ago, split the drive installed ubuntu for dual boot(it had a broadcom wireless chip, so I knew ndiswrapper would be buggy).  I set it up and X wouldnt work, the native screen resolution is 1280x768.  I found out the hard way that the opensource driver for this laptop was buggy, and used the -noaccel option to get X to work, it kept crashing so I installed the latest ATI driver from ATI's website.  Went on to install all of the video codecs, dvd support, firefox plugins, etc. And then downloaded a couple videos to test it out,  they were buggy, then today I realized the time was wayyyy off =P.  Reset it looked back down and it was going almost double speed =P.

I found this thread, but I think it might be unrelated [http://ubuntuforums.org/showthread.php?t=53094](http://ubuntuforums.org/showthread.php?t=53094) .

---

### Post by dawhippersnapper on 2005-12-03
It seems there's an issue in the kernel =P  

[http://kerneltrap.org/node/4872#comment-129554](http://kerneltrap.org/node/4872#comment-129554))

Going to try it when I get home.  Hopefully all goes well *crosses fingers*.

---

### Post by dawhippersnapper on 2005-12-03
[http://forums.gentoo.org/viewtopic-t-375914.html](http://forums.gentoo.org/viewtopic-t-375914.html)

I'm not alone in the world! =P

---

### Post by jlynaugh on 2006-01-28
I have the same problem with toten-xine playing too fast - Mplayer however
works perfectly

---

### Post by Nrvnqsr on 2006-01-28
you have a double clock issue, check your system manager and check if your processor is running at 50% while idle, if so try this thread

[http://www.ubuntuforums.org/showthread.php?t=75281&highlight=double+clock](http://www.ubuntuforums.org/showthread.php?t=75281&highlight=double+clock)

---

