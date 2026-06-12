---
title: "GlPortal Install help"
date: 2014-10-17
forum: Gaming &amp; Leisure
---

### Post by rdmike on 2014-10-17
Hi all,

Saw this game online called GlPortal and thought it might be something my son and I could play together. Went to the website ([http://glportal.de/](http://glportal.de/)) and downloaded the file(s), gave permission for it to be executable but nothing happens. I looked at the readme and it confused me lol. Hate to sound dumb but it did. Anyhoo, would one of y'all be willing to have a look and maybe walk me through the install process?

I am running LXLE (32 bit).

Thanks! :-)

---

### Post by R33D3M33R on 2014-10-17
After extracting open terminal, change directory to the folder where the game is and type:

```
ldd portal
```

You might see lines containing  **=> not found**. You have to install these libraries for the game to work.

---

### Post by rdmike on 2014-10-17
First of all thank you very much for your reply and assistance. :-)

Ok, so I went into the terminal, used CD to get to the GlPortal-v0.0.7.1-frogger folder inside the dDownlaods directory and ran the ldd portal command you suggested in the terminal. Here is the output;

> ~/Downloads/GlPortal-v0.0.7.1-frogger$ ldd portal
	linux-gate.so.1 =>  (0x00843000)
	libGL.so.1 => /usr/lib/i386-linux-gnu/mesa/libGL.so.1 (0x00b76000)
	libGLU.so.1 => /usr/lib/i386-linux-gnu/libGLU.so.1 (0x00110000)
	libassimp.so.3 => not found
	libSDL2-2.0.so.0 => not found
	libSDL2_mixer-2.0.so.0 => not found
	libstdc++.so.6 => /usr/lib/i386-linux-gnu/libstdc++.so.6 (0x00393000)
	libm.so.6 => /lib/i386-linux-gnu/libm.so.6 (0x001f7000)
	libgcc_s.so.1 => /lib/i386-linux-gnu/libgcc_s.so.1 (0x00c2f000)
	libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0x004a6000)
	libpthread.so.0 => /lib/i386-linux-gnu/libpthread.so.0 (0x00ef2000)
	libglapi.so.0 => /usr/lib/i386-linux-gnu/libglapi.so.0 (0x00d72000)
	libXext.so.6 => /usr/lib/i386-linux-gnu/libXext.so.6 (0x00185000)
	libXdamage.so.1 => /usr/lib/i386-linux-gnu/libXdamage.so.1 (0x0087a000)
	libXfixes.so.3 => /usr/lib/i386-linux-gnu/libXfixes.so.3 (0x00964000)
	libX11-xcb.so.1 => /usr/lib/i386-linux-gnu/libX11-xcb.so.1 (0x00197000)
	libX11.so.6 => /usr/lib/i386-linux-gnu/libX11.so.6 (0x00223000)
	libxcb-glx.so.0 => /usr/lib/i386-linux-gnu/libxcb-glx.so.0 (0x00769000)
	libxcb.so.1 => /usr/lib/i386-linux-gnu/libxcb.so.1 (0x006f7000)
	libXxf86vm.so.1 => /usr/lib/i386-linux-gnu/libXxf86vm.so.1 (0x008b8000)
	libdrm.so.2 => /usr/lib/i386-linux-gnu/libdrm.so.2 (0x0019a000)
	libdl.so.2 => /lib/i386-linux-gnu/libdl.so.2 (0x001a7000)
	/lib/ld-linux.so.2 (0x00659000)
	libXau.so.6 => /usr/lib/i386-linux-gnu/libXau.so.6 (0x001ac000)
	libXdmcp.so.6 => /usr/lib/i386-linux-gnu/libXdmcp.so.6 (0x00f2c000)
	librt.so.1 => /lib/i386-linux-gnu/librt.so.1 (0x001b0000)

Again, I hate to sound totally ignorant of the terminal and software installs via linux but what packages will I need to install based on this output?

---

### Post by R33D3M33R on 2014-10-17
It looks like you need: libassimp3, libsdl2-2.0-0 and libsdl2-mixer-2.0-0. These packages exist in official ubuntu repository and are probably also available for LXLE. Install with package manager or console:

```
sudo apt-get install libassimp3 libsdl2-2.0-0 libsdl2-mixer-2.0-0
```

---

### Post by rdmike on 2014-10-17
Ok well neither the terminal nor synaptic was able to install these files. I assume the right repository isn't enabled or perhaps supported in LXLE? I ran a request in terminal for software sources list with this result.

> $ cat /etc/apt/sources.list

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-proposed restricted main multiverse universe
# deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main

Not sure where to go from here...

---

### Post by dannyboy79 on 2014-10-18
can you be more specific when you say both the terminal nor synaptic were able to install them because when I issue 
```
sudo aptitude search libassimp3 libsdl2-2.0-0 libsdl2-mixer-2.0-0
```
it returns
```
p   libassimp3                                                                   - 3D model import library                                                               
p   libassimp3:i386                                                              - 3D model import library                                                               
p   libsdl2-2.0-0                                                                - Simple DirectMedia Layer                                                              
p   libsdl2-2.0-0:i386                                                           - Simple DirectMedia Layer                                                              
p   libsdl2-mixer-2.0-0                                                          - Mixer library for Simple DirectMedia Layer 2, libraries                               
p   libsdl2-mixer-2.0-0:i386                                                     - Mixer library for Simple DirectMedia Layer 2, libraries       
```
sometimes libraries are named slightly different, what you want to try to do is break the name of the package down to as small of search string as possible to find the most results. So if something says that libassimp.so.3 is missing I would use synaptic, ubuntu software center, aptitude and apt-get to search for a string like "ibassimp"  and then go from there.

---

### Post by rdmike on 2014-10-18
When I try the apt search command I get zero results. So, I tried synaptic again using your suggestion and removing the 3 from libassimp3. This is the result I got from that query.

[IMG]http://imageshack.com/a/img911/4529/eNZPy3.png[/IMG]

Will one of these work?

---

### Post by R33D3M33R on 2014-10-18
Probably not. From your sources.list it's evident that your distro is using Ubuntu 12.04 as its base, so the packages are outdated. Until LXLE catches up with Ubuntu 14.04, you will probably not be able to play the game.

---

### Post by rdmike on 2014-10-18
Ok I see. Well, I appreciate your efforts in trying to make this work. :-)

---

### Post by CatKiller on 2014-10-24
> **R33D3M33R said:**
> Probably not. From your sources.list it's evident that your distro is using Ubuntu 12.04 as its base, so the packages are outdated. Until LXLE catches up with Ubuntu 14.04, you will probably not be able to play the game.

They have, but the OP hasn't, it seems to me. Although they could probably upgrade.

---

