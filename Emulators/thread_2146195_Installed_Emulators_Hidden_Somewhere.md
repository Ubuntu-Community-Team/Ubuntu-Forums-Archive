---
title: "Installed Emulators Hidden Somewhere"
date: 2013-05-17
forum: Emulators
---

### Post by Cu Rua on 2013-05-17
Downloaded Desmume, VisualBoyAdvance, and Mednafen, but only Desmume shows up under applications. 

Software Center says I have all these programs, but I can't find an icon to open VBA or Mednafen. 

Right-clicking on a game file to "open under other application" doesn't bring up any emulators at all. 

I haz ninja emulators?? 

OS: Ubuntu 10.04.3

---

### Post by Lightning Dragon on 2013-05-17
Hi,
 
In Software Center, by the way, there are two gameboy emulators, which are "VBA Express" and Visual Boy. Are you sure you installed the later, and not VBA Express? Well, maybe you can find them this way;

VisualBoy installs via "usr/bin" and "usr/share/VisualBoyAdvance". These paths are given assuming Ubuntu 10.04.3 shares the same setup as 12.04 and Linux Mint. If you open up your file manager and go into file system or usr and search up "VisualBoy" (or any other emulator) then you will be given your results. With them, you can make launchers or make edits to your launch bar. :)

Or you can try a command line to find them;

locate visualboyadvance

Which, for me, brings this up;

/usr/share/app-install/desktop/visualboyadvance-gtk:VisualBoyAdvance.desktop

Going to that folder I find the launcher for the emulator with the image of a gameboy advance. :)

---

