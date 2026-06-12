---
title: "OpenGL failed to initialize"
date: 2011-11-05
forum: Gaming &amp; Leisure
---

### Post by Sky_City on 2011-11-05
Alright, I've been searching for previous threads, for people having encountered this problem, and haven't found anything that could help my particular situation. I'm very new to linux, having just replaced it a few days ago.

Here's my problem, I try to run a game executable, but get an error message:


Game Startup Error: Unable to set up graphics.
Reason: Failed to initialize OpenGL display.

To help fix this problem make sure you are running the newest version of your video drivers.
Lastly, you could try running this game with the -windowed command-line option.


running glxinfo, here's the output:



name of display: :0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Error: couldn't find RGB GLX visual or fbconfig

Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".


Any clues? Thanks much in advance.

---

### Post by thatguruguy on 2011-11-05
What kind of video card do you have?

---

### Post by Sky_City on 2011-11-05
I'm using a touchsmart tm2 tablet pc, i looked up the specs and it says "Intel HD Graphics". In system info, in Overview, the description next to "Graphics" is blank. Does that help?

---

### Post by thatguruguy on 2011-11-05
Type the following into a terminal, and post the result here:
```
lspci -nn | grep VGA
```
Also, what version of Ubuntu are you running?  How did you install it?

---

### Post by Sky_City on 2011-11-05
here it is:


00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 02)


I'm running Ubuntu 11.10, installed from a usb flash drive.

---

### Post by thatguruguy on 2011-11-05
Frankly, I'm not sure if your hardware will support 3D gaming.

You can try the following. Open a terminal and type the following:
```
sudo apt-get install libgl1-mesa-drv libgl1-mesa-dri libgl1-mesa-dev
```

---

### Post by thatguruguy on 2011-11-05
by the way, what "game executable" are you trying to run?

---

### Post by Sky_City on 2011-11-05
It should definitely be capable of supporting 3d gaming, I've run Homeworld II and other 3D games on it before using Windows. Also, the game I'm trying to run is Braid.

---

### Post by thatguruguy on 2011-11-05
The version of Braid from the ubuntu software center?

---

### Post by Sky_City on 2011-11-06
No I downloaded it via torrent.

Entered the line in the terminal:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libgl1-mesa-drv

Tried running the game again, still no go.

---

### Post by thatguruguy on 2011-11-06
> **Sky_City said:**
> 
Entered the line in the terminal:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libgl1-mesa-drv

Tried running the game again, still no go.
Sorry, I mistyped. It's:
```
sudo apt-get install libgl1-mesa-dev libgl1-mesa-dri libgl1-mesa-glx
```

> **Sky_City said:**
> No I downloaded it via torrent.
Braid is for sale. It's not free software.  

You can buy it in the ubuntu software center. Do so, and I'll be happy to help you further.

---

### Post by Sky_City on 2011-11-06
Fair enough. Thanks for your help so far, should I buy it I'll post again.

---

