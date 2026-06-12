---
title: "[Official Game Thread] Toadeki"
date: 2014-02-27
forum: Gaming &amp; Leisure
---

### Post by slooksterpsv on 2014-02-27
Instead of posting numerous updates on a single thread and to keep things simple. I'm making this an official thread on my game Toadeki.

**Toadeki v0.0.5a** 
Linux released
Date: *04/14/2014*

Windows still on v0.0.4a

Requirements (Linux):
[LIST]
[*]libsdl2
[*]Libraries dependent on libsdl2
[*]Accelerated graphics on Linux - maybe
[/LIST]

Requirements (Windows):
[LIST]
[*]Windows XP SP2 or later (Windows 7 recommended)
[*]Libraries are already in the application folder
[/LIST]

Linux Download: [https://drive.google.com/file/d/0BzvZWf6CGx93LVNLNnUzUnlCNzQ/edit?usp=sharing](https://drive.google.com/file/d/0BzvZWf6CGx93LVNLNnUzUnlCNzQ/edit?usp=sharing)
Last Update 2/27/14 - **0.0.4a**Windows Download: [https://drive.google.com/file/d/0BzvZWf6CGx93TnE1Y0xmZXdDVW8/edit?usp=sharing](https://drive.google.com/file/d/0BzvZWf6CGx93TnE1Y0xmZXdDVW8/edit?usp=sharing)

What needs tested:
[INDENT]32-bit version of Linux version with SDL2 libraries installed - I didn't specify an architecture, so I don't know if this works on 32-bit. I run only 64-bit machines and VM's won't work as they don't have get the accelerated graphics versions.
Report any reproducible crash, bug, etc. with accompanying steps.
Report if anything visually happens after running the game.[/INDENT]

What's new since v0.0.4a?
[INDENT]
Removed most compiler warnings which cause bugs.
Updated scheme for files again.
Fixed bug regressions with opening maps, files, tilesets, etc.
Limited rocks (no notification of how many yet).
Better memory handling (still leaky).
Updated window title to reflect version. Still not on the first screen.
Editor no longer works as many core components changed, but have yet to be updated to reflect said changes.
[/INDENT]

What's new since v0.0.3a?
[INDENT]
Fixed a bug where memory leaks were happening when reading files using fscanf.
Fixed a bug where game would randomly crash when changing maps.
Fixed a bug where game would crash on startup thinking it had to change maps.
Changed naming schema for maps.[/INDENT]

---

