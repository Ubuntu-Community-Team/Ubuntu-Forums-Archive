---
title: "ATi drivers and Compiz"
date: 2007-12-22
forum: Desktop Effects &amp; Customization
---

### Post by sevenworth on 2007-12-22
have done everything as indicated in [http://ubuntuforums.org/showthread.php?t=580748](http://ubuntuforums.org/showthread.php?t=580748), but now the graphics is as slow as fap. i can harldy scroll down on this page without folding my arms and waiting.

Please, ffs, what the hell must i do?

---

### Post by webdr on 2007-12-22
What model ATI Video Card?
Post the results of the command: 
lspci |grep ATI

That command will list PCI devices including the AGP.
I have 4 of 5 of my ATI based PCs working flawlessly, and for the most part
they either work or they don't. I only allowed myself to lose one day to working
on the 200M based laptop, in the end, stability was only to be gained by giving up on
eye-candy entirely. 

Now that AMD owns ATI, you'll likely see a rapid change for hte better in linux support for ATI.

So, post the results from that command please.
-Mark Williams

---

### Post by sevenworth on 2007-12-22
```
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AS [Radeon 9550]
01:00.1 Display controller: ATI Technologies Inc RV350 AS [Radeon 9550] (Secondary)
```

---

### Post by sevenworth on 2007-12-22
...and you have an interesting and thoughtprovoking signature,

---

### Post by Farenheit on 2007-12-22
What do you get in terminal when you run fglrxinfo?

Personally, I followed this guide, and it worked for me:
[http://ubuntuforums.org/showthread.php?t=593348](http://ubuntuforums.org/showthread.php?t=593348)

---

### Post by webdr on 2007-12-22
RE.. Sig line...Thank You.


My 
00:01.0 PCI bridge: ATI Technologies Inc Radeon 9100 IGP AGP Bridge
01:05.0 VGA compatible controller: ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP]

On Gutsy, I enabled the restricted driver. Then 'System' --> 'Preference'-->'Appearance'

Selected Visual Effects tab, lastly enabled 'extras' option and it all worked very well.

On another laptop, it has the ATI 200M, and I get no love from that card using any of the eyecandy.

By the way, once you get extras working, go check out AWN (Avant Window Navigator)

I posted a screencast here: [http://www.markw.net/out2.ogg](http://www.markw.net/out2.ogg) to demonstrate the eyecandy.

Happy Holidays,
Mark Williams

---

### Post by sevenworth on 2007-12-23
```
*******@meridian:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 20060815 AGP 8x x86/MMX/SSE2 TCL
OpenGL version string: 1.3 Mesa 7.0.1
```

---

### Post by sevenworth on 2007-12-23
I followed that tute in first post, and the extra eye candy worked. well, sort of. Moving windows around was really slow (you can see the windows being redrawn from the bottom up) until i moved a window sideways onto another desktop, as soon as the cube starts to animate, everything else (wobbly windows etc) worked fast and smooth until the cube anim finishes, the desktop settles, then its slow again. Any ideas on this?

---

### Post by sevenworth on 2007-12-23
one other thing. If I go to restricted drivers, and enable the ATI graphics driver, reboot, then I get an unreadable screen and can only re4cover the installation by starting up recovery mode and doing a dpkg-reconfigure xserver-xorg

---

### Post by sevenworth on 2007-12-23
ok i've got it working now. everything seems fine, except for when I resize a window. As soon as that happens, the whole thing slows down to snails pace. ideas?

---

### Post by MangasColoradas on 2007-12-23
I dont think it should have 'mesa' there.

I dont have any advice, except that I have followed a lot of 'how-tos' with no success with my 9800pro. I am just using the open source drivers atm.

My current thinking is that I need to manually edit the xorg.conf after I install the fglrx driver, as it seems rebooting causes the settings to be lost. (I think its the xserver-xgl install that causes this? that only applies to using the standard restricted driver, as you know, the more recent fglrx doesnt use xgl).

---

### Post by sevenworth on 2007-12-23
Ok... any thoughts on the window resizing thing? I've disabled it now so that  I dont accidentally resize anything and force myself to restart x.

---

### Post by webdr on 2007-12-23
Are you on gutsy?
Did you try to install compiz or just using the visual effect setting?

-Mark Williams

---

### Post by sevenworth on 2007-12-23
I've done everything that the tutorial says (lnked from the first post in this thread). If that means that I installed compiz then yes. I know that the options under desktop effects have changed, and I am now allowed to customize settings.

---

### Post by MangasColoradas on 2007-12-23
This is from the tut you followed, just a bit further down :)


> Troubleshooting

A common problem in step 10 is fgrlxinfo output like this:
Code:

# fglrxinfo -display :0
display: :0.0 screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

.
That means you are not using the restricted driver. Enable it via Restricted Driver Manager -- see step 8. Just in case, run command
Code:

sudo aticonfig --initial

then reboot (that's step 9).



That should fix it for you, unless you have a problem card like me......

---

### Post by Farenheit on 2007-12-23
Window resizing is going to be slow as far as I have seen (haven't found any fixes yet...apparently a driver issue).  What I had to end up doing was running CompizConfig (System > Administration > Advanced Desktop Effects Settings) and look for the "Resize Window" setting.  Click it to open it's preferences.  For "Default Resize Mode," choose "Rectangle."  It's not as sexy, but makes it bearable.

---

