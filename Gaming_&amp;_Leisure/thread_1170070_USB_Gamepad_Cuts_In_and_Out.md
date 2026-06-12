---
title: "USB Gamepad Cuts In and Out"
date: 2009-05-25
forum: Gaming &amp; Leisure
---

### Post by svtguy88 on 2009-05-25
I have a Gravis Eliminator Aftershock (two actually) that I want to configure for my friends Ubuntu home theater rig.  Everything seemed to be golden when I first tried using them...

Plugged them both in, they both lit up, and were immediately recognized by GFCE.  However, after configuring the buttons within GFCE and launching an NES ROM, it's as if the computer forgets the controller is connected after a few seconds/minutes (time seems random).  After it's 'forgotten about,' I have to unplug it and plug it back in, and then relaunch the emulator.  Any ideas?

I've configured using jscalibrator, and the disconnect/reconnect seems to happen there too.  So, any ideas why both USB pads are coming and going?  

-btw- both work fine under windows, so i know the pads are good.

---

### Post by hikaricore on 2009-05-25
You might wanna take a look at the output of:

> dmesg

Should give you an idea of what's happening if you run it after they cut out on you.
Could be flakey usb ports even if ***dows doesn't notice it doesn't mean it's not the case.

---

### Post by svtguy88 on 2009-05-26
As soon as I get back to that computer, I'll check that out.  I KNOW the USB ports are flakey.  Two don't work at all, and the other two on the back seem to be on the "ehhh" side.  The ones on the front of the tower don't function at all, as the wires got pulled off of the mobo.  

Now, if anyone can find me a diagram as to where each of the USB leads goes back to on the mobo, I'd love it.  I see the pins that the wires go to, but they aren't labeled (on the board), and each wire is a different color....

---

### Post by rob2uk on 2009-05-26
> **pkmgarf said:**
> Now, if anyone can find me a diagram as to where each of the USB leads goes back to on the mobo, I'd love it.  I see the pins that the wires go to, but they aren't labeled (on the board), and each wire is a different color....

All you need to know is where the +5v pin is - if you can get hold of a multimeter then you're shiny.

The +5v will be either the first or fourth pin, the opposite end will be the ground, the two pins between will be the data pins.

If you get the middle pins round the wrong way the USB won't work, but it won't cause any damage either

---

### Post by svtguy88 on 2009-05-26
A multimeter I do have.  Sweet...didn't know that.  I'll try hooking them up and if it doesn't work, I'll just reverse the data pins.  It will be nice to have front USB back....especially when this thing is a media center, and accessing the back of it is, well, less than desired.

---

### Post by svtguy88 on 2009-06-08
Well, I finally had some spare time to work on this machine, and I've still got problems with both gamepads I've been trying to configure.

I have the front USB ports working again, but I get similar results as to what I got before.  I think all of the USB ports are just terrible, as the connection seems to be heavily related to just how carefully the USB plug is positioned.

However, even when it is attached, ZSNES doesn't even recognize the analog sticks, and will *sometimes* let me use the dpad.  Is this all going to boil down to a sub-par USB connection (which I know I already have), or is it deeper than that (jscalibrator seems to register the pads and sees the analog sticks, dpad and buttons all working).

---

### Post by rob2uk on 2009-06-09
ok, to clarify:

The USB ports ALL seem flaky, but jscalibrator has no problems?

Seems like a software issue, to be honest...

---

### Post by svtguy88 on 2009-06-10
^^^Sort of.

jscalibrator detects and registers all of the controllers properties, but not always.  When it works, everything is there.  The calibration seems off at first, but fine after I run the calibration tool. 

But, seemingly randomly (USB ports bad?) jscalibrator also will fail (the axis don't move and buttons don't light up when pressed).

At this point (assuming everything is good in jscal), I assume everything is fine, and run ZSNES, and setup the keymaps.  The left analog stick (when I try to program it as the dpad of a snes controller) always registers as one value (J03) in the ZSNES setup window, no matter what direction it is moved.  From here, a game (Super Mario World, for example) runs fine, and the buttons may all work for some time (not the analog stick, I have to program the dpad rather than the stick to move Mario left/right at all).  

However, at some point, something fails and the controller goes dead.  Even the "Precision" LED on the controller goes out.

This point of failure seems random, but partially related to flaky USB ports, as the wireless USB keyboard/mouse cut in and out from time to time as well (on both the front or back USBs).

Hope that clears it up?  

:confused:

---

### Post by rob2uk on 2009-06-10
I assume the front USB headers are seperate to the USB ports on the rear of the PC?

And that you have verified the controller is working by testing it on another machine?

Sorry if it seems like I'm asking dumb questions, but working in IT kinda makes you give up hope that people have any form of common sense...

---

### Post by svtguy88 on 2009-06-11
Yep...different headers.  Pads work under Windows on my laptop.  I'll try it under Ubuntu on my laptop later today.  I'm stuck in Windows right now thanks to fglrx installing...sort of...and now now failing to load on bootup.  I'll go back down to vesa and see what I can do....

---

