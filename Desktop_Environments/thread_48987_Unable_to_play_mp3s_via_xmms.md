---
title: "Unable to play mp3s via xmms"
date: 2005-07-14
forum: Desktop Environments
---

### Post by eriktown on 2005-07-14
I can't get xmms to play mp3s. When I try to, I get the following errors:

(This error occurs when I first start xmms)

$ /usr/bin/xmms
libmikmod.so.2: cannot open shared object file: No such file or directory

(Then when I actually try to play an mp3, I get the following error)

** WARNING **: alsa_setup(): Failed to open pcm device (default): Device or resource busy

Anyone know what might be wrong? I'm running Ubuntu 5.04 and have xmms configured to us ALSA.  (I'm able to listen to CDs and hear normal system sounds from GNOME just fine.)  I'm running on an HP Pavilion Dv1049cl with the Intel 8280 (Centrino) chipset.

Thanks!

---

### Post by phen on 2005-07-14
in xmms preferences:
try using esound plugin  (libesd) this works for me!

kai

---

### Post by badrinarayan on 2005-07-14
See the output of
```

badri@codebox:~$ **sudo dpkg -S libmikmod.so.2**
libmikmod2: /usr/lib/libmikmod.so.2
libmikmod2: /usr/lib/libmikmod.so.2.0.4
badri@codebox:~$

```

If you get anything else, then you don't have libmikmod2. Install it

```

sudo apt-get install libmikmod2

```

Also see [http://www.ubuntuguide.org/#configuresoundproperly](http://www.ubuntuguide.org/#configuresoundproperly)

Regards
Badri

---

### Post by eriktown on 2005-07-14
Thanks to both with you -- using the other plugin worked (I wonder why the ALSA plugin doesn't?) and I was able to install libmikmod2. I tried to install it before but didn't have the right repository configured.

---

### Post by nomad311 on 2005-07-26
hey will one of you tell me how you got the esd lib to work with xmms ...its not on my list and i dont see a esd package for xmms with synaptic.

...i found one for vlc though ...which i havent tried out yet cause i have to killall esd for alsa/oss ...to work in xmms

to eriktown (im not an expart but this is how i underatnd it works):
alsa/oss/esd/arts and all sound engines and X can only use one at a time
esd and arts allow multiple programs to access it so you can listen to music and still hear system sounds
but alsa and oss only allow one at a time ...so if your playin music nothing else can use the sound engine
this is why i wanna use esd ...but the lib in the unofficial guide wont show up for me ...and ive checked all the repositories even added the one form the non-free section of the wiki!
-so id like to know what repository or whatever i need to do to get xmms to work on esd ...then i can put esd back in the startup and be happy again HA

...ubuntu comes setup on esd so unless you know what your doin you shoud proly js try to install/use everything with esd

-nomad311

---

### Post by nomad311 on 2005-07-27
id like to retract my last post ...its not that i didnt read the guide and try to follow the directions ...its that i have a problem
...i didnt read the names of the plugins in xmms and even after editing /etc/esound/esd ...i didnt realize that to use the esd in xmms it was the eSound option

...so yeh im kinda slow

-nomad311

---

