---
title: "Screen Turns Black After Day of Normal Use"
date: 2009-02-02
forum: General Help
---

### Post by blink0072005 on 2009-02-02
I have a big problem with Ubuntu 8.10.  After about a day or two of normal use, I'll be typing or listening to music or doing any activity, and my screen will instantly turn black.  Often what will happen next is that I get an "X" for my cursor and splotches of color will appear and disappear on my screen (like it's trying to a load the picture).  Also, less frequently sometimes my system will completely freeze in place with the caps and scroll lock flashing.  A restart will fix the problem, but it will happen again within a day or two.

Does anyone have any idea as to what could be wrong?  This happens reliably once every other day or so, regardless of which kernel I pick at startup (27, 24, or 22).  I tried searching the forums but didn't have any luck.  Background info:  I had installed Ibex on a blank partition after wiping my Heron partition (an upgrade resulted in a kernel panic).  My computer dual boots with Windows XP.  I had not had this problem with Gutsy or Heron.

---

### Post by Crafty Kisses on 2009-02-02
What are the results of this command?
```
/var/log/xorg.0.log
```

---

### Post by blink0072005 on 2009-02-02
billy@billy-laptop:~$ /var/log/xorg.0.log
bash: /var/log/xorg.0.log: No such file or directory
billy@billy-laptop:~$ cat /var/log/xorg.0.log
cat: /var/log/xorg.0.log: No such file or directory

Good or bad sign?

---

### Post by blink0072005 on 2009-02-02
(bump)

---

### Post by Yashiro on 2009-02-02
tail /var/log/Xorg.0.log or less /var/log/Xorg.0.log

It's a capital X.

---

### Post by blink0072005 on 2009-02-03
Oh ok, thanks for catching that.  Here's the output of both commands.

tail:
--------------------------------------------------------
billy@billy-laptop:~$ tail /var/log/Xorg.0.log
(II) intel(0): EDID vendor "AUO", prod id 23105
(II) intel(0): DDCModeFromDetailedTiming: 1024x768 Warning: We only handle seperate sync.
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1024x768"x0.0   54.16  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (40.3 kHz)
(II) intel(0): EDID vendor "AUO", prod id 23105
(II) intel(0): DDCModeFromDetailedTiming: 1024x768 Warning: We only handle seperate sync.
(EE) intel(0): Mode 1280x1024 does not fit virtual size 1024x1024 - internal error
(II) PM Event received: Capability Changed
I830PMEvent: Capability change
--------------------------------------------

Less is really long.  I can put that in here if anyone needs it, but I'll wait to see before I fill up an entire page with it.  Thanks.

---

### Post by Yashiro on 2009-02-03
I'd reconfigure X back to defaults, re-install the latest driver for your video and see how that goes.

---

### Post by blink0072005 on 2009-02-04
Not to sound ignorant, but how I would go about doing that?

---

### Post by Yashiro on 2009-02-04
[http://www.cyberciti.biz/faq/ubuntu-linux-how-to-reconfigure-x-windows-system-xorg-server/](http://www.cyberciti.biz/faq/ubuntu-linux-how-to-reconfigure-x-windows-system-xorg-server/)

If you that doesn't work you can boot up into recovery mode from grub and do xfix.

If your issues aren't resolved after this then it's probably not a rudimentary driver problem.

---

### Post by blink0072005 on 2009-02-05
Ok great.  I tried the link you gave me, and will wait to see if I need to do xfix.  I'll post again when I'm sure.  Thanks for helping me so far.

---

### Post by blink0072005 on 2009-02-12
So after trying xfix several times, it didn't work; in fact, it made it so my computer freeze much faster! (sometimes within half an hour of use).  Any idea where to go from here?  I have a hunch it had to do with kernel panics, but I don't really have any concrete reason beyond the cap/num lock lighting in a similar fashion.

---

