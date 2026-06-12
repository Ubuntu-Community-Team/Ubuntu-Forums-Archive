---
title: "ET sound issues"
date: 2006-09-12
forum: Gaming &amp; Leisure
---

### Post by rokknroll on 2006-09-12
hi, ive previously had no problems with ET etc under Mandrake/fedora, however, my shiny new ubuntu somehow lacks Sound on et, also the volume kinda wanders up and down under normal desktop use.  The chipset on the mobo is Nvidia2, and everything seems ok in device manager, im using Alsa for the sound output, movies seem to suffer the worst.  I can post more details on request, just thought this might have an obvious solution i may have overlooked.

---

### Post by lH)4~mK0e on 2006-09-12
You will need to make sure you libsdl1.2debian package is libsdl1.2debian-all.  ET is an OSS game and the support for OSS games in native ALSA is not very good.  I had Quake 2 have absolute horrible sound but when I changed this package it corrected itself.

---

### Post by rokknroll on 2006-09-12
Thanx for the quick reply, im starting ET with : aoss et, and i get a few clicks.
Im using synaptic to change my sdl just now, i think that could be the issue-i had installed the alsa version only.
ill restart and see what happens :)

---

### Post by rokknroll on 2006-09-12
ok, no luck-just the same clicks :(
I double checked, def have the libsdl1.2debian-all package
tried aoss et
and et
same result :(  the Nvidia drivers etc are all installed and working ok(although thats really just for x?)
Should there be a different switch/flag to start et?
i have googled to no avail, but thast more likely a side effect of googles haystack and the size of this needle.
aplay -l returnd the soundcard ok
As i say, i've a feeling this is an issue with the sound generally, ive tried remedies detailed elswhere such as here: 
[http://www.ubuntuforums.org/showthread.php?t=205449](http://www.ubuntuforums.org/showthread.php?t=205449)
alas, im a bit rusty on linux troubleshooting-the volume syill wanders under normal desktop use(but that could equally well be dirt in teh volume control as a software issue...)
If anyone knows of a guide/howto for troubleshooting sound isssues i'd be very grateful, im googling frantically, but as you all know, info tends to date quickly

---

### Post by fatsheep on 2006-09-12
Try the startup script in this post, it worked for me...

[http://www.ubuntuforums.org/showthread.php?t=254397](http://www.ubuntuforums.org/showthread.php?t=254397)

---

### Post by rokknroll on 2006-09-13
Great guide, alas no luck, obviously something else amiss...
ill report back when i find out what :)

---

### Post by rokknroll on 2006-09-13
Sys_LoadDll(/home/rokknroll/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/rokknroll/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: N o such file or directory"


on closer inspection of the startup, i noticed the above...

---

