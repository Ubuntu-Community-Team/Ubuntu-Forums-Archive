---
title: "Diagnose my zsnes console output?"
date: 2008-03-27
forum: Gaming &amp; Leisure
---

### Post by BetterSense on 2008-03-27
I'm a bit of a linux newbie, using gutsy with gnome right now, and I installed zsnes 1.51 from apt-get. This is what I got when I tried to run it:

```

chaz@0-1e-8c-92-86-74:~$ zsnes
ZSNES v1.51, (c) 1997-2007, ZSNES Team
Be sure to check http://www.zsnes.com/ for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

Starting Mouse detection.
Unable to poll /dev/input/event5. Make sure you have read permissions to it.
Unable to poll /dev/input/event7. Make sure you have read permissions to it.
Unable to poll /dev/input/event6. Make sure you have read permissions to it.
Unable to poll /dev/input/event4. Make sure you have read permissions to it.
Unable to poll /dev/input/event3. Make sure you have read permissions to it.
Unable to poll /dev/input/event2. Make sure you have read permissions to it.
Unable to poll /dev/input/event1. Make sure you have read permissions to it.
Unable to poll /dev/input/event0. Make sure you have read permissions to it.
ManyMouse: 0 mice detected.
Creating link /home/chaz/.kde/socket-0-1e-8c-92-86-74.
can't create mcop directory
chaz@0-1e-8c-92-86-74:~$ 
```

So I chmod 755 event* in the /dev/input directory, and now it does this

```
chaz@0-1e-8c-92-86-74:/dev/input$ zsnes
ZSNES v1.51, (c) 1997-2007, ZSNES Team
Be sure to check http://www.zsnes.com/ for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

Starting Mouse detection.
ManyMouse: 2 mice detected.
Using ManyMouse for:
Mouse 0: SynPS/2 Synaptics TouchPad
Mouse 1: Macintosh mouse button emulation
Creating link /home/chaz/.kde/socket-0-1e-8c-92-86-74.
can't create mcop directory
chaz@0-1e-8c-92-86-74:/dev/input$ 

```

And i'm not sure what to do now. Why does it say .kde? I'm not using KDE on this machine.

---

### Post by FranMichaels on 2008-03-27
Check the link in my sig, the mcop fix :)

---

### Post by BetterSense on 2008-03-27
You rocxxorzz.

---

