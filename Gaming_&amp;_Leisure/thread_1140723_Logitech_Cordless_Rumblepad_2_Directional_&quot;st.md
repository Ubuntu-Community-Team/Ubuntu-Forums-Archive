---
title: "Logitech Cordless Rumblepad 2: Directional &quot;sticks&quot; after use"
date: 2009-04-27
forum: Gaming &amp; Leisure
---

### Post by GGG121 on 2009-04-27
Hello all,

I've run into a bit of a problem using epsxe 1.6.0 (a playstation emulator) with my gamepad.

The gamepad is a Logitech Cordless Rumblepad 2. I'm using the Omnijoy Beta 1 1.0 plug-in. I'm running Mythbuntu 8.10 (...so basically Intrepid). The problem is that once I use the down or left directional, it gets stuck. I can use the up and right directionals without problem. The rest of the buttons work just fine.

I've calibrated the gamepad using jscal. Output from ```
jstest --event /dev/input/js0
``` shows the following (sans the timestamp) (for directionals left, right, up, down respectively):

Event: type 2, number 4, value -32767
Event: type 2, number 4, value 32767
Event: type 2, number 5, value -32767
Event: type 2, number 5, value 32767

with the neutral values of 0 for each.

I ran into this problem before using a gameboy emulator (...sorry, can't remember which one), and I wasn't able to solve it.

Has anyone else had this problem? If someone has this specific gamepad working properly, would you please post your configuration file? I'm truly stumped, and since this is an HTPC build, it would be really nice to get a gamepad working for it!

Thank you in advance!

---

### Post by CharmyBee on 2009-04-27
Ditto. Try tecnoballz, watch the menu cursor go up continually without touching the gamepad until you go up or down on the pad. Some weird polling going on that this gamepad (or its driver) doesn't agree with.

---

### Post by malachi on 2009-04-29
I have the same problem. Trying to play Chrono Trigger with ZSNES and the movement is all wacky. It's driving me crazy. I also had problems configuring my joypad in ePSXe. What's the deal?

Oh, and if I run ZSNES or ePSXe through Wine, everything is fine.

---

### Post by GGG121 on 2009-05-01
I tried other emulators (ZSNES, FCEU, and Mednafen (spelling?)) and the directional pad works fine. Does anybody know of another gamepad plug-in for epsxe?

---

### Post by CharmyBee on 2009-05-01
Strangely enough upgrading to Jaunty fixed my gamepad problems that i've mentioned. I don't know if it'll fix your issue though. LiveCD boot a Jaunty and see if it occurs there if you can.

---

### Post by wiebeest on 2009-05-17
> **malachi said:**
> Oh, and if I run ZSNES or ePSXe through Wine, everything is fine.

Unfortunately in my case running ePSXe through **WINE** gives me headaches. I'm using the Logitech Rumblepad 2 (USB, wired). 

With Gutsy, Hardy and Intreped it used to work perfectly. Now on Jaunty it fails me. What goes?

If I use Jscalibrator to calibrate my gamepad, al seems to work flawlessly fine.

But under **WINE** it refuses to accept my settings config-->gamepad (configcontroller). 

**Terminal output:**
```
* Running ePSXe emulator version 1.7.0. 
fixme:dinput:linuxinput_create_effect Unknown force type 0x0.
fixme:dinput:LinuxInputEffectImpl_Download Could not upload effect. Assuming a disconnected device -1 "invalid file descriptor".
 * Direct input init ok. 
fixme:dinput:joy_polldev joystick cannot handle type 21 event (code 96)
 * Memory handlers init. 
 * ePSXe: PSX BIOS loaded [bios\SCPH1001.BIN]. 
 * Loading ISO Format [MDF/BIN/IMG2352] (+subchannel) ok
 * First/Last track: 1 1
 * Track 1: (DATA)  - Start 1: (00,02,00) -  Length 64:59
 * NTSC cdrom detected. (SLUS_004.02) 
 * Doing init gpu[0]... 
 * Gpu open[0]... 
fixme:dinput:linuxinput_create_effect Unknown force type 0x0.
fixme:dinput:LinuxInputEffectImpl_Download Could not upload effect. Assuming a disconnected device -1 "invalid file descriptor".
 * Direct input init ok. 
