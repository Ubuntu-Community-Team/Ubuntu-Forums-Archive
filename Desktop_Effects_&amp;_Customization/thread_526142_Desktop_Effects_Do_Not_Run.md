---
title: "Desktop Effects Do Not Run"
date: 2007-08-15
forum: Desktop Effects &amp; Customization
---

### Post by pigbig842001 on 2007-08-15
Hi,

I have recently made a new system. The specifications are:
1) Intel Core 2 Duo E4400 (2.0 GHz) processor
2) Intel DG965WH motherboard (200 MHz FSB)
3) Kingston 2x512 MB (667 MHz) RAM
4) Seagate 160 GB HD (SATA II, 7200 RPM)

The problem is, I am unable to run Desktop Effects on Feisty Fawn. When I click on it, the screen goes blank (white and nothing happens).

Is there any way I can get it to work??? Let me tell you that my system has onboard graphics (GMA X3000 which I suppose is 128 MB) which I suppose is enough. I have run "Need for Speed Most Wanted" at 1024x768 resolution with the highest graphics detail and it was able to pull it graciously so I think that I do not need a graphics card for the purpose.

Plz tell me how to get it to work. And plz do tell me whether I need a graphics card. And, do I need to install its (motherboard) drivers??? The motherboard drivers CD doesn't run on Ubuntu FF.

---

### Post by luisromangz on 2007-08-15
Do you have hardware accelerated graphics in ubuntu? If yes, your integrated graphics card drivers support AIGLX?

If the first question's answer is no, then you need to look for the correct drivers for your graphic card. 

The second question's answer will usually be yes if you have acceleration using open source drivers, if your card needs privative drivers to provide acceleration, maybe you need to deactivate AIGLX, and install and set up XGL instead.

There are a lot of info in this forum about these topics.

---

### Post by pigbig842001 on 2007-08-15
> **luisromangz said:**
> Do you have hardware accelerated graphics in ubuntu? If yes, your integrated graphics card drivers support AIGLX?

If the first question's answer is no, then you need to look for the correct drivers for your graphic card. 

The second question's answer will usually be yes if you have acceleration using open source drivers, if your card needs privative drivers to provide acceleration, maybe you need to deactivate AIGLX, and install and set up XGL instead.

There are a lot of info in this forum about these topics.
Hi,

How to check if I have hardware accelerated graphics in ubuntu??? and how to check if integrated graphics card drivers support AIGLX??? Sorry, I am totally a newbie.

Somebody told me to check this on terminal:

> nitro@nitrous-fumes:~$ glxinfo | grep direct
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  16
  Current serial number in output stream:  17

Plz help

---

### Post by pigbig842001 on 2007-08-18
Plz Help Me out Guys

---

### Post by pigbig842001 on 2007-08-18
Hello,

I have downloaded this **"xserver-xorg-video-intel_1.9.94.orig.tar.gz"**. Now I want to install it. Plz give me the steps to do it as I am a total newbie.

---

### Post by mmmkile on 2007-08-18
You would run the file in the terminal

---

### Post by pigbig842001 on 2007-09-13
Help me out guys. How do I install xorg. I have the .gz file downloaded. now give me the steps to install it :lolflag:

---

### Post by zabien1970 on 2007-09-13
I'm pretty much a n00b myself but you should already have xorg installed, type man xorg in a terminal and press enter, (man being short for manual), if it's installed you should have some basic instructions on it to start with, hope this helps.

---

