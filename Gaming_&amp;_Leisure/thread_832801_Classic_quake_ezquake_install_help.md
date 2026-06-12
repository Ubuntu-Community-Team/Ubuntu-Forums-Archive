---
title: "Classic quake ezquake install help"
date: 2008-06-18
forum: Gaming &amp; Leisure
---

### Post by homerhomer on 2008-06-18
I finally got old school quake up and working. Here's some install tips that might help





---------- Crappy Sound ------- Blame it on ALSA
If you should is real choppy edit the config file and under //Sound Settings add s_alsa and edit s_device and s_khz

gedit ~/.ezquake/config.cfg

set s_noalsa			"1"
s_device                       "/dev/dsp"
s_khz                          "48"

or you can run ezquake like this 
./ezquake-gl.glx +set s_noalsa 1 +set s_device /dev/dsp +set s_khz 48





---------- Startup complains about libXxf86dga.so.1 file when loading
I was having this issue because I was running amd64 (64bit) and ezquake was compiled for 32bit.

Get this program  ([http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790))
[http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb](http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb)

and install the 32bit library ***  I didn't this as non-superuser / not root
getlibs -l libXxf86dga.so.1






---------- Error: Couldn't load gfx/palette.lmp on startup
This error is because you need to copy the pak0.pak from you full or shareware quake version. 
[http://www.mediafire.com/?9m3qyq3e9nu](http://www.mediafire.com/?9m3qyq3e9nu) (shareware version)

you can use doxbox or copy them from a windows install

---

