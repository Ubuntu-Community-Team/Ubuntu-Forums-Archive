---
title: "GDM flickers in a loop"
date: 2010-08-09
forum: Desktop Environments
---

### Post by fabio2722 on 2010-08-09
Hi all,

this is my first post here! Last week I have received the ZaReason Teo netbook I have bought, all specs are here:

[http://zareason.com/shop/product.php?productid=16250&cat=250&page=1](http://zareason.com/shop/product.php?productid=16250&cat=250&page=1)
OS is Ubuntu Netbook Remix 10.04.

I have had it for 3 days now and haven't really played around with it very much: I have installed a few apps (skype, synergy, dropbox, texlive) and I've been basically getting acquainted, and I'm generally satisfied. 

A couple of hours ago I came back from the office, turned on the computer again and.. gnome started to flicker in an impossible loop! In one second, it will go completely white, then I'll see the purple Ubuntu background, then the application bar on the top and then white again. I see for a tenth of a second two suspicious arrows in the top left corner.

I have taken pics and made a sequence of the loop to help you guys understand:

[IMG]http://www.famsterdamworld.com/imagfab/loop.jpg[/IMG]

this happens immediately after login. when it loads, as in when you get "Ubuntu" and the 5 bullet points below, it doesn't flicker.

While the screen loops in the sequence, i can open a terminal (using Gnome DO) and do stuff. I have tried to stop GDM, using "sudo /etc/init.d/gdm stop"
What I then get is a command line interface where I can type something, but if I press ENTER nothing happens, it just goes to the next line. To restart the thing I need to press the power button off and on again. Here's the image of where I get. When I restart, it starts to loop again. 

[IMG]http://www.famsterdamworld.com/imagfab/gdmstop.jpg[/IMG]

I don't know what to do. While it loops I can enter commands in a terminal (thanks Gnome DO). I removed synergy but it didn't help either. As per now, it's really difficult and slow to interact with the machine, this really make it useless for anything I'd like to do with it.

I'm sure it's a Gnome problem, so maybe it's occurred before..?
Any help is heartily appreciated. 
regards
Fabio

---

### Post by Sangoma-1701D on 2010-10-03
Fabio,

Did you resolve this issue?
It's just started happening to me.
Exactly the same!

Thanks,

Barny.

---

### Post by fabio2722 on 2010-10-06
hi,

unfortunately my way to solve the problem was to nuke the computer and install a fresh new ubuntu. nobody seemed to know what was going on...

good luck and keep me updated in case you find out what caused it!

cheers

---

### Post by Sangoma-1701D on 2010-10-12
Ah well.

I've ended up doing the same.
Switching off updates now...

Barny.

---

### Post by Super Nade on 2010-10-18
I have a related problem on my laptop. Ubuntu netbook-remix installed properly, I can see the screen icons etc. However, when I move my mouse over the launcher on the left hand side, I experience crazy screen flickering. Extremely annoying...

lspci output:

```
septimus@laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 02)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)
02:01.0 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:01.1 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
03:00.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)

```

---

### Post by Super Nade on 2010-10-18
My problems disappeared when I switched to the 2D session of the netbook interface. It looks like the 2D version is lighter anyway, so I'm just going to stick with this. 

Just for the record, the issue is unresolved, but I've made my peace. :)

---

### Post by abhijitd on 2011-02-21
I am having the same problem as Super Nade.  How did you change to 2D session?  I am even able to get to the Administrator menu.  Thanks.

---

