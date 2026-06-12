---
title: "logitech controller....how to get it to work?"
date: 2011-01-26
forum: Gaming &amp; Leisure
---

### Post by skyzthelimit230 on 2011-01-26
Hi,
I'm running 10.10 and want to play games on Ubuntu using my logitech GamePad F310.

Where can I find drivers for it? Thanks :)

I know this is a total noob question, but well....yeah I just started using Ubuntu.

---

### Post by acornty on 2011-01-27
If you automatically don't receive a little pop up saying that there are drivers for the device, then it most likely isn't supported by ubuntu. most logitech products usually aren't supported.

---

### Post by cchhrriiss121212 on 2011-01-27
You won't need to install any drivers, compatibility for control pads is built in to the OS. I have a Logitech controller, I just need to plug it in and it works. Check lsusb from a terminal to see if the pad is listed, if not then I would say it is not supported.

It also depends on what games you are using, support needs to be built into the game for the pad to work. AFAIK games that are designed for keyboard and mouse cannot be forced to use a pad instead.

---

### Post by travissparks1307 on 2011-03-14
You shouldn't need any drivers for it. I recently purchased this same gamepad and it worked as soon as I plugged it in. There was no pop-up or anything. I got it for my emulators, (Mupen64plus, ZSNES, Gens) and it just worked.  Flawlessly, I might add. It's easily the best gamepad I've ever used. Very responsive, very precise. I'm running 10.10 Maverick Meerkat 64-bit. 

You may have it in the wrong mode. On mine, I have the bottom switch on X not D. Also there is a mode button on the face with a light. Mine is not lit. I have had no problems. I hope you get it working, it's a great gamepad.

Also, be aware that this pad identifies as a "Generic X-Box pad" at least according to Mupen64plus.

---

### Post by magnetic651 on 2011-03-30
I have the same gamepad (F310) and it doesn't "just work."  The pads I have are new and work on other systems but not on Ubuntu.  I plugged them in and rebooted the computer but they do not work.  Can anyone help?

---

### Post by magnetic651 on 2011-03-30
I ran lsusb and the devices are listed:

Bus 003 Device 008: ID 046d:c21d Logitech, Inc. 
Bus 003 Device 007: ID 046d:c21d Logitech, Inc.

---

### Post by cchhrriiss121212 on 2011-03-30
What game or software are you using? Does it definitely support gamepad control?

---

### Post by magnetic651 on 2011-03-30
> **cchhrriiss121212 said:**
> What game or software are you using? Does it definitely support gamepad control?


I have tried SNES9X, Fusion 3.63x, FCEUX 2.1.4a, Stella 3.1.2 ...

---

### Post by dailyfare on 2011-04-15
[skyzthelimit230]("http://ubuntuforums.org/member.php?u=1168232") i have the exact same game pad, and i run the latest xubuntu. I'm a total noob at ubuntu and am having the same issue except when i run lsusb in a terminal it doesnt even detect the game pad at all, just my mouse and keyboard. I've been through many different forums over the last few days and can't seem to find an answer. If you figure it out could you lemme know? thanks...and if i can figure out mine ill post the answer here or message you. best of luck! 

"and all i wanted do is play some supermario world":D

---

### Post by skyzthelimit230 on 2011-05-04
Hello everyone
I've been trying to use it with Secret Maryo Chronicles and some emulators. It's just not detected by my Ubuntu partition, but works flawlessly on Windows.

Le sign. Not sure what else to do...

---

### Post by giacomo.c on 2011-05-04
i find it hard to believe it "just isn't supported."  did you try using google?  if you are looking for an answer odds are someone has already answered it, or is asking the same question.  check out this link and see if it helps at all (first google result):

[http://www.ubuntugeek.com/how-to-set-up-a-gameportgamepad-or-joystick-in-ubuntu.html](http://www.ubuntugeek.com/how-to-set-up-a-gameportgamepad-or-joystick-in-ubuntu.html)

---

### Post by rmose on 2011-10-16
> **travissparks1307 said:**
> You shouldn't need any drivers for it. I recently purchased this same gamepad and it worked as soon as I plugged it in. There was no pop-up or anything. I got it for my emulators, (Mupen64plus, ZSNES, Gens) and it just worked.  Flawlessly, I might add. It's easily the best gamepad I've ever used. Very responsive, very precise. I'm running 10.10 Maverick Meerkat 64-bit. 

You may have it in the wrong mode. On mine, I have the bottom switch on X not D. Also there is a mode button on the face with a light. Mine is not lit. I have had no problems. I hope you get it working, it's a great gamepad.

Also, be aware that this pad identifies as a "Generic X-Box pad" at least according to Mupen64plus.

THANKS A LOT!! I had forgotten all about the small button on the back side of the gamepad (Logitech F310). Now everything works in Ubuntu 10.10 just by plugging the usb-cable in :o)

---

### Post by Gerbil King on 2011-10-29
I have a Gigaware USB Controller (Radioshack brand), and that works perfectly, but I can't get my new Logitech F310 USB gamepad to work.

I'm using Ubuntu 8.04 (32 bit). I have jscalibrator and jscal/jstest.

