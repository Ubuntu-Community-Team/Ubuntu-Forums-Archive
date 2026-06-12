---
title: "Quake2 and I aren't getting along."
date: 2004-12-05
forum: Gaming &amp; Leisure
---

### Post by TravisNewman on 2004-12-05
First off, it complained about not having ref_softx.so, so I checked, and sure enough, it's not there. Then I downloaded the tgz file, extracted ref_softx.so to /usr/share/games/quake2, and it works, but I get a segfault. Thus:
```

quake2
QuakeIIForge 0.3
Added packfile /usr/share/games/quake2/baseq2/pak0.pak (3307 files)
Added packfile /usr/share/games/quake2/baseq2/pak1.pak (279 files)
Added packfile /usr/share/games/quake2/baseq2/pak2.pak (2 files)
using /home/travis/.quake2/baseq2/ for writing
execing default.cfg
execing config.cfg
Console initialized.

------- sound initialization -------
loading oss sound output driver, ok
oss: buffer size is 65536, 32768 samples
sound sampling rate: 11025
------------------------------------
------- Loading ref_softx.so -------
LoadLibrary("ref_softx.so")
setting mode 3: 640 480
MITSHM shared memory (id=5537810, addr=0x403fc000)
MITSHM shared memory (id=5570579, addr=0x40528000)
1488k surface cache
ref_soft version: SOFT 0.01
------------------------------------
Segmentation fault

```

The window starts up as if it's going to work, but once it segfaults, obviously it stops.

Anyone have any luck getting this going?

---

### Post by yusufk on 2005-03-30
Having the same problem(S) on Hoary, any luck since then?

---

### Post by sander marechal on 2005-03-31
Quakre2 for Ubuntu is compiled with SDL support. Instead of the ref_softx.so, try this command:

quake2 +set vid_ref softsdl

---

### Post by yusufk on 2005-04-01
Yep, came up with the same conclusion:
See [http://ubuntuforums.org/showthread.php?t=22920](http://ubuntuforums.org/showthread.php?t=22920)

Thanks
y

---

### Post by Zandor on 2005-04-04
Hi

Take the missing .so files from the debian woody package.
[http://packages.debian.org/stable/games/quake2](http://packages.debian.org/stable/games/quake2)

Download the deb, extract it with file-roller and copy
ref_glx.so
ref_sdlgl.so
ref_softx.so
to /usr/lib/games/quake2/. Then start the game with "quake2 +set vid_ref glx". Should work for Warty and Hoary since the version of the package hasn't changed.

---

### Post by tont on 2005-04-29
tont@laf:~$ quake2 +set vid_ref glx
-> Red  1.000, Green  1.000, Blue  1.000
<- Red  1.300, Green  1.300, Blue  1.300
Quake 2 -- Version 3.21+r0.16
Added packfile ./baseq2/pak10.pak (806 files)
Added packfile ./baseq2/pak11.pak (47 files)
Added packfile ./baseq2/pak12.pak (79 files)
Added packfile ./baseq2/pak13.pak (16 files)
Added packfile ./baseq2/pak14.pak (46 files)
Added packfile ./baseq2/pak16.pak (30 files)
Added packfile ./baseq2/pak17.pak (22 files)
Added packfile ./baseq2/pak19.pak (13 files)
Added packfile ./baseq2/maxpak.pak (40 files)
using /home/tont/.quake2/baseq2/ for writing
couldn't exec default.cfg
execing config.cfg
Console initialized.

------- sound initialization -------
Couldn't open SDL audio: No available audio device
------- Loading ref_glx.so -------
LoadLibrary("./ref_glx.so")
No joysticks found
ref_gl version: GL 0.01
recursive shutdown
Error: Couldn't load pics/colormap.pcx
-> Red  1.300, Green  1.300, Blue  1.300
<- Red  1.000, Green  1.000, Blue  1.000
tont@laf:~$

how do you make it to execute oss ?

---

### Post by Zandor on 2005-04-30
There's an option for setting the sound device in the config.cfg file. In my config its 'set snddevice "/dev/dsp"', without the single quotes. Maybe there's something wrong with this entry.

Another possibility I see is that the oss sdl aren't installed (package libsdl1.2debian-oss).

Hope this helps...

---

### Post by samjam on 2005-05-06
[QUOTE=Zandor]Hi

Take the missing .so files from the debian woody package.
[http://packages.debian.org/stable/games/quake2](http://packages.debian.org/stable/games/quake2)

Download the deb, extract it with file-roller and copy
ref_glx.so
ref_sdlgl.so
ref_softx.so
to /usr/lib/games/quake2/. Then start the game with "quake2 +set vid_ref glx". Should work for Warty and Hoary since the version of the package hasn't changed.[/QUOTE]

Or why not just rebuild locally from source?
sudo apt-get -b source quake2

Make Sure to install libxxf86vm-dev, libxxf86dga-dev and other dev libraries for the output modes you want, otherwise the compile fails all over the place because HAVE_XF86_VIDMODE is not defined (hey - I'm using x.org) and lots of warnings about variables not being used pop-up all over the place.  

But wait, that doesn't work because ./configure links against the wrong library when doing its tests, and somehow adds _pic onto the library name (dumb brute) 

[config.log]
configure:20919: checking for XF86VidModeSwitchToMode in -lXxf86vm_pic
configure:20950: gcc -o conftest -O2   -I/usr/X11R6/include  conftest.c -lXxf86vm_pic  -L/usr/X11R6/lib -lX11 -lXext
                          >&5
/usr/bin/ld: cannot find -lXxf86vm_pic


is this really the right source?
autoreconf fails badly, autoconf takes exception to configure.in, so in the end I edited configure to remove _pic of library names of lines that matched LIB.*_pic

etc, and then try again, luckily apt-get -b carries on from where it left off.

Finally I end up with quake2 with glx and all the other drivers, Why ubunto folk didn't do this beats me, why the source won't possibly compile in its current state beats me.

I have to say that redhat with their ENFORCED "pristine sources" beat debian here, with redhat it is nigh impossible to produce a binary package by fiddling with the build dir, and therefore impossible to produce a binary package without being certain it was produced from the source package. 

[gosh that was too much hard work] How can it be impossible to build a deb from the source?]

But I got all my ref_glx.* and friends at last!

wow!

Now I just got to work out why OSS sound has 1 second gaps for every second of sound and why ALSA sounds jittery like mad. My asoundrc is has

pcm.dsp0 {      # route OSS software through pcm.amix
        type plug
        slave.pcm "dmixer"
}
pcm.dmixer {
type dmix
ipc_key 1025
slave {
pcm "hw:0,0"
#period_time 32768
period_time 0
period_size 4096
buffer_size 32768
rate 48000
}
bindings {
0 0
1 1
}
}
 
in it

Sam

Sam

---

### Post by manny on 2005-05-18
Thank you Zandor! working great :)

---

