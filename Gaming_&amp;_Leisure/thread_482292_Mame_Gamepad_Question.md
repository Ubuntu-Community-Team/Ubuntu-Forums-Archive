---
title: "Mame Gamepad Question"
date: 2007-06-23
forum: Gaming &amp; Leisure
---

### Post by Ralleh on 2007-06-23
So I am extremely new to Ubuntu (and Linux in general) but I have gotten far enough here to where I'm using jscalibrator and it detects the Logitech Precision gamepad as what it is, I set up the calibration in dev/input/js0 with all of the directions and buttons appearing to work fine, I go to kxmame and match up dev/input/js0 for the joystick and when I load up a game all the buttons work, but I can't move in any direction. The D-pad is completely disabled. I wonder if anyone has any idea if there is something I can do to remedy this.

Thanks in advance.

---

### Post by BigSilly on 2007-06-23
I had exactly the same problem myself. I found that the only thing in kxmame I could control with a pad was the menu! I wish I could offer a solution for you, but what I did instead of using kxmame was download AdvanceMame. You have to compile it from source (which took 30 minutes on my PC :shock:) but seems to work just fine with my pad. You can get it from [here.]("http://advancemame.sourceforge.net/")

It's a tricky beast for sure, and like you I'm fairly new to Linux, so compiling it was pretty daunting. But I've actually had some success with this program, and I intend to get better acquainted with it when I can spare the time. It seems to be made for serious mame hobbyists who like to build cabinets etc, but it's also OK for desktop use. Let me know if you give it a go.

As a side note, I was told on another forum that the reason our gamepads don't work so well with certain apps in Ubuntu is because of how Gnome handles their drivers. He reckoned that if I'd used the KDE based Kubuntu that it'd work better with such programs, but I've not tried it yet, and I don't have the requisite Linux knowledge to be able to tell if he's right. Maybe someone here can confirm or correct this....?

---

### Post by rende on 2007-08-12
I am also having this exact problem on fiesty 7.04.  I have a saitek p990 usb gamepad, it has a d-pad and 2 analog sticks.  When I plug it into the usb port, it is recognized, and xpad driver is loaded. 

 jscalibrator works fine, and detects d-pad movement and both analog sticks appropriately, only when trying to use kxmame I can get nothing but the buttons to work.

I will try using advanceMame, but I would like to know why this might be a such a problem, as I am having difficulties getting other emus and things to work with the gamepad as well.

---

### Post by MonkeyBoy on 2007-08-12
Just to add my experience I have had a Logitech Playstation2 type pad for ages and it has never consistently worked but then I bought a really cheap generic snes type pad with only a digital pad and it works just fine for everything.  Of course it has no analogue axis but for kmame and zsnes this isn't a problem.

---

### Post by BigSilly on 2007-08-12
I can confirm that the cheap generic digital pads do indeed work just fine, so it's worth picking one up for a small amount. 

My dual analogue pad is absolutely fine with everything else though, with only Gridwars proving contrary. Even the buttons don't work with that. But I have ZSNES, VBA, FakeNES, Mupen64, Gens, and also loads of stuff like TORCS, WOP and PPRacer that all work just fine.

I've said it before, but the MAME scene really needs some lovin' on Linux! KXMame is quite old now, and well overdue an update anyway. Hopefully someone out there is taking note and sorting it out.

---

### Post by acoustibop on 2007-08-12
The problem is likely to be jscalibrator, Ralleh - I've had the same problem with it (using different emulators), in that it seems to stop the directional controls working.  Once you uninstall it, you will hopefully find your problem fixed.

---

### Post by Exheon on 2009-10-09
Acoustibop, I just follow your advices and remove (purge) jscalibrator... and IT WORKS!.
Im very happy now, for jscalibrator was not needed for any game I'd installed

ThanX:guitar:

Adding myself to MonkeyBoy and BigSilly experience, my only working PSX-style gamepad is a very cheap one

---

