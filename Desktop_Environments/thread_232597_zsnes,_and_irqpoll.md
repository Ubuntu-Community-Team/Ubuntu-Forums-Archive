---
title: "zsnes, and irqpoll?"
date: 2006-08-08
forum: Desktop Environments
---

### Post by dennisharrison on 2006-08-08
ok, I have reinstalled my old upgraded from hoary to breezy to dapper machine and have dapper dual booting with windows.  I was able to get the fglrx drivers working (oh, my, god... it was easy after a reinstall) I bought codeweavers crossover and transgaming cedega. So, everything is good.

ZSNES : whenever I use an advanced filter other then bilinear I drop from 60+ fps to 27 or 28 (I have a 939 pin athlon 64 3200 1.5gb of memory sata hdd and a radeon 800xl)  I compiled the newest zsnes from source.  Am I just stuck in ati hell? anyone else out there with an ati card and using advanced graphics filters with zsnes at full speed?

I have an ATI 480 chipset on my mb, to get the install cd to boot I had to use pci=noacpi and irqpoll.  I have since updated my bios and thats supposed to enable me to not use irqpoll or pci=noacpi... So when I got the slowdowns in zsnes I checked grub to see if its in the boot line for this kernel.  And its not.  How can I tell if these options are loaded anyway? because as far as opengl performance goes I am getting much better performance on windows.  This didn't used to be the case with breezy.  It was only a slight advantage to windows.  I have yet to install WoW so that will be the clincher.  

Does anyone have advice? I have spent a few hours on google between this and trying to get visio 2003 open files, and I have come up short on both ;p

Thank in advance for any replies (any, whatsoever, even if its a I have no clue)

Dennis

---

### Post by dennisharrison on 2006-08-09
bump

I have not yet gotten one response to any of my 3 messages over 2 forums on ubuntuforums.org

I have tried to help out everyone I could while waiting for a response every time.  
Why is that?

---

### Post by dennisharrison on 2006-08-09
one more bump before bed

no one has any information?

---

### Post by philippe_carlo on 2006-08-09
Why don't you just add the boot parameters to the boot line and try that once? Also, this may just be an ATI screw-up in the Linux drivers. I for one have an ATI card, but the driver keeps me from running compiz because it's broken.

---

### Post by dennisharrison on 2006-08-09
I don't have anything on the boot line (except boot), so I wanted to know if there was some way to see if somehow because I had to use those options to install with if they became default in a file somewhere.

---

