---
title: "Game Controllers (Dualshock 3, 360 Controller) Interfering with Mouse Input"
date: 2010-05-20
forum: Gaming &amp; Leisure
---

### Post by xondak on 2010-05-20
So after I upgraded to Lucid, I connected my Dualshock 3 controller via bluetooth (with QtSixA)... come to find out that after the update the SixAxis input from the controller was actually controlling  the cursor. When I use the R2 and L2 buttons or the right stick, it causes the cursor to revert to the upper left side of the screen and when I use the mouse, it will revert back to the left side of the screen when I stop moving the mouse itself.

So I though this was a problem with QtSixA but then I used my brothers wired Xbox 360 Controller and the same thing happened. This time, the right stick controls the X axis of the cursor and the right trigger controls the Y axis of the cursor... and when I use the actual mouse, it reverts back to the upper left corner of the screen. (And another weird thing happens when I use the 360 controller: if Banshee is open, it'll start the music playing when I plug it in--then if I use the mouse on it's Y axis, the track will randomly change!)

I had given up on using a gamepad for a while because of this problem and forgotten about it until today when I wanted to use my emulator.

The fix is probably simple but I'm a relative beginner at Ubuntu--so thanks for the help.

---

### Post by xondak on 2010-05-23
Hate to bump my own thread... but seriously. Nothing? :(

---

### Post by benmoran on 2010-06-09
I had this same problem. Try removing xserver-xorg-input-joystick using the Software Center or Synaptic.

---

### Post by CG81 on 2010-06-09
I also had this problem using a Dualshock2 connected through a usb adapter. The controller would simultaneously control the game whilst moving the mouse pointer around the desktop etc.

As benmoran says, the solution is to remove xserver-xorg-input-joystick.

---

### Post by BadGoomba on 2011-10-03
I have this same problem, I am using a 4port psx usb adapter, I know ubuntu is detecting my ps2 controller because if I use the dpad it moves the mouse cursor around the screen, I tried configuring it in atari and snes emulators but they will not detect any movements/buttons and I think this is the reason why. I am running on ubuntu 11.04, I tried removing xserver-xorg-input-joystick from synaptic but it just has options to install it from there so I assume I don't have that installed to begin with, maybe it's called something different in the new version of ubuntu? 
Any help with this would be greatly appreciated.

---

### Post by mark_vinton on 2012-01-31
I'm having the same problem with my new xbox 360 for windows wireless controller. I am running a Dualshock 3 w/ sixpair no problem, but I can't make the 360 controller work with either the default drivers or xboxdrv.  It just takes over my mouse and renders the system unusable until I unplug the wireless hub.  I can't calibrate with jstest/jscal.  It will re-map the axis' fine but that's about it.

Anyone have any ideas?

---

### Post by DaneFletcher on 2012-02-01
Thanks for the help, I've been wondering about this too with my Dualshock.

---

