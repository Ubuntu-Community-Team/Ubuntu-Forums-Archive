---
title: "been trying to connect to internet for 12 hours"
date: 2009-05-04
forum: General Help
---

### Post by hisham89 on 2009-05-04
hi i installed ubuntu 8.04 yesterday and its my first time on linux i've tried to install my isp but i couldn't tried to install any program but also i couldn't when i try to listen to a song or watch a movie i get an error for codecs update which i cant do without internet my pc :
P4
ram: 1 gega ddr 1 
vga: nvidia geforce 6200 128mb
ubuntu installed on D cause i have xp on my C
i have a usb modem with an installation cd working well on XP but i have tried everything u can imagine but i couldnt make it work so plz i need help i tried my best i have been awake for over 24 hours trying to do anything plz i wish to fine help here thanks in advance
my isp is a usb modem speedtouch all what i need is someone to help me and tell me what to do     :confused::confused::confused::confused::confused::( oh and i installed ubuntu by wubi

---

### Post by psmar on 2009-05-04
who is your service provider, and is it a cable or dsl, fibre???

---

### Post by delcypher on 2009-05-04
I imagine you need the firmware to use your Speedtouch USB modem. I don't know if Ubuntu has built in support.

Have you [read this?]("http://linux-usb.sourceforge.net/SpeedTouch/ubuntu/index.html")

---

### Post by Kevbert on 2009-05-04
Welcome to Ubuntu.
Please post your USB make and model. You probably need to install firmware drivers for it.

---

### Post by hisham89 on 2009-05-04
Hi all and thanks for ur reply my usb modem is Alchatel speedtouch and its a dsl.My service provider is TE-DATA is that info what u need or something else?

---

### Post by hisham89 on 2009-05-04
oh i looked up my device manager from windows XP and fount that: modem: conexant soft56 data fax modem and from Networking: i found Marvel Yukon 88E8001/8003/8010 PCI GIGABIT ethernet controller AND speedtouch ethernet adapter i dont know if that info useful for help or not :D ?

---

### Post by psmar on 2009-05-04
have you checked to see if ubuntu has seen it, maybe "lspci, or dmesg? if its seen it just might be setting up the protocol that your provider requires to connect?

---

### Post by hisham89 on 2009-05-04
> **psmar said:**
> have you checked to see if ubuntu has seen it, maybe "lspci, or dmesg? if its seen it just might be setting up the protocol that your provider requires to connect?
 what do u mean by check if ubuntu see it. look its my first time on ubuntu i dont know anything, the terminal thing is very hard to use 
and i want to know if there is anyway to setup programs without using terminal 
like if i download programs for linux while i'm online on XP. i downloaded many programs from xp and tried to install them on linux but i couldn't deal with the terminal

---

### Post by BslBryan on 2009-05-04
Your operating systems don't speak to each other, hisham89.  If you got a virus for Windows XP in Ubuntu, that virus would not take effect unless you shared folders between the two operating systems (i.e. sharing a music folder so anytime you download music in XP it also applies to Ubuntu.)

If you want to install anything for Ubuntu, you have to download it on XP and burn it to a disk, thumb drive, or external hard drive, and then shut down and boot Ubuntu.

Okay, now open up the terminal, and type this:
```
lspci
```

You can copy and paste that into it, if you'd like.  Next, copy the result from the terminal and save it, in openoffice, as a .doc file, to a flash drive.  Now boot up XP and copy and paste the results in a post here on the forums.  I'm sorry to say that since you don't have an internet connection yet, you'll be doing a lot of restarts.

Anyway, we'll get you working soon, it just might take a little work from all of us.

Don't give up, and Google is your best friend.

Good luck. :)

---

