---
title: "mplayer problem with beryl under dapper"
date: 2006-10-31
forum: Desktop Environments
---

### Post by kecsap on 2006-10-31
Hi,

my problem is that I installed the beryl from the unofficial repo was mentioned on the wiki page of beryl and everything works fine except the mplayer and other video applications:

My video card is an integrated Intel 945GM. If I'm using the xv as output in mplayer then a "grid" appears from blue points (in full screen mode also). If I'm using the gl or gl2 as output, then the window of the mplayer flickers...

I'm using mplayer pre7 installed from repo.

Any solution?

---

### Post by ayoli on 2006-10-31
try x11 (XImage/Shm) as output driver.

---

### Post by kecsap on 2006-10-31
Sorry, I did not mention that I tried x11 (XImage/Shm) as output driver and it works, but it is not satisfactory that mplayer can not scale the movie to full screen mode. I would like to watch my movies as earlier.

---

### Post by ayoli on 2006-10-31
that's true, i cant resize either with shm driver.
btw, xv works for me. my mplayer settings are:
[LIST]
[*]xv video driver
[*]alsa audio driver
[*]Win32/VfWex for video codecs 
[*]Win32/DirectShow for audio decoders
[*]post-processing is enabled
[*]no cache
[*]autosync 0
[*]stop xscreensaver
[/LIST]
i can play in normal/fullscreen size, without problems.

---

### Post by kecsap on 2006-10-31
hmmm and what kind of videocard do you have? kernel version? are you using dapper also? the beryl is svn snapshot or the normal dapper from repo [http://ubuntu.beryl-project.org?](http://ubuntu.beryl-project.org?) glx or aiglx are there installed?

sorry for the lots of questions :)

---

### Post by ayoli on 2006-10-31
> **kecsap said:**
> hmmm and what kind of videocard do you have? kernel version? are you using dapper also? the beryl is svn snapshot or the normal dapper from repo [http://ubuntu.beryl-project.org?](http://ubuntu.beryl-project.org?) glx or aiglx are there installed? sorry for the lots of questions :)
:)
edgy kernel 2.6.17-10-generic chipset video intel i855 beryl from beerorkid's repo with aiglx (embeded in edgy's xorg).

---

### Post by kecsap on 2006-10-31
Finally, I found the problem the blue grid of point in the XV output. The default depth was only 16 bit in the xorg.conf. I changed the settings of 915resolution manually and the xorg.conf from 16 to 24 bit and voila. It's working. :) But not in full screen :))

---

### Post by kecsap on 2006-10-31
Mplayer works in full screen mode also with Xv output and it is not need to much cpu power.

Additional info:

I inserted the line dev.rtc.max-user-freq=1024 in the /etc/sysctl.conf.

Beryl settings: Lightning is unchecked, Unredirect Fullscreen Windows is unchecked, Sync to VBlank is checked, Slowness fix is unchecked.

---

