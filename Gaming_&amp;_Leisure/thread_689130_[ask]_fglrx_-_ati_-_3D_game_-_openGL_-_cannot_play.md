---
title: "[ask] fglrx - ati - 3D game - openGL - cannot play game (automatic loggoff)"
date: 2008-02-06
forum: Gaming &amp; Leisure
---

### Post by doliharahap on 2008-02-06
Haii All..

I'm new in gaming, especially on ubuntu.
When the first time i used this ubuntu, i only use fglrx one (for driver of my vga card). I can play any of 3D game eventhough it was not running very well (very slow).

Then i tried to installl the driver that provided by AMD-ATI.
after that, i can play any 3D game. it always log off my desktop.

Why?:confused::confused:


before then, any one could explain to me what are these about:
- fglrx
- openGL

thanks all, sorry my englsih is not good enough.

---

### Post by FrozenFox on 2008-02-06
* Fglrx is the proprietary (ie "non-free" / closed source) video card driver software for ATI cards in linux. There is also a free (open source) driver not from ati for ati cards, but I hear it doesn't work as well in terms of 3d stuff. The drivers labeled "fglrx" are from ATI/AMD, whereas the drivers labeled "ati" are the open source community's drivers, from what I understand.

* OpenGL is, to the best of my understanding, free and open source software for windows, linux, and other operating systems which aids in creating and rendering 2d and particularly 3d software when combined with the video drivers, especially in games and other multimedia applications. 

* FYI, DirectX is the windows counterpart to opengl, but is of course closed source and does not exist on linux in its "actual" form. Programs such as WINE, Cedega, and Crossover Office on linux try to reproduce the libraries for directx and windows itself, from what i understand, in order to allow you to run (some) windows programs on linux.

* As for your speed and log-off issues, please tell me what version of ubuntu you are using (7.04 feisty fawn, 7.10 gutsy gibbon, 8.10 hardy heron?). Ubuntu, mostly for legal reasons, ships with the "ati" drivers by default instead of the "fglrx" drivers. The reason your games were slow was probably because the drivers were the open source "ati" ones, which have not yet reached the 3d capability the "fglrx" drivers have. The most likely reason your games are not playing at all right now is a messed up "fglrx" driver installation. Please tell us what your ATI video card model is along with any other relevant PC information you may have. Also, please give me the output of typing this in the terminal / konsole / console:  glxinfo | grep direct
What this does is run the program glxinfo, which prints out information about your video card to the console, and then gives the specific line with the word "direct" in it, which in this case will tell you whether or not you have direct rendering enabled (IE whether or not your video card drivers are working correctly).

---

### Post by acoustibop on 2008-02-06
More specifically, for the fglrx driver, post the output for entering fglrxinfo, please, doliharahap.

Which fglrx driver are you using, and how did you install it?

---

### Post by doliharahap on 2008-02-08
I'm using Gutsy Gibbon..

i installed the 'fglrx' by using the synaptic package manager. with the resource is from DVD repo gutsy.
When i installe it, it was ok for playing games. But because i felt it too slow, i tried installed the driver that i downloaded from ATI website. Then, the log-off thing happened.

My Vga Card is ATI MOBILITY XT1300..


How can i enter the fglrx info??

TQ bro..

---

### Post by acoustibop on 2008-02-08
Open a terminal (Applications -> Accessories -> Terminal), doliharahap, type fglrx and press Enter.

The easiest way to transfer the output to, for instance, a post here, is to highlight the text with your mouse, then click Edit and Copy.  Then change the focus to wherever you want to paste it, click where you want to paste to put the cursor there and press Control+v.

How did you install the fglrx driver from the ATI website, and which one was it?

---

### Post by doliharahap on 2008-02-13
Sorry..long time not replying..

here is my fglrxinfo output..

```
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1300
OpenGL version string: 2.1.7170 Release

```

I download from ATI/AMD, i got file with .run format.
i just do ./filename.run

that's it..
how can i back to the time before i installed the ATI/AMD driver??
or just simply uninstalled it??


TQ

---

### Post by Crylos on 2008-03-11
I have the same problem. I installed Oni on my laptop with Ubuntu and it worked fine. I could play the game properly. Then I decided to try and install Soul Reaver and, after installing, every time I tried to play Oni or the other one, the computer would just logoff automatically. If I try to uninstall Soul Reaver it just tells me the uninstall file isn't valid or might be corrupted. Maybe there's a way to backtrack what I did? Like a system rollback? Any help is apreciated ^^

Edit:By the way, sometimes it seems to work fine. Right now I have no idea what the problem might be...

---

