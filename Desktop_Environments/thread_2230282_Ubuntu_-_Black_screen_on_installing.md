---
title: "Ubuntu - Black screen on installing"
date: 2014-06-18
forum: Desktop Environments
---

### Post by Ulrich_Baeyens on 2014-06-18
I've tried both installing from windows, cd, usb..
Everytime i install it i get till the install screen, choose my language, or it says it's finishing instalation.
But whenever i choose install i either keep staring at the ubuntu loading screen, or i get a complete black screen, had my screen go in stand-by mode a few times aswell.
I've tried alot already, any idea's? Had it with ubuntu 14,12,13..

System : 

Time of this report: 6/18/2014, 17:49:38
       Machine name: ULRICH-PC
   Operating System: Windows 7 Home Premium 64-bit (6.1, Build 7601) Service Pack 1 (7601.win7sp1_gdr.140303-2144)
           Language: Dutch (Regional Setting: Dutch)
System Manufacturer: To Be Filled By O.E.M.
       System Model: To Be Filled By O.E.M.
               BIOS: BIOS Date: 09/12/12 14:27:21 Ver: 04.06.05
          Processor: Intel(R) Core(TM) i5-3450 CPU @ 3.10GHz (4 CPUs), ~3.1GHz
             Memory: 8192MB RAM
Available OS Memory: 8132MB RAM
          Page File: 2225MB used, 14035MB available
        Windows Dir: C:\Windows

      Card name: AMD Radeon HD 7800 Series
       Manufacturer: Advanced Micro Devices, Inc.
          Chip type: AMD Radeon Graphics Processor (0x679E)
           DAC type: Internal DAC(400MHz)
         Device Key: Enum\PCI\VEN_1002&DEV_679E&SUBSYS_E246174B&REV_00
     Display Memory: 4095 MB

Hope you can help!

---

### Post by LastDino on 2014-06-18
I might know the cause but no definite solution; your graphic card seems to not like opensource drivers. 

There is probably better way to tackle this, but I would simply remove graphic card till I get installer running and finish the installation, then see if I can get into grub after attaching it again. If I can, I would, try to boot from ''nomodeset'' and then install third party drivers from ''software & update manager'' in Ubuntu settings.

All this is assuming, it is indeed GPU card and I suspect there is better way to tackle this, so I would wait for someone more knowledgeable to grace this thread with their response.

---

### Post by Ulrich_Baeyens on 2014-06-19
Remove the gfx card? I wouldn't be able to see a thing? :p
Or run it on my integrated? Idk if that's possible.
Thanks anyways hah, i'll wait as you say.

---

### Post by LastDino on 2014-06-19
People can run their monitors on board graphics fine,  I do the same.

Just remove your monitor cable attached to your card and then plug it to the port on mother board which looks similar to your graphic card port. Its even designed to make sure pin goes in as it is supposed to, to make it idiot proof ;)

Just make sure you remove the card from mother board before you start the computer, or you really will see black screen with blue window floating around which says ''no signal''

---

