---
title: "Black screen after installation"
date: 2008-01-15
forum: Dell  Ubuntu Support
---

### Post by yaguang on 2008-01-15
I was able to use the LiveCD fine and install Ubuntu on the laptop, however when I tried to boot it all I got was a black screen. The recovery mode works fine. 
Here's the laptop's specs:

Dell Inspiron 5100 Laptop
Intel Pentium 4 CPU 2.4GHz
512MB of RAM
ATI Mobility Radeon 7500

Much appreciated

---

### Post by Omnios on 2008-01-15
Had this problem before and it was that xserver was not set up properly for the monitor screen. You might want to research this on this forum.

 There is also a command that you can run in text or recovery mode.

 Sudo dpkg-reconfigure xserver-xorg

 This brings up a turtle like graphics sceen where you can set up the keyboard mouse and vid settings. It may be kind of confusing but the monitor section may help you solve your problem. 

 Also you might want to try the versa graphics driver which is a standard vga driver to let you get the screen to see if its working.

 Warning never push the monitor frequency higher than what is there unless you are sure you monitor is rated as such!

---

### Post by Mystix on 2008-04-08
To get the text mode I used Clt-Alt-F1.  Also I had this problem and ended up just doing a fresh install of 7.10 after that no problems.

---

