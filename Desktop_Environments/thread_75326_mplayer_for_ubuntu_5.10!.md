---
title: "mplayer for ubuntu 5.10!"
date: 2005-10-13
forum: Desktop Environments
---

### Post by taurus on 2005-10-13
It looks like mplayer won't compile out of a box for Ubuntu 5.10 because it doesn't like GCC 4!!!  ./configure only looks for GCC 3.x and when it finds GCC 4.0.x, it comes back with a message similar to "bad compiler..."  

Everyone encounters the same problem for mplayer with the latest GCC!  :(

---

### Post by FallDog on 2005-10-13
configure threw an error at me, but it compiled and make install went fine

havnt opened anything with it yet

EDIT:
opening a file resulted in error:> 
[mpeg4 @ 0x8508ba8]looks like this file was encoded with (divx4/(old)xvid/opendivx) -> forcing low_delay flag
VDec: vo config request - 320 x 240 (preferred csp: Planar YV12)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.

FATAL: Could not initialize video filters (-vf) or video output (-vo).

is that purely a codec error? or is there some additional config i need to do with my system

i have gcc 4.0.2 (w/ Ubuntu 5.10) - and to elaborate on what i said earlier, configure didnt like the compiler, but seemed to configure/make everything okay anyway

---

### Post by taurus on 2005-10-13
What version of GCC do you have on your system???

---

### Post by FallDog on 2005-10-13
See edit above, gcc version 4.0.2

---

### Post by Karasu Tengu on 2005-10-13
install the version required by mplayer then simply force the gcc version before compliling...


> su
CC=export gcc-3.*
./configure...

---

