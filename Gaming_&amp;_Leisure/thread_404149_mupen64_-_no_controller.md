---
title: "mupen64 - no controller"
date: 2007-04-08
forum: Gaming &amp; Leisure
---

### Post by chocomoojuice on 2007-04-08
So, I've decided to try running an n64 emulator after having relative success with an snes one.  The roms start with mupen64, the only issue is that every game I try claims that no controller was detected.  In the input settings of the controller, it would appear that all is fine (I am using blight's SDL input plugin 0.0.10).  It detects the buttons I press and the specific device I am using: the EMS Production Limited Joypad to USB converter.  The commercial name of the joypad is the trio link plus, and it allows me to plug in a GC, PS, or DC controller.  I've tried installing the joystick package with adept (I'm using Kubuntu by the way), but conditions have remained the same.  The joystick calibration tool is able to detect the joypad just fine by the way.
Any suggestion for this gamer in need :confused:

---

### Post by hikaricore on 2007-04-08
> **chocomoojuice said:**
> So, I've decided to try running an n64 emulator after having relative success with an snes one.  The roms start with mupen64, the only issue is that every game I try claims that no controller was detected.  In the input settings of the controller, it would appear that all is fine (I am using blight's SDL input plugin 0.0.10).  It detects the buttons I press and the specific device I am using: the EMS Production Limited Joypad to USB converter.  The commercial name of the joypad is the trio link plus, and it allows me to plug in a GC, PS, or DC controller.  I've tried installing the joystick package with adept (I'm using Kubuntu by the way), but conditions have remained the same.  The joystick calibration tool is able to detect the joypad just fine by the way.
Any suggestion for this gamer in need :confused:

Under blight's SDL input plugin check that the box I've circled in the attached image is clicked.

---

### Post by zerothis on 2007-04-12
> **chocomoojuice said:**
> So, I've decided to try running an n64 emulator after having relative success with an snes one.  The roms start with mupen64, the only issue is that every game I try claims that no controller was detected.  In the input settings of the controller, it would appear that all is fine (I am using blight's SDL input plugin 0.0.10).  It detects the buttons I press and the specific device I am using: the EMS Production Limited Joypad to USB converter.  The commercial name of the joypad is the trio link plus, and it allows me to plug in a GC, PS, or DC controller.  I've tried installing the joystick package with adept (I'm using Kubuntu by the way), but conditions have remained the same.  The joystick calibration tool is able to detect the joypad just fine by the way.
Any suggestion for this gamer in need :confused:

i don't know what is wrong but this might help:

some applications look for "/dev/js0" but ubuntu puts the game controller at "/dev/input/js0". To solve many problems you can link these by typing this in a terminal:

```
sudo ln -s /dev/input/js0 /dev/js0
```

if this doesn't fix mupen64 it will fix others.

"sudo" means do as root
"ln" makes a link, -s makes it symbolic

---

### Post by chocomoojuice on 2007-04-12
> Under blight's SDL input plugin check that the box I've circled in the attached image is clicked.
Sorry for the late response, but your suggestion worked perfectly; all is well in the world of emulation.  I figured the dark colour meant it was on *doh*.  Ah well, better it be a dumb mistake on my part than a difficult issue to fix.  Thanks man.

---

### Post by hikaricore on 2007-04-12
> **chocomoojuice said:**
> Sorry for the late response, but your suggestion worked perfectly; all is well in the world of emulation.  I figured the dark colour meant it was on *doh*.  Ah well, better it be a dumb mistake on my part than a difficult issue to fix.  Thanks man.

Just glad to help.  You're not alone tho, I fought with mupen for about an hour one day
on this same issue trying to figure out what I could have possibly overlooked.  >.<

---

### Post by lakersforce on 2007-04-12
I have made the same mistake once. It is simply because of a badly designed GUI. But that is pretty much the worst thing about Mupen.

---

### Post by Nexus Delta on 2008-04-14
Sorry if this is in the wrong spot, but I am having a similar problem. 
I have the same setup but I am using a sony Playstation 2 controller with a PS2 to usb converter. My problem is that I can map any button exept for the joysticks. In other words all the buttons work except for the joysticks. I _can_ calibrate the joysticks with the Ubuntu joystick calibration. Any suggestions?

---

### Post by zero777zero on 2008-06-22
> **Nexus Delta said:**
> Sorry if this is in the wrong spot, but I am having a similar problem. 
I have the same setup but I am using a sony Playstation 2 controller with a PS2 to usb converter. My problem is that I can map any button exept for the joysticks. In other words all the buttons work except for the joysticks. I _can_ calibrate the joysticks with the Ubuntu joystick calibration. Any suggestions?

i'm using a gamepad that has the same layout as a ps2 controller (usb, no converter) and i cant map the joysticks properly either.

---

### Post by acoustibop on 2008-06-22
Are either of you using jscalibrator?  This application has a nasty habit of disabling controller controls - most often the directional ones - while still reporting them as working.

If you are using jscalibrator, uninstall it and make sure you remove the configuration as well.

I really don't know why such a problematic application stays in the repositories... :(

---

### Post by zero777zero on 2008-06-22
no, synaptic shows that jscalibur isnt installed

---

### Post by acoustibop on 2008-06-23
If you're searching for "jscalibur," zero777zero, you won't find anything; it's "jscalibrator." ;)

---

### Post by zero777zero on 2008-06-23
lol i meant jscalibrator

synaptic shows the package available for installation, it is not installed.

---

### Post by zero777zero on 2008-06-24
i just noticed that the play station emulator is mapping the buttons on one joystick to the 4 action buttons, i think mupen did the same, didnt have this problem on windows so it can be a hardware issue.

---

