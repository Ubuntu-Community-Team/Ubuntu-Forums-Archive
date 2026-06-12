---
title: "zsnes buffer overflow"
date: 2009-01-03
forum: General Help
---

### Post by knowledge_is_power on 2009-01-03
hey, i installed zsnes from the repositories, but when i try to run it i get a fatal buffer over flow error.

```
~$ zsnes
ZSNES v1.51, (c) 1997-2007, ZSNES Team
Be sure to check http://www.zsnes.com/ for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

Starting Mouse detection.
Unable to poll /dev/input/event8. Make sure you have read permissions to it.
Unable to poll /dev/input/event7. Make sure you have read permissions to it.
Unable to poll /dev/input/event3. Make sure you have read permissions to it.
Unable to poll /dev/input/event5. Make sure you have read permissions to it.
Unable to poll /dev/input/event2. Make sure you have read permissions to it.
Unable to poll /dev/input/event0. Make sure you have read permissions to it.
Unable to poll /dev/input/event6. Make sure you have read permissions to it.
Unable to poll /dev/input/event4. Make sure you have read permissions to it.
Unable to poll /dev/input/event1. Make sure you have read permissions to it.
ManyMouse: 0 mice detected.
*** buffer overflow detected ***: zsnes terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb7c31558]
/lib/tls/i686/cmov/libc.so.6[0xb7c2f680]
zsnes[0x8056c1b]

```

what is happening?  anyone else have same problem?

```
/dev/input$ ls
by-path  event1  event3  event5  event7  mice    mouse1
event0   event2  event4  event6  event8  mouse0

```
and i already tried uninstalling and reinstalling.

---

### Post by sc3252 on 2009-01-05
bumb.  I am having the same issue.

---

### Post by DirtDawg on 2009-01-05
It looks like this is a [registered bug]("https://bugs.launchpad.net/ubuntu/+source/zsnes/+bug/250425"). Unless you are hell-bent on using Znes, I strongly recommend giving snes9x-gtk a shot. It runs smoothly and has an outstanding GUI. There are binaries (my favorite) and debs [here.]("http://www.snes9x.com/phpbb2/viewtopic.php?p=22874")

---

### Post by knowledge_is_power on 2009-01-06
done.  thanks for the alternative.

---

