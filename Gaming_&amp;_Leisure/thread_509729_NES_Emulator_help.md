---
title: "NES Emulator help"
date: 2007-07-25
forum: Gaming &amp; Leisure
---

### Post by ninja_in_pajamas on 2007-07-25
I know there arep lenty of emulators out there, but I would like a recommendation or two.  There is one thing I need the emulator to be able to do (Other than play the games obviously).  I really need one that will let me use the XBOX 360 PC Controller.  I don't need to be able to use the triggers or even the analog stick.  All I need is x,y,a,b,start,select,and the D-pad.  Any suggestions?

---

### Post by tbroderick on 2007-07-25
[http://ubuntuforums.org/showthread.php?t=404577](http://ubuntuforums.org/showthread.php?t=404577)

---

### Post by hikaricore on 2007-07-25
The NES didn't have X & Y keys.  However the SNES did... lol

---

### Post by ninja_in_pajamas on 2007-07-26
Yes, I know Hikaricore, but the X and Y keys can easily be mapped as turbo versions of A and B.  That is what I do on NEStopia, and I see there is an unofficial version of it for linux, but I don't know how to compile it.

---

### Post by DoktorSeven on 2007-07-26
If you can get your 360 controller working as a standard gamepad under Linux, nearly any program that uses joysticks should be able to use it, so just use FCEU (and its frontend, gfceu).

I don't own a 360 controller so I don't know what's involved in getting it working, though I would think any USB controller would show up as at least a standard HID gamepad.

---

### Post by OffAxis on 2007-07-26
have you tried mednafen?
[http://www.mednafen.com]("http://www.mednafen.com")
It's officially supported in the repositories (so no compile) and can be run from the command line.
[B]
sudo apt-get install mednafen[/B]

and then

**mednafen /path/to/rom**

Once started it's just ALT+SHIFT+1 to configure the joystick. I don't have an X-box controller, but my Logitech one works fine.

---

### Post by 2manydrugsago on 2008-01-30
I  don't know how to compile so is there an NES emulator that I  can key map for my keyboard. I can follor direction for repositories. I don't need help with suppositories.

---

### Post by Dr. Clock on 2008-05-09
This is what happened in my command line:
ray@ray-desktop:~$ sudo apt-get install mednafen
[sudo] password for ray:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mednafen is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ray@ray-desktop:~$ mednafen /path/to/rom
Starting Mednafen 0.8.1
 Loading settings from "/home/ray/.mednafen/mednafen.cfg"...
 Initializing joysticks...
  Joystick 0 - Microsoft Xbox 360 Wireless Controller (PC) - Unique ID: e462ea11338354e1
  Joystick 1 - Microsoft Xbox 360 Wireless Controller (PC) - Unique ID: e462ea11338354e2
  Joystick 2 - Microsoft Xbox 360 Wireless Controller (PC) - Unique ID: e462ea11338354e2
  Joystick 3 - Microsoft Xbox 360 Wireless Controller (PC) - Unique ID: e462ea11338354e2
 Loading /path/to/rom...

Error opening "/path/to/rom": No such file or directory
ray@ray-desktop:~$

---

### Post by DoktorSeven on 2008-05-09
Don't actually type /path/to/rom, that's just instructions that you should type the full file system path to your ROM file...

---

### Post by BigSilly on 2008-05-09
I totally recommend both Mednafen and NEStopia. I think I'd probably say to go for Mednafen first, since a pretty up to date version is in the repos, and there's no compiling to do. NEStopia is similarly excellent, but you have to compile it. It's easy enough to do, though to be fair. 

Myself I'm currently using Mednafen, but when the new version of NEStopia comes out I'll give that a go too. Have both I say! :D

---

### Post by acoustibop on 2008-05-09
If you use Mednafen and also want to take advantage of its excellent Sega Master System emulation capabilities (only in recent versions), get this [.deb for version 0.88]("http://ubuntuforums.org/showpost.php?p=4655351&postcount=26") that FranMichaels was kind enough to post, as the pause function is not enabled in the previous version - and it's essential for some games.

---

### Post by NightCrawler03X on 2008-06-25
There are only two NES emulators worth using:
Nestopia
Nintendulator

Both of these are cycle-accurate, which basically means that they emulate the consoles as accurately as possible. Nestopia is more up-to-date than Nintendulator is.

I would recommend Nestopia:
Get the Nestopia 1.40 source code from [http://nestopia.sourceforge.net/](http://nestopia.sourceforge.net/)
It's windows only, but there is an "overlay" that compiles with Nestopias core, allowing you to use Nestopia on Linux [http://rbelmont.mameworld.info/?page_id=200](http://rbelmont.mameworld.info/?page_id=200)

---

### Post by disturbedite on 2008-06-25
yes, definitely use nestopia. 1.40(g) was just released with major improvements.

---

