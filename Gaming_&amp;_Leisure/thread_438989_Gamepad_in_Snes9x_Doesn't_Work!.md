---
title: "Gamepad in Snes9x Doesn't Work!"
date: 2007-05-10
forum: Gaming &amp; Leisure
---

### Post by TheForkOfJustice on 2007-05-10
Using Snes9x (and it's frontend gsnes9x) in Feisty. Sound and video are PERFECT but **my gamepad (Logitech USB Gamepad) does not work.**

I used Zsnes (version 1.42 in the repos and 1.51 compiled from source) before and the gamepad worked fine but the sound was crappy and roms were sometimes buggy.  Therefore, I know my gamepad is not at fault.

Was snes9x compiled without joystick support?  How can I get it to work?

---

### Post by Frem on 2007-05-10
Imho, Zsnes has been less buggy than Snes9x. Have you tried tweaking the sound settings and/or the game-specific prefrences?

Failing that, I'd suggest grabbing the Snes9x source and take a crack at compiling it yourself. I searched around, and it appears that joypad support should be built in. It appears to be in part of the source code, anyway. Debian has been known to disable cool stuff because it didn't work perfectly, though. *shrug*

---

### Post by TheForkOfJustice on 2007-05-10
> **Frem said:**
> Imho, Zsnes has been less buggy than Snes9x. Have you tried tweaking the sound settings and/or the game-specific prefrences?

Failing that, I'd suggest grabbing the Snes9x source and take a crack at compiling it yourself. I searched around, and it appears that joypad support should be built in. It appears to be in part of the source code, anyway. Debian has been known to disable cool stuff because it didn't work perfectly, though. *shrug*

Trust me I tweaked Zsnes like the devil and got nowhere.

I'll refrain from building it from source until I get more input.

---

### Post by po0f on 2007-05-11
TheForkOfJustice,

To fix the sound issue in zsnes:

```
$ sudo apt-get install libsdl1.2debian-oss
```

---

### Post by retrovision.tv on 2007-05-17
This is a bug in the latest snes9x.  Get an earlier version.  I am using 1.4.3 and it works fine.

---

### Post by BobCFC on 2007-11-30
Just trying snes9x for the first time on Linux.

I got my Saitek P220 usb joypad working by passing an argument on the command line

```
snes9x **-joydev1 "/dev/input/js0"**    /path/to/some/rom.smc
```



I also use the  **-y4**  flag to smooth out the pixels when maximised.   No sound yet.. back to google lol

---

### Post by dfreer on 2007-11-30
> **po0f said:**
> TheForkOfJustice,

To fix the sound issue in zsnes:

```
$ sudo apt-get install libsdl1.2debian-oss
```

This works, also, you can use zsnes 1.51 (which is compiled with libao support), and use the libao sound library like so:
```
zsnes -ad oss
```
Changing the sound frequency from 32000 to 48000 can help sometimes as well, but using libao takes care of any sound issues in most cases. No need to compile either, zsnes 1.51 is available in the official repositories for i386, and I've made a .deb for amd64/i386 that works great as well.

I was unable to get snes9x to work with my logitech dual action myself. I'm not exactly sure on how it maps the controls, but I know snes9express expects the controller to be at /dev/js0, where it's actually at /dev/input/js0

---

### Post by acoustibop on 2007-11-30
Try putting a symlink to /dev/input/js0 in /dev, dfreer.  This is a useful trick for a lot of applications that look for your controller in /dev - particularly some that can't be reconfigured. ;)

---

### Post by fluffiethesock on 2007-12-16
I don't know if anyone is still having a problem with the game pad, but I spent nearly two hours downloading drivers, rebooting my computer, changing settings, etc.. only to discover that the controller has to be set for Joypad #1. I had assumed that if you disabled the first controller and enabled the second, you'd be able to use #2 as #1. NOPE. DUMB.

---

### Post by pasha2891 on 2007-12-16
I had this issue.  Once I updated the snex9x.conf to the correct mappings on the gamepad and then passed the "snes9x -joydev1 "/dev/input/js0" " everything seemed to work fine.  I got both joysticks working if anyone is wondering.

---

