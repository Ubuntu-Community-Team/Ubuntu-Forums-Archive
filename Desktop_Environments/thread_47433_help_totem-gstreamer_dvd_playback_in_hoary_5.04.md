---
title: "help totem-gstreamer dvd playback in hoary 5.04"
date: 2005-07-08
forum: Desktop Environments
---

### Post by stanwebber on 2005-07-08
i want to play non-encrypted non-region coded dvds using gstreamer with the totem frontend, but am having no success.  i have the following packages installed:

gstreamer0.8-alsa
                     -audiofile
                     -cdparanoia
                     -dv
                     -dvd
                     -esd
                     -flac
                     -gnomevfs
                     -gsm
                     -hermes
                     -jpeg
                     -misc
                     -mpeg2dec
                     -oss
                     -plugin-apps
                     -sdl
                     -sid
                     -speex
                     -theora
                     -tools
                     -vorbis
                     -x
libgstreamer0.8-0
libgstreamer-gconf0.8-0
                   -plugins0.8-0
totem-gstreamer

what am i missing?  whenever i insert a dvd totem autostarts & displays the following error message:  *Totem could not play 'dvd://'.  cannot open file "dvd://"*

i am not interested in using any other media player besides gstreamer; however, i will replace totem as frontend if it turns out to be the source of the problem.  i really want gstreamer to work--it should work.  i am NOT trying to play css encrypted or region-coded dvds or anything complex.  i must be missing an installed package or something equally simple

thanks for any help you can offer

---

### Post by Lunde on 2005-07-08
[QUOTE=stanwebber]i want to play non-encrypted non-region coded dvds using gstreamer with the totem frontend, but am having no success.  i have the following packages installed:

gstreamer0.8-alsa
                     -audiofile
                     -cdparanoia
                     -dv
                     -dvd
                     -esd
                     -flac
                     -gnomevfs
                     -gsm
                     -hermes
                     -jpeg
                     -misc
                     -mpeg2dec
                     -oss
                     -plugin-apps
                     -sdl
                     -sid
                     -speex
                     -theora
                     -tools
                     -vorbis
                     -x
libgstreamer0.8-0
libgstreamer-gconf0.8-0
                   -plugins0.8-0
totem-gstreamer

what am i missing?  whenever i insert a dvd totem autostarts & displays the following error message:  *Totem could not play 'dvd://'.  cannot open file "dvd://"*

i am not interested in using any other media player besides gstreamer; however, i will replace totem as frontend if it turns out to be the source of the problem.  i really want gstreamer to work--it should work.  i am NOT trying to play css encrypted or region-coded dvds or anything complex.  i must be missing an installed package or something equally simple

thanks for any help you can offer[/QUOTE]
 you need libdvdcss2

That was the only extra I needed

---

### Post by stanwebber on 2005-07-08
let me re-state:  i am not interested in playing encrypted dvds on my linux box, now or ever

---

### Post by Lunde on 2005-07-08
[QUOTE=stanwebber]let me re-state:  i am not interested in playing encrypted dvds on my linux box, now or ever[/QUOTE]
 When you install this, if I don't remember completly wrong. It also installs: libdvdread3 so you are able to view all dvd's after.

But sorry, maybe you only need the** libdvdread3**

---

