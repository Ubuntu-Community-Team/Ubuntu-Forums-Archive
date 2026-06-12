---
title: "Quake 2 problems"
date: 2005-09-16
forum: Gaming &amp; Leisure
---

### Post by Beej on 2005-09-16
I've installed quake2 and quake2-data from synaptic, when i type "quake2" from the terminal I get the following output

I have an original Quake2 CD, but haven't done anything with that yet. Can anyone help, I'd love to get it running on my machine. 

 QuakeIIForge 0.3
using /home/ben/.quake2/baseq2/ for writing
couldn't exec default.cfg
execing config.cfg
Console initialized.

------- sound initialization -------
loading oss sound output driver, ok
/dev/dsp: Input/output error
SNDDMA_Init: Could not mmap /dev/dsp.
------- Loading ref_softx.so -------
LoadLibrary("ref_softx.so")
No joysticks found
recursive shutdown
Error: Couldn't load pics/colormap.pcx

---

### Post by kairu0 on 2005-10-15
First, it's not finding your file from the quake cd. If you've copied it into the right directory (/usr/lib/games/quake2/base2q) then make sure the filename is LOWERCASE.

Second, to fix your sound problem install libsdl1.2debian-esd (which will uninstall libsdl1.2debian-oss)

---

### Post by hammett111 on 2005-10-21
Copy the file "gamex86_64.so" or"gamex386.so" from your quake installation directory /usr/local/games/quake2 on mine to your hidden directory /.quake2/baseq3/ - should run fine now. :D

---

### Post by nasar2k2000 on 2005-10-27
[QUOTE=hammett111]Copy the file "gamex86_64.so" or"gamex386.so" from your quake installation directory /usr/local/games/quake2 on mine to your hidden directory /.quake2/baseq3/ - should run fine now. :D[/QUOTE]

i just installed quake2 using apt-get...

i tried to run it usnig the command quake2 in gnome-terminal...

it gave the same error as above...but when i entered my /usr/share/games/quake2/baseq3 folder, it was empty...

there are no *.so files in it or in the video folder...:confused:

---

### Post by kairu0 on 2005-11-05
[QUOTE=nasar2k2000]it gave the same error as above...but when i entered my /usr/share/games/quake2/baseq3 folder, it was empty...

there are no *.so files in it or in the video folder...:confused:[/QUOTE]

.so files are libraries. Have you checked /usr/lib/games/quake2/ for them?

---

### Post by dominicb on 2005-11-11
i have quake2 running, but the mouse is crappy. It works fine in the os as a whole, but in quake2 it barely responds. i get the occasional small jerk but other than that no response. the keys work fine. any ideas what's up?

---

