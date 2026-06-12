---
title: "Connecting To The Internet"
date: 2008-12-08
forum: Desktop Environments
---

### Post by DumbPoet on 2008-12-08
I just installed kubuntu on my machine and now I'm trying to connect to the wifi in this coffee shop. No dice.

I looked up some old posts and they suggested I'd have to hit ethernet first.. but that was over a year ago. Certainly that has been some advancement where I can set this up on a wireless network and have the my computer automatically detect networks while in kubuntu.

I saw some stuff about running commands to give more information about the nature of my problem. If you require that to help me, you'll have to give me a bit more direction than just what commands. I'm about 1.5 hours old with ubuntu at this point.

Thanks.

---

### Post by p_quarles on 2008-12-08
The first thing we need to know is the make of the wireless card installed in the laptop. Depending upon that, it could be anywhere from really easy to very difficult to get working fully. 

Try running this in the terminal:
```
lspci | grep Network
```

---

### Post by DumbPoet on 2008-12-09
Vista tells me that I have an Atheros AR5007EG Wireless Network Adapter.

I'll be back with the terminal results in a bit.

EDIT: When I run that in the terminal I get:

bash: ispci: command not found

Also, the screen had jitter runs in it when I booted up Ubuntu, like a failing digital signal. I believe it is because I haven't gotten the videocard driver up and running. When I try to use the simple interface it tells me I need some kind of administrative access and suggests a more complex way for me to go about enabling the driver.

Again, I am a complete newb with this stuff... I'm hoping this doesn't turn out to be a complex mess. I just want to use one program that runs in KDE. A program which didn't like the Windows port...

---

### Post by jacksaff on 2008-12-09
lspci not ispci
The following page has lots of info on getting that chip to work with linux.

[http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html)

You no longer have to use windows drivers through ndis wrapper, but the linux drivers are not yet part of the kernel by the looks of it so there are still hoops to jump through.

---

### Post by DumbPoet on 2008-12-09
> **jacksaff said:**
> lspci not ispci
The following page has lots of info on getting that chip to work with linux.

[http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html)

You no longer have to use windows drivers through ndis wrapper, but the linux drivers are not yet part of the kernel by the looks of it so there are still hoops to jump through.


After looking at my notes from last night's attempt the "i" was a typo. I tried it several times as an "l" in the terminal.

That link eventually led me to this tutorial, which is aimed at absolute beginners:
[http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/](http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/)

Apparently I'm going to have to get an ethernet cable no matter what solution I try...

Any thoughts on the problem I experienced with my screen in kubuntu?

---

