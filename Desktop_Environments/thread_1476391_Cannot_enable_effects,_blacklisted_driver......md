---
title: "Cannot enable effects, blacklisted driver....."
date: 2010-05-07
forum: Desktop Environments
---

### Post by Gi_Joe on 2010-05-07
Hey, im new to Ubuntu.
Took my laptop into the computer shop for a format and asked what they thought of Linux etc, they suggested i tried Ubuntu and installed it for me.
Ive been searching around trying to get past the fact that my graphics card is black listed so i can enable effects but am having no luck, im not to worried about flashy effects like the cube but i would like to tidy up my desktop as it is very cluttered with the original setup 

im not sure how to post a screen shot but all the icons are very big and un-appealing
would love to simplify it all and maybe have the window navigator along the bottom...
Im not to confident with using the Terminal, but have had a go at Compiz-Check etc and some random commands (hope i havent done any damage)
any help would be appreciated...
Cheers
Joseph

---

### Post by Gi_Joe on 2010-05-08
bump

---

### Post by martijntje on 2010-05-08
Which version of Ubuntu are you using and can you post the output of the command lspci ?

---

### Post by Gi_Joe on 2010-05-08
Ubuntu 10.04 


00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter



make any sense?

---

### Post by clhsharky on 2010-05-08
HI Gi_Joe

I have never been able to enable compiz on SIS chips. 
You can enable Metacity compositor, ubuntu tweek has a GUI .

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

Sharky

---

### Post by Gi_Joe on 2010-05-08
Cheers for that, much appreciated.
Joseph

---

### Post by Gi_Joe on 2010-05-09
installed Tweak but cant actually manage to change the appearance in anyway :( would love to just have the simple Ibuntu appearance that you see if you google Ubuntu........

---

### Post by P4man on 2010-05-09
Forget about compiz with that videocard. You should consider yourself lucky if you can get it to work properly in 2D. 

Anyway, Im not sure I understand what your problem currently is, but Im guessing its a too low resolution making icons and text too large and blurry? 

To post a screenshot, just press printscreen on your keyboard. Save the file, then attach it to a post here or upload it somewhere like to [http://imageshack.us](http://imageshack.us) and post a link here.

---

### Post by andrea000 on 2010-05-10
There's not really a way to ununblacklist a driver in 10.04
there is workaround's but i have not been able to get any of
them to work.So if anyone knows a way then please tell us.

---

### Post by RJARRRPCGP on 2010-05-10
Your video hardware sucks! 

Looks like you should just dump your laptop and get one with Intel graphics.

---

### Post by Gi_Joe on 2010-05-15
> **RJARRRPCGP said:**
> Your video hardware sucks! 
 
Looks like you should just dump your laptop and get one with Intel graphics.
 
wow thanks for your help with that one
 
all im trying to do is make my computer usable without re-installing windows or buying a new computer, thanks.
 
Im not sure what ive done now by pissing a,round, but when i start my computer now there is just a completley blank desktop, the bar along the top is still there with user name, off button etc but i cant actually open any thing :S
 
any ideas on making my desktop a. useable, and b. mildly attractive.....
 
cheers
Joseph

---

