---
title: "What about gamepads?"
date: 2006-07-31
forum: Gaming &amp; Leisure
---

### Post by muxecoid on 2006-07-31
Hi, people what about USB gamepad support? It would be cool to play emulated PS games with gamepad under linux. Remapping joystick to non-game applications would also be cool. Can I use my gamepad as browser controller, like scrolling pages, opening bookmarks with gamepad key etc?

---

### Post by leech on 2006-07-31
As far as I know, it is possible to do all of what you mentioned.  Though not really easy.  I know at one point, my Dual Firestorm Power 3 (I think that's what it is called) worked out of the box, at least in Debian.  For some reason I always had to change permissions in Ubuntu.  

I play Playstation games all the time with it though, in fact at one point I think I even got the force feedback (well, ok, it's really just a vibration) working in Linux.  

Leech

---

### Post by muxecoid on 2006-07-31
Would there be any serious problems with Pine XFX Dual Gamepad (cheap) under linux?

Did you try to use it as input device for browser scrolling?

---

### Post by leech on 2006-07-31
I hadn't, though I think it's possible.  There are input drivers for joysticks/gamepads for X.org.  It could be an interesting project to do the research into this.

Leech

---

### Post by leech on 2006-08-01
Here's a quick start.  A simple search with 'apt-cache search joystick' reveals quite a lot.

**inputattach** - utility to attach serial devices to the input subsystem
dasher - A graphical predictive text input system
ddrmat-source - Linux kernel driver for using Playstation dancing mats (source)
fceu - FCE Ultra - a nintendo (8-bit) emulator
gl-117 - An action flight simulator
gl-117-data - Data files for gl-117
gngb - GameBoy Emulator
**joy2key** - Translate joystick movements into equivalent keystrokes
joystick - Testing and calibration tools
jscalibrator - GTK Joystick Calibrator
libgii0 - General Input Interface runtime libraries
libjsw-dev - Joystick Library header files
libjsw2 - Joystick Library
lsr - The Linux Screen Reader for GNOME
mednafen - multi-platform emulator, including NES, GB/A, Lynx, PC Engine
mixxx - Digital Disc Jockey Interface
mixxx-data - Digital Disc Jockey Interface -- data files
plib-doc - Portability Libraries: documentation and examples
plib1.8.4-dev - Portability Libraries: Development package, stable release
plib1.8.4-pic - Portability Libraries: Dev. package (with PIC code), stable rel.
plib1.8.4c2 - Portability Libraries: Run-time package, stable release
**psemu-input-omnijoy** - Controller/keyboard plugin for PSX emulators
**psemu-input-padjoy** - Controller plugin for PSX emulators
python-pygame - SDL bindings for games development in Python
python2.4-pygame - SDL bindings for games development in Python 2.4
searchandrescue - fly aircraft to search (for) and rescue people in distress
visualboyadvance - a full featured Game Boy Advance emulator
xblast-tnt - multiplayer blast-the-others game inspired by Dynablaster
**xserver-xorg-input-joystick** - X.Org X server -- joystick input driver
dgen - Sega Genesis/MegaDrive emulator
xtrs - emulator for TRS-80 Model I/III/4/4P computers

Leech

---

