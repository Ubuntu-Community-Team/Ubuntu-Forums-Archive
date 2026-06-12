---
title: "bad sound quality or no sound at all in Ubuntu 8.10"
date: 2008-12-24
forum: General Help
---

### Post by andresmh on 2008-12-24
After using sound in a couple of applications (i.e. Firefox, Last.fm, Rythmbox, VLC, etc) I always end up with either no sound at all (possibly caused by one of the apps taking over sound and never giving it up) or with extremely bad quality with cracking sounds at high pitch sounds.

My solution so far has been to reboot but this seems ridiculous. Any suggestions? I've tried using ALSA, OSS and Pulse and it always happens. This is my current Sound settings:

[[IMG]http://img364.imageshack.us/img364/5939/soundla1.th.png[/IMG]](http://img364.imageshack.us/my.php?image=soundla1.png)

This some info about my card:
```
$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Analog Devices AD1984A

$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfa220000 irq 17

$ lspci  | grep Audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

```

---

### Post by Zorael on 2008-12-24
Have a look at [http://ubuntuforums.org/showthread.php?p=5017453](http://ubuntuforums.org/showthread.php?p=5017453) and see if anything applies.

---

