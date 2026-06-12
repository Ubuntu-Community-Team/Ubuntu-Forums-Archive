---
title: "mpg123 /321 problem when in gnome"
date: 2005-04-04
forum: Desktop Environments
---

### Post by Ric_ on 2005-04-04
Hi all, this is a little odd.

When i first installed warty this was great and there was a period in hoary that it also worked.

if i run mpg123 fromt he command line all is great. However we have a office jukebox running otto which in turn calls mpg123. But it seem to have a problem the debug states this

Playing MPEG stream from 11 - Simple_Things.mp3 ...
MPEG 1.0 layer III, 128 kbit/s, 44100 Hz joint-stereo
Can't find a suitable libao driver. (Is device in use?)

Now i have tried stopping the sound system in gnome to no avail. Has anyone seen anything simular?

---

### Post by wmcbrine on 2005-04-05
In my case I saw this on the command line. Two solutions:

1. Add the -o option, e.g., "-o alsa".

2. Edit /etc/libao.conf, e.g, to "default_driver=alsa".

---

### Post by Ric_ on 2005-04-06
Now I get this problem when I set default driver to alsa argh!

opening mpg123
No default libao driver available.
play result =

(helps if a paste the error ;) )

---

