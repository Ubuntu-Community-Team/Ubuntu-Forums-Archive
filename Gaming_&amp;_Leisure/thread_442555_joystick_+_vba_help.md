---
title: "joystick + vba help"
date: 2007-05-13
forum: Gaming &amp; Leisure
---

### Post by jimp180 on 2007-05-13
I must be missing something in my setup but i can't figure out what. I can't seem to get my joystick..actully its a logitec dual action joypad, to work with any of the emulators I have loaded. for right now i am concentrating on VisualBoyAdvance because once i get that going the rest should work too. I am running feisty from the alternative install for amd 64 cd . I can see my joystick and all buttons and axis work in jscalibrator. I tried to edit the visualboyadvance.cfg file with what i thought was the right codes for the buttons on my joystick but this didnt work. so I thought maybe I don't have the right codes- no problem I'LL just install vbaexpress and set it up that way but it doesnt see the joystick either. Somethings missing between the joystick and the emulator but what? SDL? if so what part? and why wouldn't it be part of one of the packages if its needed? 
Any thoughts- Ideas?

---

### Post by BigDXLT on 2007-08-16
Bump!  

I've got the same problem, though it's a different controller.  Jscalibrate detects it fine but I can't do anything in VBA.  :(

---

### Post by BigSilly on 2007-08-16
You shouldn't be having any bother here at all. Ubuntu works fine with these pads. I suspect the issue is JSCalibrator. It's known to cause problems sometimes, so I would certainly recommend you remove that before continuing. Have you tried ZSNES too, and is that giving you the same bother?

---

### Post by Sockerdrickan on 2007-08-16
Try my emu if you only play GB/C games [www.tuxemu.se.nu](www.tuxemu.se.nu)

---

### Post by BigDXLT on 2007-08-16
> **BigSilly said:**
> Have you tried ZSNES too, and is that giving you the same bother?

I just tried it.  While I don't have any games for it, it recognized my input enough to set the buttons.  Going to fiddle around with VBA some more.

Edit:  I should add, the driver that comes up when I grep dmesg for joystick is:
[   24.223447] input: GreenAsia Inc.    USB Joystick      as /class/input/input3
[   24.223462] input: USB HID v1.10 Joystick [GreenAsia Inc.    USB Joystick     ] on usb-0000:00:1f.4-2

If that's of any use.  Mine isn't a Logitech, it's a Nexxtech (some sort of Radioshack/Source by Circuit City type el cheapo brand)

---

### Post by BigDXLT on 2007-10-28
Update:

I just reinstalled vba with the hopes that maybe my Gutsy install would let things work better.

This time I installed vbaexpress (sudo apt-get install vbaexpress)

This GUI lets me configure every button except the directional pad/joysticks.  VBAexpress interface seems to recognize when I press the direction to set the buttons, but in game, I can't move!  

ARGH!  So close!  :O

And a quick test in Znes, it seems that the d-pad don't wanna work there now either...  But jscalibrator also shows it works.  

Edit:  Today it works!  

I dunno, maybe my computer just needed to be rebooted one more time.  :p

---

