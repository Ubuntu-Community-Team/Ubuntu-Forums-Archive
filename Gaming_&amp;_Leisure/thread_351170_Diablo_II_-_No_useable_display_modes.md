---
title: "Diablo II - No useable display modes"
date: 2007-02-01
forum: Gaming &amp; Leisure
---

### Post by darkkterror on 2007-02-01
I just installed D2 under wine on Edgy.  When I ran the D2VidTst.exe to check for video modes it tells me that there are no useable display modes.  Then it just tells me to make sure I have Windows 95/98, DirectX, and the latest video drivers.

I'm guessing the problem either lines with wine not having configured my video card properly or my video card isn't configured properly period.  I'm running on a Dell laptop with an integrated Intel 945GM chipset.  My laptop can run D2 perfectly on Direct3D mode under Windows so I know the problem isn't that my card isn't capable.

As for which video driver I'm using it's the i810 (according to xorg.conf).  Is there a later version I need or is there something in wine I have to configure?  I simply installed wine using apt-get (version 0.9.22) and I was able to install D2 and LOD flawlessly with no configuration necessary.

---

### Post by blakzer0 on 2007-02-01
Here are my ideas:
1. Try running diabloII vidtest from the command line to see if thats the issue.
2. Run glxgears in the terminal to test to see if it is infact your card.
3. If glxgears runs just fine try downloading the latest GLIDE3-to-OpenGL-Wrapper. [http://www.tu-harburg.de/~sisl0020/english/index.html](http://www.tu-harburg.de/~sisl0020/english/index.html) and run the vidtest again and select opengl.

Hope this helps!

---

### Post by darkkterror on 2007-02-02
Thanks, the glide wrapper thingy worked.  Diablo II runs and is fully patched.

The only problem now is I have no sound.  The sound options in game is grayed out, so I would guess that wine isn't properly detecting/configuring my sound card or what not...

---

### Post by Josey on 2007-02-02
run winecfg and configure sound there.

---

### Post by darkkterror on 2007-02-02
When I rune winecfg and I click on the Audio tab it immediately closes the window and the terminal reports this error:

ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
Creating link /home/mike/.kde/socket-mike-laptop.
can't create mcop directory

---

