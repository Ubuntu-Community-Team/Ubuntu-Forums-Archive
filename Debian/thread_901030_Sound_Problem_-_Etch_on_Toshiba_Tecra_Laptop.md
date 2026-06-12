---
title: "Sound Problem - Etch on Toshiba Tecra Laptop"
date: 2008-08-26
forum: Debian
---

### Post by GeneralSpecific on 2008-08-26
I know the problem...need to know how to fix it.

Running Etch on Toshiba Tecra 550cdt.  There is an io conflict with the sound card, it has been mentioned before by other's using this laptop.  

When I had DSL running on it I just had to add this*(or something real close..it's been awhile)* to the startup script to fix it:

[COLOR="navy"]modprobe opl3sa2 io=0x530 irq=5 dma1=1 dma2=0[/COLOR]

I have tried every variant I can think of on my debian install without success:

modprobe opl3sa3 " opl3sa23 " snd-opl3sa2
etc...

I keep getting the error message(or equivalent):

[COLOR="navy"]FATAL: module opl3sa2 not found[/COLOR]

When I look under /proc/asound/cards it lists

[COLOR="Navy"]0 [OPL3SA23       ]:OPL3SA23 - YAMAHA OPL3-SA23

[INDENT][/INDENT]YAMAHA OPL3-SA23 at 0x370, irq 5, dma 1&0[/COLOR]

Not sure what all that means, but pretty sure I need to get it to somehow say "as 0x530" to work.

My bios sound card settings are:
[COLOR="Red"]WSS I/O Address = 0x530 
SB Pro I/O = 0x220 
Synth I/O = 0x388 
WSS/SBPro/MPU401 irq = 5 
WSS (play) DMA = 1 
WSS (rec) & SBPro DMA = 0 
Ctrl I/O Address = 0x370 
MPU401 (MIDI I/F) = 0x330 [/COLOR]

Any help is greatly appreciated.

---

### Post by markharding557 on 2008-08-30
i think it means etch has no driver have you tried debian lenny or ubuntu they are much more up to date

---

### Post by GeneralSpecific on 2008-09-12
Thanks for the input!

I hate to say it, but I'm sure upgrading isn't the answer.  

I previously had sound working on this laptop using DSL 3.2, which runs the 2.4 kernel, and using a modprobe command to change the sound seeting in the bootlocal.sh.  I need to find how to do similar with etch.

Anyone else?

---