When I set my Logitech controller to "X" (Xinput), pushing the mode button will make the green light come on, but when setting it to "D" (DirectInput) the light turns off and will not come on when pressed. Is this normal, or some sort of hardware failure?

When I set my controller to "X" it does not show up in dev/input and jscalibrator says it could not access the specified paths, but if I unplug it, set it to "D", and plug it back in it will show up as dev/input/js0. Then, when I run jscalibrator or jscal or jstest the controller will show up, but it will not recognize input - everything stays at zero no matter what button(s) I press.  

In the terminal, lsusb gives:

Bus 001 Device 010: ID 046d:c216 Logitech, Inc. Dual Action Gamepad
Bus 001 Device 002: ID 046d:0a0c Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  

Is this a hardware or software problem? I don't have any other systems to test the controller on. If software, any ideas how to fix this? Thanks.

---

### Post by jawrat on 2012-05-08
> **travissparks1307 said:**
> 
You may have it in the wrong mode. On mine, I have the bottom switch on X not D. 

*This* solved my problem after googling for a half hour.  Thanks for the tip and here's to anyone else trying to get their Logitech Dual Action F310 working with ubuntu!  :)

---

### Post by illunatic on 2012-11-08
Logitech F310 here and it works for me as well. (Sorry for the bump, but it's been a while since I used this gamepad and I forgot why it wasn't working at first until I landed here).

It is confirmed that the switch on the back must be set to X. Try unplugging and plugging it back in after you switch to X.

Also, it is recommended to install jstest-gtk to calibrate it. This tool has seriously enhanced performance of this gamepad.

sudo apt-get install jstest-gtk

---

### Post by Famicommander on 2012-11-09
I have the F510, which is just a 310 with built in rumble, and it works fine. You have to make sure that the switch on the bottom is set for Xinput rather than Directinput. 

I highly recommend QJoyPad for setting it up with different games and programs.
[http://qjoypad.sourceforge.net/](http://qjoypad.sourceforge.net/)

You can use it for games that don't have explicit gamepad support by mapping keystrokes and mouse actions to the buttons and sticks, and you can save different profiles for different games.

---

### Post by mbiebel872 on 2012-12-21
> **travissparks1307 said:**
> You shouldn't need any drivers for it. I recently purchased this same gamepad and it worked as soon as I plugged it in. There was no pop-up or anything. I got it for my emulators, (Mupen64plus, ZSNES, Gens) and it just worked.  Flawlessly, I might add. It's easily the best gamepad I've ever used. Very responsive, very precise. I'm running 10.10 Maverick Meerkat 64-bit. 

You may have it in the wrong mode. On mine, I have the bottom switch on X not D. Also there is a mode button on the face with a light. Mine is not lit. I have had no problems. I hope you get it working, it's a great gamepad.

Also, be aware that this pad identifies as a "Generic X-Box pad" at least according to Mupen64plus.

You are my hero. I have been pulling my hair out trying to get Ubuntu 12.10 to recognize this controller.

Turns out all I needed was to flick that little switch on the back, that I didn't even know existed, to X and there it is on lsusb.

I'm just trying to set up an old laptop with lubuntu and zsnes for my 11 year old cousin, and the whole process has been riddled with issues all the way.

This is what works for me off a fresh install of lubuntu.

1. sudo apt-get install joystick
 1a. (I also had packages linux-firmware-nonfree and zsnes at this point)

2. make sure that the switch on the back of the controller is switched to X input mode.

3. Plug and Play

Seriously, you saved me.

P.S. If you don't already know, the mode button on the front with the light swaps the left d-pad and analog stick. Using mode, you can set one set of controls in zsnes. By pressing mode, you can switch between analog and d-pad without altering input settings.

---

### Post by CrystalDreamer59 on 2013-01-28
Hi I'm I just bought this controller and I'm trying to use it in Ubuntu 12.10 for PCSX2 but when I set configure my buttons I can't use both the d pad and the analogue sticks at the same time. the pad plugin for PCSX2 detects it as a generic xbox controller.

---

### Post by NotumFeind on 2013-05-23
BUMP
finally found out what was wrong. Had to modprobe for a logitech gamepad as it wasnt being read lsusb. 

Logitech ADI digital joysticks and gamepads

 
in terminal run
"sudo modprobe adi"

flip the switch on the bottom to "x"

enjoy

---

### Post by Horbo on 2013-05-26
> **Famicommander said:**
> I have the F510, which is just a 310 with built in rumble, and it works fine. You have to make sure that the switch on the bottom is set for Xinput rather than Directinput. 

I highly recommend QJoyPad for setting it up with different games and programs.
[http://qjoypad.sourceforge.net/](http://qjoypad.sourceforge.net/)

You can use it for games that don't have explicit gamepad support by mapping keystrokes and mouse actions to the buttons and sticks, and you can save different profiles for different games.

Does this work for logitech mice? (Or is there something similar for mice?)  My MX518 works fine, except that the two buttons that are officially for increasing/decreasing dps on the fly can't be remapped in Linux like they can in Windows, which is quite annoying....

---

