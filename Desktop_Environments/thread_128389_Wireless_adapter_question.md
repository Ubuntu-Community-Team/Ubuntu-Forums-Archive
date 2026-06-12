---
title: "Wireless adapter question"
date: 2006-02-11
forum: Desktop Environments
---

### Post by PapaWiskas on 2006-02-11
What brand of pcmcia card or even usb and pci card is most compatible with Linux or Ubuntu.  My Ubuntu works great, but now I am considering buying the wireless Vonage Router finally.  And I would like to finally ditch all my hardline wires running through my living room.

I have two laptops, and building one mid tower unit, and all them will be running Linux, I am getting rid of my wifes Windoze PC.  She has been using my Ubuntu laptop and loves it, and is willing to change.

Thanks for your time.

---

### Post by GeneralZod on 2006-02-11
There are many wireless "b" cards (11mbps) that are very easy to get working under Linux, as long as you don't need WPA.  Wireless "g" with easy WPA support are quite a lot rarer, though.  Which kind do you need?

Ones to watch are the "ralink" ones which have GPL drivers available.  I'm not sure if I can recommend them just yet as the drivers are still under very heavy development, but eventually they will be pretty much the cards (USB, PCI and PCMCIA) to go for.

PS

I have that exact case badge stuck to the laptop I'm using right now :)

---

### Post by PapaWiskas on 2006-02-11
OK....so if I understand this right I should go for a wireless b card, but I wont be able to use encryption?

How do I secure my wireless network then.  Guess I have more reading to do then, drat!

The router I am getting is a Vonage Linsys G ....**I was hoping to be able to get G based cards**, but I guess those dont work in Linux yet or are rare?

If you have any further suggested links or advice Zod I would appreciate it.

p.s.  I ordered my badge this week....gonna put it on my new tower Im building.
Also ordered some Ubuntu stickers from the Ubuntu shop...putting one of them on my car. 
Does that classify me as a dork yet?

---

### Post by GeneralZod on 2006-02-11
[QUOTE=PapaWiskas]OK....so if I understand this right I should go for a wireless b card, but I wont be able to use encryption?

How do I secure my wireless network then.  Guess I have more reading to do then, drat!
[/QUOTE]

Well...I wouldn't  go as far as to say you should go with a "b" card (although there are other methods of securing wireless networks, such as only allowing specified MAC addresses to connect, and WEP for encryption, although the latter is easily broken nowadays), but the difference is between "Just Works" (like with my PCI and PCMCIA cards - no drivers need  to be installed, as they are part of the kernel) and "works with a lot of fiddling" :) I believe that the ralink cards are supported out of the box by Breezy, but may take a bit of work to get WPA working.  I'm not sure on this, though - best to search the forums for "rt2500" and see what experiences people have had.

> 
The router I am getting is a Vonage Linsys G ....**I was hoping to be able to get G based cards**, but I guess those dont work in Linux yet or are rare?


Let's just say that they are less common than well-supported "b" cards, but can still be found relatively easily :)

> 
If you have any further suggested links or advice Zod I would appreciate it.


I should probably point out that I am most definitely *not* an expert on any of this and have not done much research, so don't take my word as gospel :) You should definitely ask other people and do a bit of searching on the forums before making a decision.

A huge amount of cards are listed here, along with Linux support:

[http://linux-wless.passys.nl/](http://linux-wless.passys.nl/)

> 
p.s.  I ordered my badge this week....gonna put it on my new tower Im building.
Also ordered some Ubuntu stickers from the Ubuntu shop...putting one of them on my car. 
Does that classify me as a dork yet?

You have dork status the very moment you install Linux ;)

---

### Post by PapaWiskas on 2006-02-11
Thanks Zod, I checked out the link for the different cards.  Guess I just have to pick a good manufacturer.  What model of cards are you using?

Can anyone else share their make and model of wireless card in Ubuntu?

Please......

---

### Post by hugeness on 2006-02-11
i've been trying to get wireless to work with linux for <i>ages</i> without success.
i've just installed fedora core 4 and can confirm that did pick up a ralink wireless pci card (hooray!) (they are very cheap too) but i am in a city and so sensibly use wpa-psk which of course is missing from the configuration box in the network settings.
i'll try the pci card in the ubuntu box tomorrow (sunday) and let you know if / how well it works if you have not had a better answer by then (i am a newbie so far as actually configuring linux goes - been using it for years, but keep ditching it and coming back!).

---

### Post by henkeboy on 2006-02-12
I'm also going to buy a wireless network card and have been looking around for some Ubuntufriendly card. Check this out: [https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards](https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards)

---

### Post by GeneralZod on 2006-02-12
[QUOTE=PapaWiskas]Thanks Zod, I checked out the link for the different cards.  Guess I just have to pick a good manufacturer.  What model of cards are you using?

Can anyone else share their make and model of wireless card in Ubuntu?

Please......[/QUOTE]

For the record, here are my "b" cards.  I've never tried WPA on them. 

PCI - 3Com 3CRDW696
PCMCIA - Netgear MA401

I also own the following cards, all bought specifically because they use the ralink chipset.  I have not tested any of them yet, but will probably do so by Dapper, when the ralink drivers should be a lot more advanced (the last snapshots of the rt2500 and rt2570 are usable, I gather, but they are undergoing a total re-write and no further major development on the old drivers will be performed, so I'm just going to wait until the new, re-worked drivers have a stable release).  As I said, do a search on the forums for "rt2500" (PCI/PCMCIA) and "rt2570" (USB).

USB - ASUS 167g
PCI - [This one!](http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&item=5846662584&rd=1&sspagename=STRK%3AMEWN%3AIT&rd=1)
PCMCIA - ASUS WL-107g

Here's where the drivers for these three cards are being developed:

[http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page](http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page)

Be warned, though - wireless card manufacturers have been known to use completely different chipsets in the exact same model number, so buying the same model numbers as these is, very annoyingly, no guarantee of success! :(

---

### Post by Jason_25 on 2006-02-12
The wireless G atheros chip based cards like my Netgear WG311T work pretty well out of the box.  I haven't tried WPA though.

I also have a wireless B Netgear MA311 with a prism chipset that works out of the box.

---

### Post by hugeness on 2006-02-12
yep ralink pci 802.11g 54mbps is picked up automatically, this is good, because with windows the driver disk connects to their website without asking for some unknown reason.
i have used them extensively and they are just as good as any other and usually less than half the price. no wpa automated in the ubuntu activation, though there is a wep option.

---

### Post by waspinagermanhelmet on 2006-04-22
I have a PCI - 3Com 3CRDW696 which I picked up off ebay the other day - Which I notice that General Zod has... and I assume - working under ubuntu?

I have Kubuntu and I'd like to use this card to go wifi on that - so shouldn't be any different to set up - how do I do it?  :)

Thanks for your help! 

Craig

---

### Post by nickmcg on 2006-04-23
I'd recommend the rt2500/rt2570 if you're going to move to dapper drake. The support's already there, and wep works fine.

The broadcom chips are somewhat more problematic (for me) tho', needing ndiswrapper.


Cheers

Nick

---

