---
title: "zsnes glibc detected malloc() memory corruption?!"
date: 2006-11-08
forum: Gaming &amp; Leisure
---

### Post by play0r on 2006-11-08
it seems after doing a clean install with edgy, zsnes no longer functions properly on my system. 
occasionally it will load just fine & play games with no problem at all (usually after i've installed a new version during this saga). although, most of the time it will crash (output below) when using the load option in the gui, sometimes it'll just crash when i go to open it (same error output as before as far as i can tell). 
i've tried installing it from the source, svn (which was 1.43 instead of 1.42), the current repo, & other 1.42 deb's, which all crash with the same symptoms previously described & yielding the same output.
please try & sort me out with a solution, because it seems to be beyond me. ](*,) 
i don't want to downgrade to dapper just to play zsnes, but if i have to i will. :cry:

> 
*** glibc detected *** zsnes: malloc(): memory corruption: 0x08602820 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7bb81cd]
/lib/tls/i686/cmov/libc.so.6(malloc+0x7f)[0xb7bb983f]
/lib/tls/i686/cmov/libc.so.6[0xb7bdb673]
/lib/tls/i686/cmov/libc.so.6(opendir+0x63)[0xb7bdb753]
/lib/tls/i686/cmov/libc.so.6[0xb7be2d79]
/lib/tls/i686/cmov/libc.so.6(glob+0x79b)[0xb7be373b]
zsnes[0x80de65a]
======= Memory map: ========
08048000-082fa000 r-xp 00000000 03:03 10715      /usr/bin/zsnes
082fa000-0834d000 rwxp 002b1000 03:03 10715      /usr/bin/zsnes
0834d000-0861c000 rwxp 0834d000 00:00 0          [heap]
b5300000-b5321000 rwxp b5300000 00:00 0 
b5321000-b5400000 ---p b5321000 00:00 0 
b548f000-b5490000 ---p b548f000 00:00 0 
b5490000-b5c90000 rwxp b5490000 00:00 0 
b5c90000-b5cb0000 rwxs 00000000 00:08 79659023   /SYSV0056a4d6 (deleted)
b5cb0000-b5cc0000 rwxs 00000000 00:0d 7322       /dev/snd/pcmC0D0p
b5cc0000-b5cc9000 r-xp 00000000 03:03 119111     /lib/tls/i686/cmov/libnss_files-2.4.so
b5cc9000-b5ccb000 rwxp 00008000 03:03 119111     /lib/tls/i686/cmov/libnss_files-2.4.so
b5ccb000-b5cd3000 r-xp 00000000 03:03 119117     /lib/tls/i686/cmov/libnss_nis-2.4.so
b5cd3000-b5cd5000 rwxp 00007000 03:03 119117     /lib/tls/i686/cmov/libnss_nis-2.4.so
b5cd5000-b5ce7000 r-xp 00000000 03:03 118841     /lib/tls/i686/cmov/libnsl-2.4.so
b5ce7000-b5ce9000 rwxp 00011000 03:03 118841     /lib/tls/i686/cmov/libnsl-2.4.so
b5ce9000-b5ceb000 rwxp b5ce9000 00:00 0 
b5ceb000-b5cf2000 r-xp 00000000 03:03 118842     /lib/tls/i686/cmov/libnss_compat-2.4.so
b5cf2000-b5cf4000 rwxp 00006000 03:03 118842     /lib/tls/i686/cmov/libnss_compat-2.4.so
b5cf4000-b5cf5000 r-xp 00000000 03:03 120610     /usr/lib/gconv/ISO8859-1.so
b5cf5000-b5cf7000 rwxp 00001000 03:03 120610     /usr/lib/gconv/ISO8859-1.so
b5cf7000-b5cfe000 r-xs 00000000 03:03 4961       /usr/lib/gconv/gconv-modules.cache
b5cfe000-b5d6f000 rwxp b5cfe000 00:00 0 
b5d6f000-b5e4f000 rwxs 00000000 00:08 79560715   /SYSV00000000 (deleted)
b5e4f000-b5e53000 r-xp 00000000 03:03 20383      /usr/lib/libXfixes.so.3.1.0
b5e53000-b5e54000 rwxp 00003000 03:03 20383      /usr/lib/libXfixes.so.3.1.0
b5e54000-b5e5c000 r-xp 00000000 03:03 21606      /usr/lib/libXcursor.so.1.0.2
b5e5c000-b5e5d000 rwxp 00007000 03:03 21606      /usr/lib/libXcursor.so.1.0.2
b5e6a000-b5e6b000 rwxs 81000000 00:0d 7322       /dev/snd/pcmC0D0p
b5e6b000-b5e87000 r-xp 00000000 03:03 20333      /usr/lib/X11/locale/common/ximcp.so.2.0.0
b5e87000-b5e89000 rwxp 0001b000 03:03 20333      /usr/lib/X11/locale/common/ximcp.so.2.0.0
b5e89000-b5e8e000 r-xp 00000000 03:03 20336      /usr/lib/X11/locale/common/xlibi18n.so.2.0.0
b5e8e000-b5e8f000 rwxp 00004000 03:03 20336      /usr/lib/X11/locale/common/xlibi18n.so.2.0.0
b5e8f000-b5e90000 ---p b5e8f000 00:00 0 
b5e90000-b7949000 rwxp b5e90000 00:00 0 
b7949000-b794d000 r-xp 00000000 03:03 20074      /usr/lib/libXdmcp.so.6.0.0
b794d000-b794e000 rwxp 00003000 03:03 20074      /usr/lib/libXdmcp.so.6.0.0
b794e000-b7950000 r-xp 00000000 03:03 20061      /usr/lib/libXau.so.6.0.0
b7950000-b7951000 rwxp 00001000 03:03 20061      /usr/lib/libXau.so.6.0.0
b7951000-b7952000 rwxp b7951000 00:00 0 
b7952000-b7958000 r-xp 00000000 03:03 20838      /usr/lib/libdrm.so.2.0.0
b7958000-b7959000 rwxp 00005000 03:03 20838      /usr/lib/libdrm.so.2.0.0
b7959000-b795d000 r-xp 00000000 03:03 21208      /usr/lib/libXxf86vm.so.1.0.0
b795d000-b795e000 rwxp 00003000 03:03 21208      /usr/lib/libXxf86vm.so.1.0.0
b795e000-b796a000 r-xp 00000000 03:03 20357      /usr/lib/libXext.so.6.4.0
b796a000-b796b000 rwxp 0000c000 03:03 20357      /usr/lib/libXext.so.6.4.0
b796b000-b7a31000 r-xp 00000000 03:03 20330      /usr/lib/libX11.so.6.2.0
b7a31000-b7a34000 rwxp 000c5000 03:03 20330      /usr/lib/libX11.so.6.2.0
b7a34000-b7a36000 r-xp 00000000 03:03 118672     /lib/tls/i686/cmov/libdl-2.4.so
b7a36000-b7a38000 rwxp 00001000 03:03 118672     /lib/tls/i686/cmov/libdl-2.4.so
b7a38000-b7a44000 r-xp 00000000 03:03 41951      /usr/lib/libdirect-0.9.so.24.0.0
b7a44000-b7a45000 rwxp 0000c000 03:03 41951      /usr/lib/libdirect-0.9.so.24.0.0
b7a450Aborted (core dumped)


