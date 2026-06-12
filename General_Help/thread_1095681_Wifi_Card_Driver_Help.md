---
title: "Wifi Card Driver Help"
date: 2009-03-14
forum: General Help
---

### Post by Miroku419 on 2009-03-14
I have a Realtek 8101 and I wanted to use it with kismet w/e else for things like mitm attacks.  This is not going to be used illigally - it is going to be used on my home network.  It's just, now that i got a laptop, I dont want to keep it hooked up to an ethernet cord.  I think I need to get something like madwifi but i need one for realtek.  If anyone would please give step-by-step "tutorial" on how to do this?

Oh and im a bit new to ubuntu so please dont expect i know what to do for most things...

---

### Post by 3l3vans on 2009-03-14
first of all...do some research...

1.check in "hardware drivers" (its in one of your menus-i can't remember which off of the top of my head)-i think its under "system"-fi you find it click on it and it should be pretty self explanatory.

2.if that doesn't work..

search "ndiswrapper how to"

and post again... ndiswrapper is a little complicated but i would be glad to tell you what i know about it...3l

---

### Post by Miroku419 on 2009-03-14
> **3l3vans said:**
> first of all...do some research...

1.check in "hardware drivers" (its in one of your menus-i can't remember which off of the top of my head)-i think its under "system"-fi you find it click on it and it should be pretty self explanatory.

2.if that doesn't work..

search "ndiswrapper how to"

and post again... ndiswrapper is a little complicated but i would be glad to tell you what i know about it...3l

The only thing listed in the hardware drivers is my gfx card.  And ndiswrapper... i went to open it - and i had to install it - after that - says no utilities found...  im not really sure wat ndiswrapper is so idk what to do..

---

### Post by 3l3vans on 2009-03-14
ok ndiswrapper is a program that only works from the command line...but that will come later....now you need to search the name of your card, OR the chipset of your card...then you need to find the "driver" for said card...THEN you can use ndiswrapper...you might want to search "ndiswrapper" and your card/chipset to see if anyone has posted anything about it working or not...3l

---

### Post by Miroku419 on 2009-03-14
> **3l3vans said:**
> ok ndiswrapper is a program that only works from the command line...but that will come later....now you need to search the name of your card, OR the chipset of your card...then you need to find the "driver" for said card...THEN you can use ndiswrapper...you might want to search "ndiswrapper" and your card/chipset to see if anyone has posted anything about it working or not...3l

this?
[http://drivers.softpedia.com/get/NETWORK-CARD/REALTEK/Realtek-RTL8100-8101-8110-8130-8139-8169-version-663-WHQL.shtml](http://drivers.softpedia.com/get/NETWORK-CARD/REALTEK/Realtek-RTL8100-8101-8110-8130-8139-8169-version-663-WHQL.shtml)

googled ndiswrapper realtek

if you could IM me it would be much help..
yahoo - [email]miroku419@ymail.com[/email]
msn - [email]dark_angel_41992@hotmail.com[/email]
aim - kryxis

---

### Post by 3l3vans on 2009-03-14
could you do me a favor and open a "terminal" so i we can get some info for your card? 

when you get it open just type "lspci" and hit enter...a list will apear...

if you look near the bottom of that list (its near the bottom on mine) there will be a line about your wifi (it might say something like...bla bla bla WIRELESS LAN 802.bla. bla

that is the name of your "chipset" 

search for a driver using that name

if they are the same then your cool

if they are not, i would go with the "chipset" driver first,and bookmark the other one because you might need it later...3l

---

### Post by 3l3vans on 2009-03-14
and then post your chipset...we'll see if i come up with the same...AND THEN ndiswarapper + driver = wifi card works...

---

### Post by Miroku419 on 2009-03-14
> **3l3vans said:**
> could you do me a favor and open a "terminal" so i we can get some info for your card? 

when you get it open just type "lspci" and hit enter...a list will apear...

if you look near the bottom of that list (its near the bottom on mine) there will be a line about your wifi (it might say something like...bla bla bla WIRELESS LAN 802.bla. bla

that is the name of your "chipset" 

search for a driver using that name

if they are the same then your cool

if they are not, i would go with the "chipset" driver first,and bookmark the other one because you might need it later...3l

```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3650
01:00.1 Audio device: ATI Technologies Inc RV635 Audio device [Radeon HD 3600 Series]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
04:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
04:06.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
04:06.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
04:06.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
04:06.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

```

not sure what i need here - only wireless i see is the wifi link 5100 but - idk... sorry i feel dumb rite now..

---

### Post by Miroku419 on 2009-03-14
and not sure if you are doin this but - my wireless is working - its just that i want to be able to use it with like kimset - so i need the "madwifi" for realtek..

---

### Post by 3l3vans on 2009-03-14
don't feel stupid...

it took me two weeks to figure out how to make mine work...but now it works

i think this is what you are looking for

03:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100

is your chipset

so get the driver unpack it anywhere you like....


and then switch gears





the way ndiswrapper works is you tell it to install two files (the ****.inf file and the *****.sys file...they will be in the same folder somewhere in the driver you download...if there is a file README or INSTALL check it out it might tell you where those files are...

create a folder in your "home" (home is where i do it you can put this file somewhere else if you like) folder called ndiswrapper

copy ******.sys *******inf to that folder

you can get rid of the rest of the driver package later but hang on to it for now (in case you need to get .inf and .sys again)

then open a terminal

#cd /path to inf file/where ever you copied it to/bla


(cd is "change directory" - you are essentially going to the the directory that you copied those two files to)---





#ndiswrapper -i *****.inf

then

#ndiswrapper -m


then



#ndiswrapper -l


(this will tell you what driver ndiswrapper has installed)



(you might need to be root i am not sure-i will explain that if you need it)

---

### Post by 3l3vans on 2009-03-14
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAH...see whose the stupid one now? i'm terribly sorry....i misunderstood your question :(

---

### Post by Miroku419 on 2009-03-14
> **3l3vans said:**
> don't feel stupid...

it took me two weeks to figure out how to make mine work...but now it works

i think this is what you are looking for

03:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100

is your chipset

so get the driver unpack it anywhere you like....


and then switch gears





the way ndiswrapper works is you tell it to install two files (the ****.inf file and the *****.sys file...they will be in the same folder somewhere in the driver you download...if there is a file README or INSTALL check it out it might tell you where those files are...

create a folder in your "home" (home is where i do it you can put this file somewhere else if you like) folder called ndiswrapper

copy ******.sys *******inf to that folder

you can get rid of the rest of the driver package later but hang on to it for now (in case you need to get .inf and .sys again)

then open a terminal

#cd /path to inf file/where ever you copied it to/bla


(cd is "change directory" - you are essentially going to the the directory that you copied those two files to)---





#ndiswrapper -i *****.inf

then

#ndiswrapper -m


then



#ndiswrapper -l


(this will tell you what driver ndiswrapper has installed)



(you might need to be root i am not sure-i will explain that if you need it)

could you please give a link to the driver i should download?  im findin almost all windows drivers..

also.. what im finding is people referring drivers to people that cant get it to work - but my wifi is working...

dont i need a certain driver to be able to do the injection for mitm attacks and stuff?  my wifi works but - everytime i look up for wep cracking..  it says the wifi card must be setup for injection..  and they give a tutorial with madwifi for ath. card - but idk what to do for mine..

---

### Post by Miroku419 on 2009-03-14
thanks for  tryin to help but im dead tired - its 3 am here... im gunna goto bed...  if you wouldn't mind helpin tomorrow - please add me on a messenger..

yahoo - [email]miroku419@ymail.com[/email]
msn - [email]dark_angel_41992@hotmail.com[/email]
aim - kryxis


thanks

---

### Post by Miroku419 on 2009-03-14
> **3l3vans said:**
> AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAH...see whose the stupid one now? i'm terribly sorry....i misunderstood your question :(

oh so your not able to help me with this?

---

### Post by 3l3vans on 2009-03-14
no i am a doof...i dont even know what kimset is, thought it was a brand name...VERY SORRY ;( .

---