### Post by Kevbert on 2009-05-04
Unfortunately it's not straightforward to set up your modem in Ubuntu. Please take a look at this [COLOR="Red"][guide]("https://help.ubuntu.com/community/UsbAdslModem")[/COLOR].
To see if the USB modem is recognized you can use the following command in Applications-Accessories-Terminal
```
lsusb
```
(that's list usb devices, 'lspci' lists only pci connected devices). The information displayed may not mean much to you, but may be worth posting anyway.
The other command you could try is
```
lshw
```
this will list all connected hardware, including any connected modems.

---

### Post by hisham89 on 2009-05-04
> **BslBryan said:**
> Your operating systems don't speak to each other, hisham89.  If you got a virus for Windows XP in Ubuntu, that virus would not take effect unless you shared folders between the two operating systems (i.e. sharing a music folder so anytime you download music in XP it also applies to Ubuntu.)

If you want to install anything for Ubuntu, you have to download it on XP and burn it to a disk, thumb drive, or external hard drive, and then shut down and boot Ubuntu.

Okay, now open up the terminal, and type this:
```
lspci
```You can copy and paste that into it, if you'd like.  Next, copy the result from the terminal and save it, in openoffice, as a .doc file, to a flash drive.  Now boot up XP and copy and paste the results in a post here on the forums.  I'm sorry to say that since you don't have an internet connection yet, you'll be doing a lot of restarts.

Anyway, we'll get you working soon, it just might take a little work from all of us.

Don't give up, and Google is your best friend.

Good luck. :) 
hi bryan first thanks to ur reply. ok i have no virus on XP so no worries about virus
oh i forgot to tell u that i installed  (hsfmodem_7.80.02.04full_i386.deb) i read it in some help text but i dont know what is it and will it affect anything that we will try to do now or not. and about downloading programs for linux and burn it on a cd what type do i have to choose burn data or what exactly? and sorry for my stupid questions but really thats my first time on ubuntu and am really used to windows so its hard for me the terminal thing and about the programs i'll download i need only a vedio and audio program to make movies and songs work cause the programs installed with ubuntu need codecs which i cant get without internet so if i downloaded lets say VLC will it also need codecs or what?
so for now i'll write the command u gave me and post the result in here till u tell me what to do after that and thanks for ur effort

---

### Post by hisham89 on 2009-05-04
i saved the data as u said with odt format but i cant open it with any program from windows to past it here what shall i do ????

---

### Post by hisham89 on 2009-05-04
> **Kevbert said:**
> Unfortunately it's not straightforward to set up your modem in Ubuntu. Please take a look at this [COLOR=Red][guide]("https://help.ubuntu.com/community/UsbAdslModem")[/COLOR].
To see if the USB modem is recognized you can use the following command in Applications-Accessories-Terminal
```
lsusb
```(that's list usb devices, 'lspci' lists only pci connected devices). The information displayed may not mean much to you, but may be worth posting anyway.
The other command you could try is
```
lshw
```this will list all connected hardware, including any connected modems.
 
i've done that commands but they are in odt format and i cant open  them with any windows program so what to do to paste them for you?

---

### Post by hisham89 on 2009-05-04
[ATTACH]112422[/ATTACH]

[ATTACH]112423[/ATTACH]

[ATTACH]112424[/ATTACH]


i uploaded them for u guys to see them
thanks

---

### Post by Kevbert on 2009-05-05
As I suggested earlier there is no easy way of installing the drivers and getting your modem working. I believe the correct driver is attached to this post. The best method I've found so far is [[COLOR="Red"]this[/COLOR]]("http://www.vivaolinux.com.br/topico/Modems/INTERNET-DISCADA?num_por_pagina=12&pagina=3") and it involves playing around with commands in terminal (Applications-Accessories-Terminal).
It may be easier to get a Broadcom based USB modem!!!
Good luck.

---

### Post by vahnx on 2009-05-05
I also have a SpeedStream DSL Modem, it came with a USB Connector as well as an Ethernet cable. If you have a Windows machine using the Ethernet cable, connect that to your Ubuntu box and install the USB drivers to your other machine and use USB on it. That was my workaround before I decided to get a wireless router. Other than that, I don't think theres a way to get the SpeedTouch USB working in Ubuntu I'm afraid.

---

### Post by hisham89 on 2009-05-05
> **Kevbert said:**
> As I suggested earlier there is no easy way of installing the drivers and getting your modem working. I believe the correct driver is attached to this post. The best method I've found so far is [[COLOR=Red]this[/COLOR]]("http://www.vivaolinux.com.br/topico/Modems/INTERNET-DISCADA?num_por_pagina=12&pagina=3") and it involves playing around with commands in terminal (Applications-Accessories-Terminal).
It may be easier to get a Broadcom based USB modem!!!
Good luck.

so u mean i can't make my usb modem work on ubuntu 
if that then there is no need for ubuntu to stay on my pc since there is no internet therefore no programs or anything
is that right or am wrong
ok what about the dial-up can i make it work on ubuntu or not?

---

### Post by Kevbert on 2009-05-05
It is possible to get this modem working in Ubuntu, but it's not straightforward as per the links. For someone starting new, in Ubuntu or Linux, this may be a problem.

---

### Post by hisham89 on 2009-05-05
> **Kevbert said:**
> It is possible to get this modem working in Ubuntu, but it's not straightforward as per the links. For someone starting new, in Ubuntu or Linux, this may be a problem.
So can't u guys help me to make it work just tell me all the info u need and i'll get it for u
cause u know i can't do anything in  UBUNTU  without an internet connection

---

