---
title: "Compiz doesn't work on Natty"
date: 2011-05-25
forum: Desktop Environments
---

### Post by Uvoguine on 2011-05-25
Hi,

I just insatlled Ubuntu 11.04 64 bits and I've got one big problem. In fact, I tried to install Emerald and it crashed immediatly. Since that I can not have any effects on my computer. I tried ```
compiz --replace
``` but nothing happened really. I just have a lot of errors I don't understand.

```
Backend     : gconf
Integration : true
Profile     : default
Adding plugins
Initializing core options...done
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing wobbly options...done
Initializing animation options...done
Initializing cube options...done
Initializing rotate options...done
Initializing animationaddon options...done
Initializing gnomecompat options...done
Initializing obs options...done
Initializing scale options...done
Initializing td options...done
*** glibc detected *** compiz: corrupted double-linked list: 0x0000000000897190 ***
======= Backtrace: =========
/lib/x86_64-linux-gnu/libc.so.6(+0x77fb1)[0x7fc8a5bf9fb1]
/lib/x86_64-linux-gnu/libc.so.6(+0x78528)[0x7fc8a5bfa528]
/lib/x86_64-linux-gnu/libc.so.6(cfree+0x73)[0x7fc8a5bfe8e3]
/usr/lib/nvidia-current/libnvidia-glcore.so.270.41.06(+0xd2e873)[0x7fc89b0e1873]
/usr/lib/nvidia-current/libnvidia-glcore.so.270.41.06(+0xf1190d)[0x7fc89b2c490d]
/usr/lib/nvidia-current/libnvidia-glcore.so.270.41.06(+0x10c7030)[0x7fc89b47a030]
/usr/lib/nvidia-current/libnvidia-glcore.so.270.41.06(+0xf18cb2)[0x7fc89b2cbcb2]
/usr/lib/nvidia-current/libnvidia-glcore.so.270.41.06(+0xf1a048)[0x7fc89b2cd048]
/usr/lib/nvidia-current/libnvidia-glcore.so.270.41.06(+0xee89ed)[0x7fc89b29b9ed]
/usr/lib/nvidia-current/libGL.so.1(+0x7de22)[0x7fc8a1db1e22]
======= Memory map: ========
00400000-0046f000 r-xp 00000000 08:01 15204534                           /usr/bin/compiz
0066e000-0066f000 r--p 0006e000 08:01 15204534                           /usr/bin/compiz
0066f000-00670000 rw-p 0006f000 08:01 15204534                           /usr/bin/compiz
00670000-00671000 rw-p 00000000 00:00 0 
00688000-008ec000 rw-p 00000000 00:00 0                                  [heap]
7fc899d50000-7fc899d65000 r-xp 00000000 08:01 15207964                   /usr/lib/compiz/libtd.so
7fc899d65000-7fc899f65000 ---p 00015000 08:01 15207964                   /usr/lib/compiz/libtd.so
7fc899f65000-7fc899f66000 r--p 00015000 08:01 15207964                   /usr/lib/compiz/libtd.so
7fc899f66000-7fc899f67000 rw-p 00016000 08:01 15207964                   /usr/lib/compiz/libtd.so
7fc899f67000-7fc899f8a000 r-xp 00000000 08:01 15209504                   /usr/lib/compiz/libscale.so
7fc899f8a000-7fc89a18a000 ---p 00023000 08:01 15209504                   /usr/lib/compiz/libscale.so
7fc89a18a000-7fc89a18c000 r--p 00023000 08:01 15209504                   /usr/lib/compiz/libscale.so
7fc89a18c000-7fc89a18d000 rw-p 00025000 08:01 15209504                   /usr/lib/compiz/libscale.so
7fc89a18d000-7fc89a1b1000 r-xp 00000000 08:01 15209492                   /usr/lib/compiz/libobs.so
7fc89a1b1000-7fc89a3b0000 ---p 00024000 08:01 15209492                   /usr/lib/compiz/libobs.so
7fc89a3b0000-7fc89a3b2000 r--p 00023000 08:01 15209492                   /usr/lib/compiz/libobs.so
7fc89a3b2000-7fc89a3b3000 rw-p 00025000 08:01 15209492                   /usr/lib/compiz/libobs.so
7fc89a3b3000-7fc89b801000 r-xp 00000000 08:01 17174223                   /usr/lib/nvidia-current/libnvidia-glcore.so.270.41.06
7fc89b801000-7fc89ba01000 ---p 0144e000 08:01 17174223                   /usr/lib/nvidia-current/libnvidia-glcore.so.270.41.06
7fc89ba01000-7fc89bfe9000 rwxp 0144e000 08:01 17174223                   /usr/lib/nvidia-current/libnvidia-glcore.so.270.41.06
7fc89bfe9000-7fc89c000000 rwxp 00000000 00:00 0 
7fc89c000000-7fc89c021000 rw-p 00000000 00:00 0 
7fc89c021000-7fc8a0000000 ---p 00000000 00:00 0 
7fc8a00be000-7fc8a00c8000 r-xp 00000000 08:01 15209482                   /usr/lib/compiz/libgnomecompat.so
7fc8a00c8000-7fc8a02c8000 ---p 0000a000 08:01 15209482                   /usr/lib/compiz/libgnomecompat.so
7fc8a02c8000-7fc8a02c9000 r--p 0000a000 08:01 15209482                   /usr/lib/compiz/libgnomecompat.so
7fc8a02c9000-7fc8a02ca000 rw-p 0000b000 08:01 15209482                   /usr/lib/compiz/libgnomecompat.so
7fc8a02ca000-7fc8a030f000 r-xp 00000000 08:01 15205169                   /usr/lib/compiz/libanimationaddon.so
7fc8a030f000-7fc8a050e000 ---p 00045000 08:01 15205169                   /usr/lib/compiz/libanimationaddon.so
7fc8a050e000-7fc8a0516000 r--p 00044000 08:01 15205169                   /usr/lib/compiz/libanimationaddon.so
7fc8a0516000-7fc8a0517000 rw-p 0004c000 08:01 15205169                   /usr/lib/compiz/libanimationaddon.so
7fc8a0517000-7fc8a053a000 r-xp 00000000 08:01 15209502                   /usr/lib/compiz/librotate.so
7fc8a053a000-7fc8a073a000 ---p 00023000 08:01 15209502                   /usr/lib/compiz/librotate.so
7fc8a073a000-7fc8a073b000 r--p 00023000 08:01 15209502                   /usr/lib/compiz/librotate.so
7fc8a073b000-7fc8a073c000 rw-p 00024000 08:01 15209502                   /usr/lib/compiz/librotate.so
7fc8a073c000-7fc8a0758000 r-xp 00000000 08:01 15209476                   /usr/lib/compiz/libcube.so
7fc8a0758000-7fc8a0958000 ---p 0001c000 08:01 15209476                   /usr/lib/compiz/libcube.so
7fc8a0958000-7fc8a0959000 r--p 0001c000 08:01 15209476                   /usr/lib/compiz/libcube.so
7fc8a0959000-7fc8a095a000 rw-p 0001d000 08:01 15209476                   /usr/lib/compiz/libcube.so
7fc8a095a000-7fc8a09c7000 r-xp 00000000 08:01 15207974                   /usr/lib/libGLU.so.1.3.071000
7fc8a09c7000-7fc8a0bc6000 ---p 0006d000 08:01 15207974                   /usr/lib/libGLU.so.1.3.071000
7fc8a0bc6000-7fc8a0bc8000 r--p 0006c000 08:01 15207974                   /usr/lib/libGLU.so.1.3.071000
7fc8a0bc8000-7fc8a0bc9000 rw-p 0006e000 08:01 15207974                   /usr/lib/libGLU.so.1.3.071000
7fc8a0bc9000-7fc8a0c39000 r-xp 00000000 08:01 15209468                   /usr/lib/compiz/libanimation.so
7fc8a0c39000-7fc8a0e39000 ---p 00070000 08:01 15209468                   /usr/lib/compiz/libanimation.so
7fc8a0e39000-7fc8a0e48000 r--p 00070000 08:01 15209468                   /usr/lib/compiz/libanimation.so
7fc8a0e48000-7fc8a0e49000 rw-p 0007f000 08:01 15209468                   /usr/lib/compiz/libanimation.so
7fc8a0e49000-7fc8a0e51000 r-xp 00000000 08:01 15209499                   /usr/lib/compiz/libregex.so
7fc8a0e51000-7fc8a1051000 ---p 00008000 08:01 15209499                   /usr/lib/compiz/libregex.so
7fc8a1051000-7fc8a1052000 r--p 00008000 08:01 15209499                   /usr/lib/compiz/libregex.so
7fc8a1052000-7fc8a1053000 rw-p 00009000 08:01 15209499                   /usr/lib/compiz/libregex.so
7fc8a1053000-7fc8a106f000 r-xp 00000000 08:01 15209511                   /usr/lib/compiz/libwobbly.so
7fc8a106f000-7fc8a126f000 ---p 0001c000 08:01 15209511                   /usr/lib/compiz/libwobbly.so
7fc8a126f000-7fc8a1270000 r--p 0001c000 08:01 15209511                   /usr/lib/compiz/libwobbly.so
7fc8a1270000-7fc8a1271000 rw-p 0001d000 08:01 15209511                   /usr/lib/compiz/libwobbly.so
7fc8a1271000-7fc8a1279000 r-xp 00000000 08:01 15208155                   /usr/lib/libdecoration.so.0.0.0
7fc8a1279000-7fc8a1478000 ---p 00008000 08:01 15208155                   /usr/lib/libdecoration.so.0.0.0Abandon

```I don't know what to do. If someone can help me I'll be grateful.


( I'm sorry for my bad bad english )

---

### Post by Krytarik on 2011-05-25
The current Emerald package in the official repos of Natty doesn't work with the current version of Compiz.
But you could try to compile it yourself:
[http://abz89.wordpress.com/2011/05/02/how-to-fix-emerald-in-ubuntu-11-04/](http://abz89.wordpress.com/2011/05/02/how-to-fix-emerald-in-ubuntu-11-04/)

Or you log in to "Ubuntu Classic (No effects)" and make sure that the setting "CompizConfig Settings Manager -> Window Decoration -> Command" is set to "/usr/bin/compiz-decorator", in both profiles, "Default" and "Unity", in "Preferences" at the lower left.

Greetings.

---

### Post by Uvoguine on 2011-05-25
Ahah awesome ! It's work ! I put " metacity --replace " in this field 'cause I could not remember what was there.

But now I've got an other problem. I can't move any window because a long click on the title bar doesn't do anything. Even in pressing Alt I can't move it.


I found the solution ! I just forgot to activated " Move windows " in Compiz !

Thanks a lot !

---

