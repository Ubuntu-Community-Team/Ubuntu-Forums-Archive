---
title: "pcsx-df plugins (Playstation Emulator)"
date: 2009-05-14
forum: Gaming &amp; Leisure
---

### Post by TheIdiotThatIsMe on 2009-05-14
Hi, I just recently installed PCSX from Add/Remove (the pcsx-df fork), and am happy that it seems to work well, excpet for one small slight problem. I use an Xbox 360 wired controller for my games, and I am unable to figure out how to map the controller plugin to the Controller, and haven't been able to find any alternative plug-ins for controllers.

I also tried alternate emulators, but both pSX and ePSXe crash on startup for me :-(

Does anyone know where I can find another plugin or how to map the controller for PCSX?

---

### Post by TheIdiotThatIsMe on 2009-05-15
Does anyone have any working PS emulator on 9.04? :-(

---

### Post by slave-zeo on 2009-05-16
I'll install PSX, ePSXe and pcsx-df on 9.04 tonight and see what I can come up with. ):P

Check back tomorrow and I should have something to report.

Just so I know what you are working with, what kind of computer are you using? You know, stuff like CPU, RAM, video card. Also, is it 64-bit or 32-bit.

---

### Post by zero777zero on 2009-05-16
> **TheIdiotThatIsMe said:**
> Does anyone have any working PS emulator on 9.04? :-(

pcsx is working fine for me, no 360 controller here tho. i assume you have bios...

---

### Post by TheIdiotThatIsMe on 2009-05-16
> **slave-zeo said:**
> I'll install PSX, ePSXe and pcsx-df on 9.04 tonight and see what I can come up with. ):P

Check back tomorrow and I should have something to report.

Just so I know what you are working with, what kind of computer are you using? You know, stuff like CPU, RAM, video card. Also, is it 64-bit or 32-bit.

Definitely would love that! I've tried both pSX and ePSXe and both crash on startup. 

I'm running an older machine (although it's always proved good for PS Emulation on 8.04 and 8.10), an Athlon XP 2200+, 1GB RAM, NVidia GeForce 5900XT, and 32-bit OS and software.

[QUOTE=zero777zero]pcsx is working fine for me, no 360 controller here tho. i assume you have bios... [/QUOTE]

I do have BIOS, :-) And actually PCSX *does* work, but for the life of me I can't figure out how to use the controller plugin included with it. I open it and don't understand it at all, and cant figure out how to get it to use my 360 pad. I know it sees it, I have it set to the right device (/dev/input/js0), and the light on the controller is solid, just can't figure out how to set the buttons on it.

---

### Post by zero777zero on 2009-05-16
u got this far? i assume

[IMG]http://img30.imageshack.us/img30/2936/screenshotf.png[/IMG]

just a matter of clicking on the PlayStation buttons (my cursor is over L2 on that screenshot) and pressing the button you want to map it to. did u try that? is it working?

---

### Post by TheIdiotThatIsMe on 2009-05-16
If I click on one of those in the screenshot, it changes it to like A0+ or something like that. When I click on it, it doesn't seem to ask for me to press a button to map it to.

---

### Post by zero777zero on 2009-05-16
actually the button should just depress, it wont ask you how you want to map it (i'm thinking of another emu).

it sounds like one of your analog sticks may be off center or stuck and it is reading that

---

### Post by TheIdiotThatIsMe on 2009-05-16
I got it to work. It was something with my 360 pad that it wasn't taking, I just stuck in another gamepad. Just one last question, the two pyramid looking selection of buttons near the buttom, are those for the analog sticks?

---

### Post by zero777zero on 2009-05-16
circled are left and right analog sticks

[IMG]http://img2.imageshack.us/img2/6261/screenshot1a.png[/IMG]

when you configure your analog sticks you are only configuring X and Y axises not up,down,left,right. I'm pretty sure the "|" buttons are L3 and R3

---

### Post by TheIdiotThatIsMe on 2009-05-16
Thanks, I tried that, and it wouldn't read an up and down on them, if I set the X axis it would clear the Y axis? Other than that, it picked up all my buttons. Except when I start the game, the buttons don't do anything?

---

### Post by zero777zero on 2009-05-17
it can be very sensitive. when setting the X axis you only have to press left OR right. y axis you only need to press up OR down i think.

you should try multiple games/roms and see if they pick up. make sure your start button is set correctly lol

---

### Post by TheIdiotThatIsMe on 2009-05-17
Hi, unfortunately I can get it mapped but it's not working across any of the games I have. Hopefully I can still figure something out with pSX or ePSXe

---

### Post by BoyOfDestiny on 2009-05-17
Try pressing F5, from the old readme
F5: Sio Irq Dis/Enable
Should work.

Too bad the newest version isn't packaged for Ubuntu.

If someone needs help with compiling, maybe even help me make/test a script to automate that, post here.

[http://pcsx-df.sourceforge.net/](http://pcsx-df.sourceforge.net/)

---

