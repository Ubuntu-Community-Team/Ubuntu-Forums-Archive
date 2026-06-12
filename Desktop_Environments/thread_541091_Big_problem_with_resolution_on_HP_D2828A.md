---
title: "Big problem with resolution on HP D2828A"
date: 2007-09-02
forum: Desktop Environments
---

### Post by thewolf32 on 2007-09-02
Hi everyone!

I recently installed Ubuntu Feisty Fawn 7.04 on my PC. I absolutly LOVE IT!

There is only one little BIG problem:

I have a monitor HP 52 D2828A, and it only shows resolution max. 800x600, when on windows XP it supports max 1024x768@60hz.

I've tried EVERYTHING, EVERYTHING! I've tried writing the syncs rates (horizontal 30-54, vertical 50-120), but when i do so after rebooting the monitor blinks it's LED like if there were no signal, so I have to reconfigure xorg. I've tried putting my monitor as Generic Monitor (1024x76 in xorg but it still shows a max. of 800x600. I've tried deleting everything else except 1024x768 on the screen section of the xorg.conf file but still nothing.

I've tried Knoppix liveCD, and it's too max 800x600.

This didn't happened in my old monitor.


Please, please help me I'm going nuts!!!!!!!!!!!!!!!!!!!!!!!! I can't stand 800x600!!!!!!!!!!!!!!!


My PC:

Graphics: S3 Graphics ProSavageDDR
Screen: HP 52 (D2828A)
Processor: Intel Celeron Northwood 2.00 Ghz
HD: 40 GB IDE
Mainboard: Biostar U8668-D

Sorry for some spelling problems!!!

---

### Post by thewolf32 on 2007-09-02
C'mon!! Nobody??? I'm really going like crazy for this issue!!!!!!!!

---

### Post by thewolf32 on 2007-09-02
Please!!!!!!!!!!!!!!!!

---

### Post by elderbuy on 2007-09-03
Do you know how much memory your video card has?  For some reason, both Edgy and Feisty Fawn install telling the system to default to a color depth of 24.  That takes more RAM, at high resolutions, than many older cards have.  I edited
      /etc/X11/xorg.conf
to set the default colour depth to 16, and I can now run at higher resolutions (up to 1024x768) on my old video card.

---

### Post by thewolf32 on 2007-09-03
I did that, still nothing. Help... help please heeeeeeeeeeelp!!!!!!!!!!!!!

---

### Post by thewolf32 on 2007-09-04
Help! I need somebody! HElp! Heeeeeeeelp!!!!!!1

---