fixme:dinput:joy_polldev joystick cannot handle type 21 event (code 96)
 * Doing spu init... 
 * Spu open... 
fixme:dinput:joy_polldev joystick cannot handle type 4 event (code 4)
 * LoadState Done! 
fixme:dinput:joy_polldev joystick cannot handle type 4 event (code 4)
 * Closing spu ... 
 * Shutdown gpu ...
 * Closing ISO system. 
 * Going out from gui. (exit)

```What goes?

---

### Post by wiebeest on 2009-05-19
**Bump**

Doesn't anyone know a sollution? 

My Logitech Rumblepad 2 USB used to work perfectly under **WINE** playing ePSXe in previous versions of Ubuntu. Now it fails me under Jaunty. What gives?

**_My lsusb output:_**

```
wiebeest@wiebeest-desktop:~$ lsusb
Bus 001 Device 007: ID 046d:c218 Logitech, Inc. Logitech RumblePad 2 USB
Bus 001 Device 006: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 004: ID 1532:0200 Razer USA, Ltd 
Bus 002 Device 003: ID 046d:c049 Logitech, Inc. G5 Laser Mouse
Bus 002 Device 002: ID 1532:0103 Razer USA, Ltd 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```[B][U]
And Jscal states:[/U][/B]

```
wiebeest@wiebeest-desktop:~$ jscal /dev/input/js0
Joystick has 6 axes and 12 buttons.
Correction for axis 0 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 1 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 2 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 3 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 4 is broken line, precision is 0.
Coeficients are: 0, 0, 536870912, 536870912
Correction for axis 5 is broken line, precision is 0.
Coeficients are: 0, 0, 536870912, 536870912
```What am I overlooking? 
Or is this a known **Jaunty**/ **WINE** (using version 1.1.21) related bug?

Jyaan' s sollution ([http://newyork.ubuntuforums.org/showthread.php?t=1097169&highlight=logitech+rumblepad )]("http://newyork.ubuntuforums.org/showthread.php?t=1097169&highlight=logitech+rumblepad")
Didn't help me much.

Help me Obi-some one, you're my only hope...;)

---

### Post by wiebeest on 2009-05-27
Well stupid me. **](*,)**

The sollution was to install [B]xserver-xorg-input-joystick
from synaptic.
[B]
Moderators: my problem is fixed now.[/B] :D
[/B]

---

### Post by clicker4721 on 2010-03-19
> **wiebeest said:**
> Well stupid me. **](*,)**

The sollution was to install [B]xserver-xorg-input-joystick
from synaptic.
[B]
Moderators: my problem is fixed now.[/B] :D
[/B]

So, once that package is installed, what do you do? It didn't work any special magic for me...

---

### Post by dieklaue on 2010-09-12
> **clicker4721 said:**
> So, once that package is installed, what do you do? It didn't work any special magic for me...

I have the same problem (with a different gamepad, a Saitek Cyborg rumble, but that probably makes no difference?) in ePSXe, installing the named package doesn't make any difference here, either.

---

### Post by dfreer on 2010-09-12
jscalibrator is known to cause issues with joysticks. I've been preaching about the evils of jscalibrator for years and yet it seems to continously pop up. I need to put it in my signature along with the links to fix it, which I'm to lazy to go search for right now.

Suffice it to say, most controllers work perfectly fine **out of the box**, except in the rare case where the controller doesn't use a standard USB HID driver but that's different, you just need to install the correct driver. Most cases the controller will NOT need to be calibrated. jscalibrator is installed for whatever reason, and although it reports everything as working fine, it will generally cause issues with the joysticks/dpads. Buttons generally continue to work fine.

Some people have reported that jscalibrator works fine in KDE based distros, but irregardless you generally don't need to use it in the first place. Uninstalling it also doesn't fix the problem competely, I believe the complete fix involves uninstalling and removing a .joystick file in the home directory, like I said I'm too lazy right now to find the link.

EDIT: nevermind quick google search found the link:
[http://board.zsnes.com/phpBB3/viewtopic.php?f=22&t=12253](http://board.zsnes.com/phpBB3/viewtopic.php?f=22&t=12253)

---

