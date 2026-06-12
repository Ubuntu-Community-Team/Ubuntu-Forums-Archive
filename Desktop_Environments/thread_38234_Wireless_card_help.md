---
title: "Wireless card help"
date: 2005-05-30
forum: Desktop Environments
---

### Post by mis@nthrope on 2005-05-30
Hello, I can't get my wireless card to work in Kubuntu. I installed the driver via ndiswrapper according to the instructions at {http://www.ubuntulinux.org/wiki/SetupNdiswrapperHowto}. Then from the kcontrol dialog (which is annoyingly buggy) I tried to activate the wlan0 interface but after I activate it it deactivates in a few seconds. This didn't happen when I installed the card in Ubuntu. How can I fix it?

Thanks for any help :roll:

---

### Post by GeneralZod on 2005-05-30
When you enabled it, did you click the Apply button at the lower-right? I had the same problem with my wireless card, but after I clicked Apply it went on, and stayed on.

---

### Post by mis@nthrope on 2005-05-30
The apply button remains greyed out. I click on "Enable Interface", and it rapidly becomes disabled again (the green check mark stays up for like a second). ](*,)

---

### Post by mis@nthrope on 2005-05-30
While I'm at it, I have another question. How do I install things that aren't in kynaptic? Like I'd like to install the newest OpenOffice and KOffice betas to compare. I tried downloading the KOffice source and when I type "./configure" in the konsole it goes until it errs with "checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!" Honestly, installing stuff shouldn't be this hard! Can I install the binaries? I'm not even sure how to do this properly from the konsole and they're not in kynaptic. :-(

---

### Post by treris on 2005-05-30
I'm having problems with wireless cards as well, but I think you should be able to solve your KOffice and OpenOffice problems by adding additional repositories to your /etc/apt/sources.list. 

you can find the precise adresses and procedures on [www.ubuntuguide.org](www.ubuntuguide.org), which I recommend every (k)ubuntu user visiting at least once

good luck

---

### Post by mis@nthrope on 2005-06-07
Okay, so I got the wireless card to work (all I had to do was unplug my ethernet cable first) but I have to enable it every time I start up. Can I fix this? Also, I broke kynaptic a few minutes ago. Now it doesn't open, it just makes a busy cursor for half a minute and goes away. Restarting doesn't fix it. I don't know what I did, but maybe since I edited my etc/apt/sources.list, uncommenting the extra repositories. This is really annoying, seriously guys, I thought linux is supposed to be *less* of a headache than windows. :mad:

---

