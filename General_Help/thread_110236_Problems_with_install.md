---
title: "Problems with install"
date: 2005-12-30
forum: General Help
---

### Post by foulplay on 2005-12-30
System specs:
AMD Athlon 64 3700+
2GB DDR 400 RAM
Crossfire motherboard, onboard audio and NIC
ATI x800 in primary slot, nothing in secondary, set to single card mode.
120GB SATAII HDD

I'm not sure if it's my AMD64 processor, or my Crossfire motherboard, but when I install the AMD64 version of Ubuntu it just sends me to a black screen with "Username:" and says that X was not installed correctly and sends me to a scrambled screen.  I've tried reinstalling several times, with different CDs (including Kubuntu), but they all have the same effect.  I assume that this is because of Crossfire, and I was wondering if anyone else has encountered this, and has possibly come across a solution?

Thanks for any support,
Chris.

---

### Post by ThePerg on 2005-12-30
[QUOTE=foulplay]System specs:
AMD Athlon 64 3700+
2GB DDR 400 RAM
Crossfire motherboard, onboard audio and NIC
ATI x800 in primary slot, nothing in secondary, set to single card mode.

I'm not sure if it's my AMD64 processor, or my Crossfire motherboard, but when I install the AMD64 version of Ubuntu it just sends me to a black screen with "Username:" and says that X was not installed correctly and sends me to a scrambled screen.  I've tried reinstalling several times, with different CDs (including Kubuntu), but they all have the same effect.  I assume that this is because of Crossfire, and I was wondering if anyone else has encountered this, and has possibly come across a solution?

Thanks for any support,
Chris.[/QUOTE]


Don't feel bad, I have an identical system built to my 5.04 system and the 5.10 failes to install properly.. Try 5.04 and see what happens.. I bet you dont have the same problem.

---

### Post by foulplay on 2005-12-30
Going to try that out, downloading it as we speak.  Thanks for the quick response.

---

### Post by ThePerg on 2005-12-30
[QUOTE=foulplay]Going to try that out, downloading it as we speak.  Thanks for the quick response.[/QUOTE]


sure no problem, glad i could give you an idea.. Im installing 5.04 on that pc that 5.10 failed to install on.. so far.. flawlessly.. :)

---

### Post by foulplay on 2005-12-30
Just tried with 5.04, and it gives me a 'No paritionable media' error message.  :confused: but then I can boot into ***dows.

---

### Post by ThePerg on 2005-12-30
[QUOTE=foulplay]Just tried with 5.04, and it gives me a 'No paritionable media' error message.  :confused: but then I can boot into ***dows.[/QUOTE]

Do you have partition magic? if so delete the partition that 5.10 created.. and try again.. if not.. you'll have to fdisk to remove the 5.10 partition, you need a clean partition to install 5.04 onto. make sense? 

Are you trying to dual boot? are you placing 5.04 on the same physical disk?

---

### Post by foulplay on 2005-12-30
I tried using partition magic to clear the partition back to the way it was, but I think it's because I'm using a SATAII harddrive.  May be time to get a massive IDE drive (they're cheap enough now, just need a credit card).

---

### Post by ThePerg on 2005-12-30
[QUOTE=foulplay]I tried using partition magic to clear the partition back to the way it was, but I think it's because I'm using a SATAII harddrive.  May be time to get a massive IDE drive (they're cheap enough now, just need a credit card).[/QUOTE]


Well that could be if there are no drivers/packages to support SATAII in ubuntu it may very well not recognize you have a hard disk at all. I dont know if there is any drivers/support for SATAII hell I dont know SATA either.. 
what you could do is intall VPC in windows or VMware in windows and use a virtual PC for linux as I do.. until such time you know you have all the hardware/software and support to make it function as a standalone or dual boot setup.

do you have a smaller spare ide you can plug in temporarily to see it 5.04 will install onto IDE?

---

### Post by foulplay on 2005-12-30
[QUOTE=ThePerg]Well that could be if there are no drivers/packages to support SATAII in ubuntu it may very well not recognize you have a hard disk at all. I dont know if there is any drivers/support for SATAII hell I dont know SATA either.. 
what you could do is intall VPC in windows or VMware in windows and use a virtual PC for linux as I do.. until such time you know you have all the hardware/software and support to make it function as a standalone or dual boot setup.

do you have a smaller spare ide you can plug in temporarily to see it 5.04 will install onto IDE?[/QUOTE]
No unfortunitally I sold my old computer with the harddrive (after a secure erase).  I can run Ubuntu through VMWare, but I would prefer to have it stand alone.

---

### Post by ThePerg on 2005-12-30
[QUOTE=foulplay]No unfortunitally I sold my old computer with the harddrive (after a secure erase).  I can run Ubuntu through VMWare, but I would prefer to have it stand alone.[/QUOTE]


I can understand that.. I picked up an old DELL Precision 410 MT with a dual proc system board with 1 installed 500Mhz P3 196MB of ram and 2 9G IDE hard disk, it also has onboard SCSI, LAN, USB and AUDIO. I picked it up from this local (what I call PC WRECKHOUSE) for only $20 bucks I ordered a second proc from ebay for  $6 bucks and had a few extra PC100 sticks laying around.. It ran Windows like SHI$! but Linux runs like a champ on it..  not a bad standalone for $26 and few hours of work.

---

