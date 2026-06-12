---
title: "Display problem after fiddling with effects"
date: 2009-08-24
forum: Desktop Environments
---

### Post by codescribler on 2009-08-24
Hi All,

I have managed to mess up my display. I selected 'blur' from the effects menu and now when I log in after seeing my screen as normal, every time a window opens it gets blacked out until eventually the whole screen is black. The mouse still works. I tried going in to the command line from boot as was able to issue the command 'sudo apt-get remove compiz'. This command worked but did not resolve the problem. 

What can I try next?

Danny

---

### Post by altogether on 2009-08-24
haha I have just gotten a similar problem. What are the odds. My problem was caused by my doddling with the screen edges option. stuck yo.

---

### Post by altogether on 2009-08-25
Hey dude check this link out. Might work for you.

[http://www.ivankristianto.com/2009/06/howto-fix-ubuntu-jaunty-904-intel-graphics-problem/](http://www.ivankristianto.com/2009/06/howto-fix-ubuntu-jaunty-904-intel-graphics-problem/)

i'm going to try it now.

---

### Post by Mia1990 on 2009-08-25
Try resetting to the defaults

> [FONT=monospace]sudo dpkg-reconfigure -phigh xserver-xorg[/FONT]

---

### Post by codescribler on 2009-08-30
Thanks for the tip but unfortunately all the 'effects' still seem to be in place including the one that is blanking my screen. I have not tried the other posers suggestion as it appears to be reffering to a different sort of problem. We will see.

Thanks for the suggestion so far.

Still hoping for some more help though.

---

### Post by codescribler on 2009-08-30
> **altogether said:**
> Hey dude check this link out. Might work for you.

[http://www.ivankristianto.com/2009/06/howto-fix-ubuntu-jaunty-904-intel-graphics-problem/](http://www.ivankristianto.com/2009/06/howto-fix-ubuntu-jaunty-904-intel-graphics-problem/)

i'm going to try it now.

Unfortunately, I can not even get past the first step as I cant log in to the desktop. Command line access in the recovery mode only!

---

