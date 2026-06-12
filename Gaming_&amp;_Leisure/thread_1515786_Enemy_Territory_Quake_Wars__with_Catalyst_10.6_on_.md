---
title: "Enemy Territory: Quake Wars  with Catalyst 10.6 on 64bit"
date: 2010-06-22
forum: Gaming &amp; Leisure
---

### Post by h0t1ce on 2010-06-22
I have tried running ETQW Demo using this guide here: [http://gwos.org/doku.php/guides:64bit:etqw]("http://gwos.org/doku.php/guides:64bit:etqw")

But unfortunately it just ends up with some errors. I tried the multithreaded script (see: etqw-rthread.txt) or single core script (see: etqw.txt) to launch the game but they both fail. I have also included glxinfo.

Here are my specs:
AMD Athlon II x3 435 (@2.9Ghz)
ATI HD5770 1Gb HIS
4Gb DDR2 @800Mhz

Using Ubuntu Lucid 10.04 64bit
Catalyst 10.6 for ATI drivers

Let me know if more info is needed

thanks in advance!


EDIT: I don't know why but piping the script to a log didn't contain all the information. Here's the end for each logs.

single core (etqw):
pure virtual method called
terminate called recursively
Segmentation fault


multicore (etqw-rthread):
X Error of failed request:  GLXBadRenderRequest
  Major opcode of failed request:  137 (GLX)
  Minor opcode of failed request:  1 (X_GLXRender)
  Serial number of failed request:  388
  Current serial number in output stream:  389

---

### Post by h0t1ce on 2010-06-24
Switching from ATI's Catalyst 10.6 to Ubuntu's ATI Proprietary driver through Hardware Drivers resolved this issue.

I was hoping someone could confirm ET:QW was working for them with Catalyst 10.6. The new 2D acceleration in the newest Catalyst driver makes minimizing windows much smoother.

---

### Post by meklu on 2010-07-29
The game (latest demo) works with 10.7 but only if launched from nautilus (ie. launching from terminal doesn't work, throws the same "GLXBadRenderRequest" error at me), which is quite odd. Other than that, it runs perfectly.

---

### Post by Cresho on 2010-07-30
use compiz.  also, 

sudo apt-get install compizconfig-settings-manager


right click on desktop and go to change desktop background and click on visual effects


application under system->preferences->advanced desktop effects settings->General settings->Display settings
Change the texture filter to "best", tick or untick"detect refresh rate"(this one was the one that made a difference and reboot the system between changes), bump to 200 "refresh rate", tick "Sync to vblank" and first tab unredirect fullscreen is ticked.

then your desktop will run smooth as silk

---

