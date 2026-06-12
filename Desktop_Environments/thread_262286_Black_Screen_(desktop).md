---
title: "Black Screen (desktop)"
date: 2006-09-21
forum: Desktop Environments
---

### Post by locohygynx on 2006-09-21
i am trying to boot ubuntu off the cd and it asks if i want to install/run it, i select it and it goes to a "loading" screen where it starts saying stuff is ok. after a while the screen goes black and nothing happens. i can type stuff in the screen but nothing. i tried this same disc on my work computer (Dell) and it worked fine. my home pc specs are:

<<< System Summary >>>

  > Mainboard : Asus Grafito

  > Chipset : Intel i915G

  > Processor : Intel Celeron D 336J @ 2800 MHz

  > Physical Memory : 512 MB (2 x 256 DDR2-SDRAM )

  > Video Card : Intel Corporation 82915G/GV/GL, 82910GL Integrated Graphics Device

  > Hard Disk : ST3160023AS (160 GB)

  > Hard Disk : LEXAR (1 GB)

  > DVD-Rom Drive : HL-DT-ST DVDRRW GWA-4161B

  > Monitor Type : Hewlett Packard HP vs15c - 15 inchs

  > Network Card : Intel Corporation 82562EZ PRO/100 Ethernet Controller

  > Operating System : Microsoft Windows XP Home Edition 5.01.2600 Service Pack 2

  > DirectX : Version 9.0c

if anyone can help plz lmk. thanks.

---

### Post by locohygynx on 2006-09-24
any1 plz..........

---

### Post by asearle on 2006-09-24
I had a 'black screen' problem with my ASUS laptop with an ATI Mobility Radeon X700 graphic card.  The system was booting up fine but the screen was black.

I got a suggestion (from this forum, I think) whereby I could specify the screen format.  At the boot prompt (safe mode), I entered:

sax2 -m 0=vesa -V 0:1024x768@60

Then I using that resolution, I could activate the ATI graphics driver and got the full screen resolution (including wide screen support).

Anyway, give it a try :-)

All the best,
Alan.

---

