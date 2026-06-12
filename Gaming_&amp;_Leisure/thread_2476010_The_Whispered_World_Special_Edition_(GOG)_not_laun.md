---
title: "The Whispered World Special Edition (GOG) not launching"
date: 2022-06-14
forum: Gaming &amp; Leisure
---

### Post by vindicivuoto on 2022-06-14
Getting the following message in the terminal:

[I]Running The Whispered World: Special Edition ./TWWSE: error while loading shared libraries: libopenal.so.1: cannot open shared object file: No such file or directory

It looks like the player crashed! If you need support, please include the contents of the log file in your problem report. Unfortunately, no log file has been created![/I]

A bit of googling told me this was due to trying to run a 32-bit game on a 64-bit system (22.04 LTS). If anyone has encountered and managed to solve this problem, please steer me in the right direction.

---

### Post by Dennis N on 2022-06-14
> error while loading shared libraries: libopenal.so.1: cannot open shared object file: No such file or directory
This is common when installing Linux games. How to fix it:
Visit [Ubuntu Package Search]("https://packages.ubuntu.com/")
Look for the section shown in the secreenshot below, enter the name of the "shared library" and press Search.
The list of any Ubuntu packages supplying this library is shown. Pick the architecture you need to install. If you know for sure it's a 32-bit program, you need to install the i386 package. After you have installed the package with apt, reboot and try again with the program.

Note: The 32-bit package is **libopenal1:i386** You will get a bunch of other 32-bit packages that are dependencies. That is a good thing.

---

### Post by vindicivuoto on 2022-06-15
Thanks for your time. Turns out I just had to install Wine.

---

