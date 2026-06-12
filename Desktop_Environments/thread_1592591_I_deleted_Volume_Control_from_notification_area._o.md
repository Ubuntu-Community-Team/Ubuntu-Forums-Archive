---
title: "I deleted Volume Control from notification area. oops"
date: 2010-10-10
forum: Desktop Environments
---

### Post by elisimmer on 2010-10-10
I was trying to right click and delete something from the panel, but in my haste I missed and deleted the volume control button from the notification area. (don't ask)

Anyway the volume control for the notification area is not in the "add to panel" menu. 

What do I do?

---

### Post by Frogs Hair on 2010-10-10
You can drag the sound icon from the preferences menu if you want.

---

### Post by bigsmitty64 on 2010-10-10
right click panel/add to panel/**indicator applet**
Hopefully this is what ya need?

---

### Post by DanPerecky on 2010-10-11
in Synaptics: _**asmix**_ - display a volume knob.

my installed Vrs: 1.5-4

---------------------
There are (at least) two other pkgs. I haven't used them, but they look cool:

_**kmix**_ - KMix is an audio device mixer, used to adjust volume, select recording inputs,
and set other hardware options.

**_gnome-alsamixer_** - A "volume control" application. You can use it to adjust the volume
of different sound sources of your sound card.

It has a nice graphical user interface and a lot of features:

 - access to all of your computers sound cards and audio sources
 - possibility to give them custom names
 - only display the mixer controls you need
 - access to all the extra features some sound cards offer, like
   3d enhancement, microphone gain boost...
 - and more

This application uses the ALSA sound API, you cannot use it if you
use the (older) OSS drivers for your sound card(s). In return, it
gives you access to all the functionality ALSA provides with the
"alsamixer" program, found in the "alsa-utils" package.
**---Update: Installed gnome-alsamixer. This is the pkg that you see when you right-mouse click on the sound button. Nice prg, but I'm guessing no value add here.**

---

### Post by elisimmer on 2010-10-13
> **bigsmitty64 said:**
> right click panel/add to panel/**indicator applet**
Hopefully this is what ya need?

This is exactly what I wanted, thank you.

---

### Post by bigsmitty64 on 2010-10-13
You are welcome! Glad to help.

---

