---
title: "Halloween The new nightmare - the first playable release for Linux x86-64!"
date: 2021-11-13
forum: Gaming &amp; Leisure
---

### Post by mateo14 on 2021-11-13
Hi

This is amazing! You can download a first playable version of Halloween:  The new nightmare for Linux. Farox fixed the issue with loading the TGA  images, and pocak100 solved many other issues that you can see below:

- Turn on automatic mipmap generation
- Add CMake as an alternative build method
- Enable window
- Let's show what we draw in the window
- Let us interact with the menu
- Don't skip the splash screen
- Fix console buffer overflow
- Reenable keyboard
- Load jpeg files using libjpeg-turbo
- Plug memory leak
- Don't delete textures in UnloadMap(), since we never reload them
- Nasty workaround to keep the mouse within the game window
- Grab all input while ingame
- Restore labels in the controls menu
- Rectify confusion between color and depth buffer bit depths
- Plug another leak
- Fix some minor buffer overflows
- We're not using GLU anymore 

I would like to remind you that the commercial version was published for Linux in 2003, and now you can play it for free:

[https://github.com/brizzly/Halloween3D](https://github.com/brizzly/Halloween3D)Halloween The new nightmare - the first playable release for Linux x86-64!

---

### Post by mateo14 on 2021-11-30
Last week, Julien Meyer from Jadeware decided to get back to developing the open source version of Hallowen.

You need libsdl-dev and libturbojpeg to build it on Linux.

sudo apt install libsdl1.2-dev libturbojpeg0-dev

You can use my script to quickly download, build, and run Halloween on Linux:

#!/bin/sh
git clone --recursive [https://github.com/brizzly/Halloween3D.git](https://github.com/brizzly/Halloween3D.git)
cd Halloween3D/HalloweenSrc
mkdir Build
cd Build
cmake ..
make
cd Halloween3D/HalloweenSrc/Build
cp halloween ../../distrib
cd ..
cp libbass.so ../distrib
cd ..
cd distrib
./halloween

---

