---
title: "Best ATI driver?"
date: 2006-08-31
forum: Desktop Environments
---

### Post by srunni on 2006-08-31
Is the official driver or the unofficial driver better?

---

### Post by Greycloak on 2006-08-31
The 8.28.8 drivers from ATI seem to work the best for me.

---

### Post by Ziox on 2006-08-31
it all depends on your graphic card. there are two sources that you can install the drivers from.  One is from the repository via synaptic or apt-get.  This version has decent support for a verity of cards.  However, it might not work for recent, high-end cards.  

There is a binary driver provided by ATI.  This binary driver has more and better support for recent cards, and it might have the possiblities of increasing performance gains over the open-source driver (from repos). However, as times goes on, ATI tend to drop support for older cards (such as mine) :(.

So it all depends on the card.

Another thing, most of the time, the open-source driver is easier to install than the binary one...

Hopefully this helped

---

### Post by Anduu on 2006-08-31
Yep...for older cards like mine(Radeon 9600...) the driver from the repos is better.

If you have a newer one go with the proprietary driver from ATI.

---

### Post by Greycloak on 2006-08-31
According to the release notes on the 8.28.8 driver, older cards are supported.  I'm using it on a Radeon 9200 PCI.

---

### Post by Ziox on 2006-09-01
> **Greycloak said:**
> According to the release notes on the 8.28.8 driver, older cards are supported.  I'm using it on a Radeon 9200 PCI.

it may support yours, but for my card (ATI 340m IGP) isn't supported.  I can't even boot with fglrx as the driver :-& 

But the repos driver allows me to boot and enables 3d rendering out-of-the-box...:p

---

### Post by jmattos on 2007-03-09
Hmm

I'm trying to pick a driver also for my ATI Radeon x1800, which is pretty recent. I think i'm going to go with the driver from ATI

[http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html) (version 8.34.8)

and follow the slightly more complex directions I found here.
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI?highlight=(Driver)%7C(ATI)#head-99489608eb537a1a0346cdd3ad34209d7887714a](https://help.ubuntu.com/community/BinaryDriverHowto/ATI?highlight=(Driver)%7C(ATI)#head-99489608eb537a1a0346cdd3ad34209d7887714a)

Does this make sense?

---

### Post by srunni on 2007-03-09
> **jmattos said:**
> Hmm

I'm trying to pick a driver also for my ATI Radeon x1800, which is pretty recent. I think i'm going to go with the driver from ATI

[http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html) (version 8.34.8)

and follow the slightly more complex directions I found here.
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI?highlight=(Driver)%7C(ATI)#head-99489608eb537a1a0346cdd3ad34209d7887714a](https://help.ubuntu.com/community/BinaryDriverHowto/ATI?highlight=(Driver)%7C(ATI)#head-99489608eb537a1a0346cdd3ad34209d7887714a)

Does this make sense?

Yeah, I used the proprietary driver from ATI, and it's worked fine for me.

---

### Post by jmattos on 2007-03-12
> **srunni said:**
> Yeah, I used the proprietary driver from ATI, and it's worked fine for me.

Well, I installed the binary driver and everything looked fine, but whenever I start up, after 10 minutes, the screen goes blank, and wont come back... and i have to reboot.

That happened with the binary driver as well as the one bundled with Ubuntu.

Ugh. sound familiar to anyone?

---

### Post by geirha on 2007-03-12
First driver I tried for my ati radeon 9800 was the latest ( 8.34.8 ), but it hung the entire machine whenever I logged out or switched user, so I tried the envy package, [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) , which selected 8.33.6 for me and installed it without a glitch. And it's been working perfectly ever since :)

---

### Post by srunni on 2007-03-13
I actually do have problems with logging out, but since I rarely log into an account other than mine, I just open a tty (with ctrl+alt+f1-12) and run ```
sudo halt
``` when I want to turn it off and it works fine.

---

### Post by purefan on 2007-03-14
wow sounds like its actually a "dangerous" process this installing of the video card driver.... so, I got an AMD64 system but running Ubuntu Edgy (6.10) wit ha vid-card ATI X1600, which way do you recommend I go? ATI's driver or Repos?

---

### Post by srunni on 2007-03-14
Use Envy: [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)
It's an automated script for ATi and NVIDIA, and works with Ubuntu 6.06 or 6.10, x86 and x64 editions. Here is a direct link to the .deb installer file you want to download: [http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.1-0ubuntu3_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.1-0ubuntu3_all.deb)
All you have to do is right-click on it and choose install.

---

### Post by purefan on 2007-03-14
ok installin ATI driver according to Envy.... hope it works :) wish there was a Restore Point hehe (yeap, windows user)

---

### Post by srunni on 2007-03-15
Well, be sure to report back how well it works :)

---

### Post by purefan on 2007-03-15
it was absolutely marvelous!! after downloading Envy and installing it he offered me 4 options, to install the nVidia driver or the ATI driver, manually or automatically, of course I chose Auto. opened a console, shook its magic wand... then he said "do you want me to fix your .xorg (this is recommended)" -> Clicked Yes!, then "do you want to reboot your computer now (recommended)" -> Yes please!
when it was done rebooting it all looked much better, I could set higher resolutions and of course the graphic acceleration was working, everything seems to be working fine and Ive left the computer alone for many hours without going blank or anything, been working many hours too and its alright!

Envy made my day!

---

### Post by srunni on 2007-03-16
Sounds great! Back when I installed my driver, there was no Envy :( Had to manually edit xorg.conf, which is a complete pain. I'll be sure to try Envy when I reinstall Ubuntu.

---

