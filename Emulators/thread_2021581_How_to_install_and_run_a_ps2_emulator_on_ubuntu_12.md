---
title: "How to install and run a ps2 emulator on ubuntu 12.04?"
date: 2012-07-09
forum: Emulators
---

### Post by Braden57 on 2012-07-09
Hey I don't know much about computers so if someone can explain the steps to finding, installing and actually using a playstation 2 emulator on ubuntu 12.04 that would be great! :) Again, i don't know any computer terms, however i know that 32 bit is what i have. If that makes sense.

Thanks in advance!

---

### Post by madjr on 2012-07-09
i havent triedit myself, I personally have only tried all other systems till ps1.


but I believe these might help:

[http://www.ubuntubuzz.com/2011/03/5-greatest-ubuntu-game-console-emulator.html](http://www.ubuntubuzz.com/2011/03/5-greatest-ubuntu-game-console-emulator.html)

[http://www.youtube.com/watch?v=n-l_U0hk0d4](http://www.youtube.com/watch?v=n-l_U0hk0d4)

[http://www.ubuntumine.com/playstation-2-emulator-bios/](http://www.ubuntumine.com/playstation-2-emulator-bios/)

---

### Post by sffvba[e0rt on 2012-07-09
*Thread moved to **Emulators**.*


404

---

### Post by thatguruguy on 2012-07-09
> **Braden57 said:**
> Hey I don't know much about computers so if someone can explain the steps to finding, installing and actually using a playstation 2 emulator on ubuntu 12.04 that would be great! :) Again, i don't know any computer terms, however i know that 32 bit is what i have. If that makes sense.

Thanks in advance!

PCSX2 is a PS2 emulator that runs on Linux (and Windows, as well). You can install the "official" pcsx2 ppa by opening a terminal and typing the following:
```
sudo add-apt-repository **ppa:gregory-hainaut/pcsx2.official.ppa**
```
Follow the on-screen prompts. When that is finished, type the following to install the package:
```
sudo apt-get update
sudo apt-get install pcsx2-unstable
```

---

### Post by Ikesurmarth on 2012-07-11
@thatguruguy, Cool, it worked! I'm gonna get Kingdom Hearts 2 on it later. :D

---

### Post by Dlambert on 2012-07-12
Please mark this thread as solved:)

---

### Post by ejcottier on 2012-09-25
> **thatguruguy said:**
> PCSX2 is a PS2 emulator that runs on Linux (and Windows, as well). You can install the "official" pcsx2 ppa by opening a terminal and typing the following:
```
sudo add-apt-repository **ppa:gregory-hainaut/pcsx2.official.ppa**
```
Follow the on-screen prompts. When that is finished, type the following to install the package:
```
sudo apt-get update
sudo apt-get install pcsx2-unstable
```

Hi there, I'm running Ubuntu 12.04 and I just installed PSCX2 (following your instructions). It installed just fine, no unmet dependencies or errors. But when I choose the ISO and run it, I get a blank screen and the UI interface freezes (so I have to kill it). Although there's no error messages :S 

This is the terminal output:


Interface is initializing.  Entering Pcsx2App::OnInit!
Applying operating system default language...
Command line parsing...
Command line parsed!
ZZogl-PG: Calling GSinit.
ZZogl-PG: GSinit finished.
ZZogl-PG: Calling GSopen2.
ZZogl-PG: Capturing ZZOgl window.
ZZogl-PG:  Got Doublebuffered Visual!
ZZogl-PG:  glX-Version 1.4 with Direct Rendering
ZZogl-PG:  Using multitexturing.
ZZogl-PG:  Maximum texture size is 2048 for Tex_2d and 2048 for Tex_NV.
ZZogl-PG: Disabling MRT depth writing.

And no errors on the log window either, just "Opening GS" and that's it.

Do you have any idea what I should do to get it to work? 

Just thought I'd mention that I got it to work in windows XP, but it was unplayable (slow motion kinda slow). 

I have a Intel Pentium 4 Hyperthreading Processor @ 3ghz

This is my graphics info (sorry, not an ubuntu expert)

*-display               
       description: VGA compatible controller
       product: 82915G/GV/910GL Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 04
       width: 32 bits
       clock: 33MHz
       capabilities: pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:cfd00000-cfd7ffff ioport:1800(size=8) memory:e0000000-efffffff memory:cfd80000-cfdbffff

---

### Post by mister_playboy on 2012-11-07
> **ejcottier said:**
> 

Do you have any idea what I should do to get it to work? 

I have a Intel Pentium 4 Hyperthreading Processor @ 3ghz

CPU recommendations from PCSX2's page
> Intel Core 2 Duo @ 3.2 GHz or better OR i3/i5/i7 @ 2,8 GHz or better OR AMD Phenom II @ 3,2 GHz or better

Your system is way too old to play any games at normal speed.  Even brand-new hardware can't always do that.

---

### Post by valroadie on 2012-11-12
Just wanted to add to this.
 My system:

Macbook 2,1
Ubuntu 12.04 LTS 
1 gig of ram
core 2 duo 3.0ghz

I have installed and ran this emulator with success! Thank you to thatguruguy for the easy console commands.

---

### Post by stevo1977 on 2012-11-18
I, too, am having difficulty getting this emulator running. I have 64-bit Ubuntu 12.04 and installed from the ppa. When I try to configure the graphics the only option is for GSdx. When I try to load an ISO it brings up the game window but it freezes immediately (it doesn't get to the playstation loading screen or anything). The only output in the log window was
```
HLE Host: Will load ELF:
HLE Notice: ELF does not have a path.
```

I would like to try the zzogl plugin, but it isn't available from the dropdown, even though the .so file is in the plugins folder along with GSdx. Anyone have any idea as to how I can enable it or something?

Please let me know if I can provide any more information. Thanks!

stevo

---

### Post by Fende on 2012-12-31
> **thatguruguy said:**
> PCSX2 is a PS2 emulator that runs on Linux (and Windows, as well). You can install the "official" pcsx2 ppa by opening a terminal and typing the following:
```
sudo add-apt-repository **ppa:gregory-hainaut/pcsx2.official.ppa**
```Follow the on-screen prompts. When that is finished, type the following to install the package:
```
sudo apt-get update
sudo apt-get install pcsx2-unstable
```

It worked for me too. Good work!!!:)

---

### Post by stevo1977 on 2012-12-31
Update: I got it working once I installed the proprietary drivers for my Nvidia card.

Cheers,
stevo

---

