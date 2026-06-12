---
title: "Problem installing ATi Radeon 8.16.20 drivers!"
date: 2005-10-05
forum: Desktop Environments
---

### Post by St3althcAt on 2005-10-05
Hello!
I've recently reformatted my Linux partition and I've installed it again and all stuff. I've download the .run file from ATi website with their latest drivers, that I did manage to install succesfully after the reformat of the partitions, but now I can't install them. I download and run the .run file with the installer, select the first option and then Automatic. It install without problems (I think). Then I run fglrxconfig, create the xorg.conf file and reboot. System boots ok, but using the Mesa renderer. I went to this website, [http://www.objorkum.com/scripts/fglrxconfig/](http://www.objorkum.com/scripts/fglrxconfig/) but it also boots with the Mesa renderer. Don't understand the problem :\! Ask any information you want (lol, I don't mean address and name and my credit card number hehehe!), log files, whatever, as long as I put this to work. Thank you!

---

### Post by KingBahamut on 2005-10-05
whats your xorg.conf file say? post in here?

Ive had pretty decent success with the ati drivers.

---

### Post by Dolphin on 2005-10-05
Do you have kernel headers installed?

---

### Post by St3althcAt on 2005-10-05
Here is my xorg.conf file:

Section "dri"
     Mode 0666
EndSection

Section "Module"
     Load "dbe"

SubSection "extmod"
     Option "omit xfree86-dga"
EndSubSection

     Load "type1"
     Load "freetype"
     Load "glx"
     Load "dri"
EndSection

Section "Files"
     FontPath "/usr/X11R6/lib/X11/fonts/local/"
     FontPath "/usr/X11R6/lib/X11/fonts/misc/"
     FontPath "/usr/X11R6/lib/X11/fonts/75dpi/:unscaled"
     FontPath "/usr/X11R6/lib/X11/fonts/100dpi/:unscaled"
     FontPath "/usr/X11R6/lib/X11/fonts/Type1/"
     FontPath "/usr/X11R6/lib/X11/fonts/75dpi/"
     FontPath "/usr/X11R6/lib/X11/fonts/100dpi/"
EndSection

Section "InputDevice"
     Identifier "Keyboard"
     Driver "kbd"
     Option "XkbRules" "xorg"
     Option "XkbModel" "pc105"
     Option "XkbLayout" "pt"
EndSection

Section "InputDevice"
     Identifier "Mouse"
     Driver "mouse"
     Option "Protocol" "ImPS/2"
     #Option "Buttons" "7"
     Option "ZAxisMapping" "4 5"
     Option "Device" "/dev/input/mice"
EndSection

Section "Monitor"
     Identifier "Monitor"
     Option "DPMS"
EndSection

Section "Device"
     Identifier "Device"
     Driver "fglrx"
     Option "UseInternalAGPGART" "yes"
     Option "TVFormat" "NTSC-M"
     Option "TVStandard" "VIDEO"
     Option "DesktopSetup" "single"
     Option "VideoOverlay" "on"
     Option "OpenGLOverlay" "off"
     #Option "OverlayOnCRTC2"
EndSection

Section "Screen"
     Identifier "Screen"
     Device "Device"
     Monitor "Monitor"
     DefaultDepth 24

Subsection "Display"
     Depth 24
     Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubsection

EndSection

Section "ServerLayout"
     Identifier "ServerLayout"
     Screen "Screen"
     InputDevice "Mouse" "CorePointer"
     InputDevice "Keyboard" "CoreKeyboard"
EndSection

Graphic card: Sapphire ATi Radeon 9000 Pro 128 Mb

I'm afraid the problem isn't on the xorg.conf file, but on the drivers itself that are not installing correctly (maybe the kernel module is not being installed, but I'm a newbie, so... :P, just a guess).

Uh, by the way, Kernel headers? Uh, is that for eating :P!? How do I install those?

Thank you!

---

### Post by Dolphin on 2005-10-05
Open synaptic.  Search for headers.  Install the kernelheaders appropriate for your kernel.  Then try again with the drivers.

---

### Post by St3althcAt on 2005-10-05
Kernel headers installed. Problem persists.

---

### Post by Dolphin on 2005-10-05
Reinstall drivers.
Open console.
enter "sudo modprobe fglrx"
reboot

If that doesn't work then I dunno. :)

---

### Post by St3althcAt on 2005-10-05
Once more, thank you for the posts.
Nope, not working. I'm installing the drivers via apt-get (the old ones), just to have them temporarily, as I need the 8.16.20 for World of Wacraft and some games work without problems. Any other answers are welcome!

Thank you!

---

### Post by mlomker on 2005-10-05
My [how-to]("http://www.ubuntuforums.org/showthread.php?p=348911") works reliably.  Give it a try.

---

### Post by jlx on 2005-10-05
After you run the installer from Ati, you have to compile the fglrx libraries. 
```
 cd /lib/modules/fglrx/build_mod/
sh make.sh 
```
and then
```
cd /lib/modules/fglrx/
sh ./make_install
```

Everytime you install the drivers or install a diferent version of your xorg server you have to recompile the fglrx libraries.
I leave you a tutorial I wrote in spanish. But at the end of the tutorial you can find all the posts from the ubuntu forums I used to write it. All the information and problems are there. Try to compile the libraries as I told you before and then modprobe fglrx.

[http://foro.linuxjuegos.com/viewtopic.php?t=62&start=0&postdays=0&postorder=asc&highlight=]("http://foro.linuxjuegos.com/viewtopic.php?t=62&start=0&postdays=0&postorder=asc&highlight=")

---

### Post by St3althcAt on 2005-10-05
Installed the drivers via rpm downloaded from ati (turned into deb using alien, etc.). Then I've done what jlx suggested and it worked. Doesn't know what caused it, the instalation through rpm package or the jlx tip, but they're working. Thank you for all the posts and help!

---

### Post by St3althcAt on 2005-10-07
Due to some reasons I had to reformat my Linux partition and now I can't get them to work again, but I have found what I believe is the reason of the error: when I startx, I see a message like this "fglrx(0) incompatible kernel module detected...", something like this. What should I do? Thank you!

---

### Post by mlomker on 2005-10-07
You should probably look through the /var/log/Xorg.0.log file for details.

---