---

### Post by play0r on 2006-11-10
okay, so i found something odd happening. 
when i deleted /home/username/.zsnes after having a segmentation fault, i could resume using zsnes like normal (until the next segmentation fault of course). :confused: 
if anyone has any info on why that would help the situation? it'd be much appreciated, because i'm more than just a little confused with this whole thing.

---

### Post by play0r on 2006-11-10
okay, i think i finally have a resolution here.
if i **don't** uncheck enable sound & enable stereo, but i have the volume control at 0% (i like to listen to music while i play snes) i no longer receive errors about memory corruption or segmentation faults.
can someone please enlightening me on **why** this happened? 
is it some hang-up between sdl & alsa? 
is it a bug that should be filed or an unique occurrence? :confused: 
thanks in advance for any comments.

---

### Post by slimdog360 on 2006-11-10
Id say it is a bug, to the zsnes team. It seems to be written in c (not suprising) and its not doing a very good job at allocating memory. 

The malloc command will allocate memory for certain things in the program, and here is what Id guess is stuffing up, its allocating RAM that isnt actually there, or the software cant see it. Its only a guess though as Im not an expert on this sort of thing. I know thats what the malloc command does but the rest really is a guess.

Try running zsnes using sudo, with the sound on and everything, maybe there is some permission problem which will solve this. Or otherwise maybe try another emulator.

---

### Post by techweenie on 2006-11-10
It just so happens I compiled zsnes 1.42 from source a couple minutes ago and it ran fine.  I loaded up Super Mario World and didn't notice any problems, but I didn't mess with many of the sound options either.

---

### Post by play0r on 2006-11-20
i figured it out i was missing needed code in .asoundrc
i was having problems with crackling sound in quake2 & then remembered i didn't re-edit my .asoundrc 
heres the following code that fixed it.

```
pcm.!default {
     type hw
     card 0
}

ctl.!default {
     type hw
     card 0
}
```

---

