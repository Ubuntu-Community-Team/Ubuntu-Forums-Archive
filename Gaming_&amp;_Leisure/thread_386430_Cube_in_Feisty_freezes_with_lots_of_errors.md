---
title: "Cube in Feisty freezes with lots of errors"
date: 2007-03-17
forum: Gaming &amp; Leisure
---

### Post by fakie_flip on 2007-03-17
I am getting many many errors from the game cube [www.cubeengine.com](www.cubeengine.com) in Feisty. I had to restart x many times to get my gui back. Doing certain things in the game or going to certain maps will freeze it. Nothing is wrong with my copy of the game. I tried downloading it again, and the game was still freezing with errors.

```
*** glibc detected *** ./bin_unix/linux_client: double free or corruption (fasttop): 0xb24128a0 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7af37ad]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb7af6e10]
/usr/lib/libX11.so.6[0xb79e4668]
/usr/lib/libX11.so.6(_XReply+0x12c)[0xb79e49bc]
/usr/lib/libX11.so.6(XSync+0x6a)[0xb79d8b6a]
/usr/lib/libX11.so.6(XCloseDisplay+0xd7)[0xb79b99b7]
/usr/lib/libSDL-1.2.so.0[0xb7eccc6e]
/usr/lib/libSDL-1.2.so.0[0xb7ed6497]
/usr/lib/libSDL-1.2.so.0(SDL_VideoQuit+0x50)[0xb7ec5e60]
/usr/lib/libSDL-1.2.so.0(SDL_QuitSubSystem+0x65)[0xb7e9a5e5]
/usr/lib/libSDL-1.2.so.0(SDL_Quit+0x1e)[0xb7e9a65e]
/usr/lib/libSDL-1.2.so.0[0xb7e9ae9f]
/lib/tls/i686/cmov/libpthread.so.0[0xb7e7a638]
/usr/lib/libSDL_mixer-1.2.so.0[0xb7e17696]
/usr/lib/libSDL-1.2.so.0[0xb7ea3ceb]
/usr/lib/libSDL-1.2.so.0[0xb7eeef3d]
/lib/tls/i686/cmov/libpthread.so.0[0xb7e7231b]
/lib/tls/i686/cmov/libc.so.6(clone+0x5e)[0xb7b5b3ee]
======= Memory map: ========
08048000-0807b000 r-xp 00000000 08:02 14090241   /home/chriscube/bin_unix/linux_client
0807b000-0807f000 rw-p 00033000 08:02 14090241   /home/chriscube/bin_unix/linux_client
0807f000-0b1ae000 rw-p 0807f000 00:00 0          [heap]
b1bff000-b1c00000 ---p b1bff000 00:00 0 
b1c00000-b2400000 rwxp b1c00000 00:00 0 
b2400000-b24d6000 rw-p b2400000 00:00 0 
b24d6000-b2500000 ---p b24d6000 00:00 0 
b2500000-b2556000 rw-p b2500000*** glibc detected *** ./bin_unix/linux_client: double free or corruption (fasttop): 0xb24128a0 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7af37ad]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb7af6e10]
/usr/lib/libX11.so.6[0xb79e4668]
/usr/lib/libX11.so.6(_XReply+0x12c)[0xb79e49bc]
/usr/lib/libX11.so.6(XSync+0x6a)[0xb79d8b6a]
/usr/lib/libX11.so.6(XCloseDisplay+0xd7)[0xb79b99b7]
/usr/lib/libSDL-1.2.so.0[0xb7eccc6e]
/usr/lib/libSDL-1.2.so.0[0xb7ed6497]
/usr/lib/libSDL-1.2.so.0(SDL_VideoQuit+0x50)[0xb7ec5e60]
/usr/lib/libSDL-1.2.so.0(SDL_QuitSubSystem+0x65)[0xb7e9a5e5]
/usr/lib/libSDL-1.2.so.0(SDL_Quit+0x1e)[0xb7e9a65e]
/usr/lib/libSDL-1.2.so.0[0xb7e9ae9f]
/lib/tls/i686/cmov/libpthread.so.0[0xb7e7a638]
/usr/lib/libSDL_mixer-1.2.so.0[0xb7e17696]
/usr/lib/libSDL-1.2.so.0[0xb7ea3ceb]
/usr/lib/libSDL-1.2.so.0[0xb7eeef3d]
/lib/tls/i686/cmov/libpthread.so.0[0xb7e7231b]
/lib/tls/i686/cmov/libc.so.6(clone+0x5e)[0xb7b5b3ee]
======= Memory map: ========
08048000-0807b000 r-xp 00000000 08:02 14090241   /home/chriscube/bin_unix/linux_client
0807b000-0807f000 rw-p 00033000 08:02 14090241   /home/chriscube/bin_unix/linux_client
0807f000-0b1ae000 rw-p 0807f000 00:00 0          [heap]
b1bff000-b1c00000 ---p b1bff000 00:00 0 
b1c00000-b2400000 rwxp b1c00000 00:00 0 
b2400000-b24d6000 rw-p b2400000 00:00 0 
b24d6000-b2500000 ---p b24d6000 00:00 0 
b2500000-b2556000 rw-p b2500000 00:00 0 
b2556000-b2600000 ---p b2556000 00:00 0 
b2600000-b26ff000 rw-p b2600000 00:00 0 
b26ff000-b2700000 ---p b26ff000 00:00 0 
b2712000-b2713000 ---p b2712000 00:00 0 
b2713000-b2f13000 rwxp b2713000 00:00 0 
b2f13000-b42d7000 rw-p b2f13000 00:00 0 
b4398000-b4499000 rw-p b4398000 00:00 0 
b4653000-b4754000 rw-p b4653000 00:00 0 
b4815000-b4900000 rw-p b4a0b000 00:00 0 
b4900000-b49e1000 rw-p b4900000 00:00 0 
b49e1000-b4a00000 ---p b49e1000 00:00 0 
b4a81000-b4b01000 rw-s 14206000 00:0d 14532      /dev/nvidia0
b4b01000-b4b02000 ---p b4b01000 00:00 0 
b4b02000-b5302000 rwxp b4b02000 00:00 0 
b5302000-b5502000 rw-s 047e1000 00:0d 14532      /dev/nvidia0
b5502000-b5543000 rw-p b5502000 00:00 0 
b5545000-b56a6000 rw-p b5545000 00:00 0 
b56e2000-b56eb000 r-xp 00000000 08:03 12780903   /lib/tls/i686/cmov/libnss_files-2.5.so
b56eb000-b56ed000 rw-p 00008000 08:03 12780903   /lib/tls/i686/cmov/libnss_files-2.5.so
b56ed000-b56f5000 r-xp 00000000 08:03 12780905   /lib/tls/i686/cmov/libnss_nis-2.5.so
b56f5000-b56f7000 rw-p 00007000 08:03 12780905   /lib/tls/i686/cmov/libnss_nis-2.5.so
b56f7000-b570a000 r-xp 00000000 08:03 12780900   /lib/tls/i686/cmov/libnsl-2.5.so
b570a000-b570c000 rw-p 00012000 08:03 12780900   /lib/tls/i686/cmov/libnsl-2.5.so
b570c000-b570e000 rw-p b570c000 00:00 0 
b570e000-b5715000 r-xp 00000000 08:03 12780901   /lib/tls/i686/cmov/libnss_compat-2.5.so
b5715000-b5717000 rw-p 00006000 08:03 12780901   /lib/tls/i686/cmov/libnss_compat-2.5.so
b5727000-b57a9000 rw-p b5727000 00:00 0 
b57a9000-b57aa000 r-xp 00000000 08:03 15696294   /usr/lib/gconv/ISO8859-1.so
b57aa000-b57ac000 rw-p 00000000 08:03 15696294   /usr/lib/gconv/ISO8859-1.so
b57ac000-b57b3000 r--s 00000000 08:03 15695873   /usr/lib/gconv/gconv-modules.cache
b57b4000-b57f4000 rw-s d793a000 00:0d 14532      /dev/nvidia0
b57f4000-b58f4000 rw-s 11921000 00:0d 14532      /dev/nvidia0
b58f4000-b58f8000 rw-s 139b2000 00:0d 14532      /dev/nvidia0
b58f8000-b58f9000 rw-s d797b000 00:0d 14532      /dev/nvidia0
b58f9000-b58fa000 rw-s 1212d000 00:0d 14532      /dev/nvidia0
b58fa000-b58fb000 rw-s 1212b000 00:0d 14532      /dev/nvidia0
b58fb000-b58fc000 rw-s fac02000 00:0d 14532      /dev/nvidia0
b58fc000-b5a3e000 rw-s 0e9c7000 00:0d 14532      /dev/nvidia0
b5a3e000-b5a3f000 rw-s 00000000 00:08 4390928    /SYSV00000000 (deleted)
b5a3f000-b5a80000 rw-p b5a3f000 00:00 0 
b5a80000-b5aea000 rw-p 00000000 00:0d 2661       /dev/zero
b5aea000-b5aeb000 rw-s fa001000 00:0d 14532      /dev/nvidia0
b5aeb000-b641b000 rw-s d0000000 00:0d 14532      /dev/nvidia0
b641b000-b643c000 rw-p b641b000 00:00 0 
b643c000-b6466000 rw-s 00000000 00:08 32768      /SYSV00000000 (deleted)
b64b1000-b64b2000 rw-p b64b1000 0Aborted
chris@ubuntu:~/cube$ 
chris@ubuntu:~/cube$ ./cube_unix 
init: sdl
init: net
init: world
game mode is ffa/default
init: video: sdl
init: video: mode
init: video: misc
init: gl
init: basetex
init: sound
init: cfg
init: localconnect
init: mainloop
read map packages/base/metl3.cgz (222 milliseconds)
Cyclops by metlslime
game mode is ffa/default
read map packages/base/rampage.cgz (1305 milliseconds)
Castle Rampage by Fanatic modded by spentron
game mode is SP
savegame restored
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
Segmentation fault
chris@ubuntu:~/cube$  00:00 0 
b2556000-b2600000 ---p b2556000 00:00 0 
b2600000-b26ff000 rw-p b2600000 00:00 0 
b26ff000-b2700000 ---p b26ff000 00:00 0 
b2712000-b2713000 ---p b2712000 00:00 0 
b2713000-b2f13000 rwxp b2713000 00:00 0 
b2f13000-b42d7000 rw-p b2f13000 00:00 0 
b4398000-b4499000 rw-p b4398000 00:00 0 
b4653000-b4754000 rw-p b4653000 00:00 0 
b4815000-b4900000 rw-p b4a0b000 00:00 0 
b4900000-b49e1000 rw-p b4900000 00:00 0 
b49e1000-b4a00000 ---p b49e1000 00:00 0 
b4a81000-b4b01000 rw-s 14206000 00:0d 14532      /dev/nvidia0
b4b01000-b4b02000 ---p b4b01000 00:00 0 
b4b02000-b5302000 rwxp b4b02000 00:00 0 
b5302000-b5502000 rw-s 047e1000 00:0d 14532      /dev/nvidia0
b5502000-b5543000 rw-p b5502000 00:00 0 
b5545000-b56a6000 rw-p b5545000 00:00 0 
b56e2000-b56eb000 r-xp 00000000 08:03 12780903   /lib/tls/i686/cmov/libnss_files-2.5.so
b56eb000-b56ed000 rw-p 00008000 08:03 12780903   /lib/tls/i686/cmov/libnss_files-2.5.so
b56ed000-b56f5000 r-xp 00000000 08:03 12780905   /lib/tls/i686/cmov/libnss_nis-2.5.so
b56f5000-b56f7000 rw-p 00007000 08:03 12780905   /lib/tls/i686/cmov/libnss_nis-2.5.so
b56f7000-b570a000 r-xp 00000000 08:03 12780900   /lib/tls/i686/cmov/libnsl-2.5.so
b570a000-b570c000 rw-p 00012000 08:03 12780900   /lib/tls/i686/cmov/libnsl-2.5.so
b570c000-b570e000 rw-p b570c000 00:00 0 
b570e000-b5715000 r-xp 00000000 08:03 12780901   /lib/tls/i686/cmov/libnss_compat-2.5.so
b5715000-b5717000 rw-p 00006000 08:03 12780901   /lib/tls/i686/cmov/libnss_compat-2.5.so
b5727000-b57a9000 rw-p b5727000 00:00 0 
b57a9000-b57aa000 r-xp 00000000 08:03 15696294   /usr/lib/gconv/ISO8859-1.so
b57aa000-b57ac000 rw-p 00000000 08:03 15696294   /usr/lib/gconv/ISO8859-1.so
b57ac000-b57b3000 r--s 00000000 08:03 15695873   /usr/lib/gconv/gconv-modules.cache
b57b4000-b57f4000 rw-s d793a000 00:0d 14532      /dev/nvidia0
b57f4000-b58f4000 rw-s 11921000 00:0d 14532      /dev/nvidia0
b58f4000-b58f8000 rw-s 139b2000 00:0d 14532      /dev/nvidia0
b58f8000-b58f9000 rw-s d797b000 00:0d 14532      /dev/nvidia0
b58f9000-b58fa000 rw-s 1212d000 00:0d 14532      /dev/nvidia0
b58fa000-b58fb000 rw-s 1212b000 00:0d 14532      /dev/nvidia0
b58fb000-b58fc000 rw-s fac02000 00:0d 14532      /dev/nvidia0
b58fc000-b5a3e000 rw-s 0e9c7000 00:0d 14532      /dev/nvidia0
b5a3e000-b5a3f000 rw-s 00000000 00:08 4390928    /SYSV00000000 (deleted)
b5a3f000-b5a80000 rw-p b5a3f000 00:00 0 
b5a80000-b5aea000 rw-p 00000000 00:0d 2661       /dev/zero
b5aea000-b5aeb000 rw-s fa001000 00:0d 14532      /dev/nvidia0
b5aeb000-b641b000 rw-s d0000000 00:0d 14532      /dev/nvidia0
b641b000-b643c000 rw-p b641b000 00:00 0 
b643c000-b6466000 rw-s 00000000 00:08 32768      /SYSV00000000 (deleted)
b64b1000-b64b2000 rw-p b64b1000 0Aborted
chris@ubuntu:~/cube$ 
chris@ubuntu:~/cube$ ./cube_unix 
init: sdl
init: net
init: world
game mode is ffa/default
init: video: sdl
init: video: mode
init: video: misc
init: gl
init: basetex
init: sound
init: cfg
init: localconnect
init: mainloop
read map packages/base/metl3.cgz (222 milliseconds)
Cyclops by metlslime
game mode is ffa/default
read map packages/base/rampage.cgz (1305 milliseconds)
Castle Rampage by Fanatic modded by spentron
game mode is SP
savegame restored
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
write /dev/sequencer: Bad file descriptor
Segmentation fault
chris@ubuntu:~/cube$ 
```

Here's my Nvidia driver version.

```
chris@ubuntu:~$ sudo nvidia-installer -i
Password:

Welcome to the NVIDIA Software Installer for Unix/Linux


The currently installed driver is: 'NVIDIA Accelerated Graphics Driver for
Linux-x86' (version: 1.0-9746).

chris@ubuntu:~$ 
```

---

### Post by hikaricore on 2007-03-17
As feisty is still in pre-beta development it may be hard to pinpoint the exact cause of this.  >.<

Are you having any sound issues in game?

> write /dev/sequencer: Bad file descriptor

Just a guess, and I may be wrong but this looks like a sound error.

Only other thing I can think of is making sure you're using the "nvidia" driver in your xorg.conf and not the "nv" (default driver).

```
cat /etc/X11/xorg.conf | grep Driver
```

should return something like this:

> 
Driver "kbd"
Driver "mouse"
Driver "_nvidia_"


You may have more or less lines returned than I did depending on your configuration, but if you see "nv" instead of "nvidia" this could be a major cause to the problem.

Again just speculating, I havn't much experience with feisty or Cube for that matter.

Good luck,

--Aaron

---

### Post by fakie_flip on 2007-03-17
> **hikaricore said:**
> As feisty is still in pre-beta development it may be hard to pinpoint the exact cause of this.  >.<

Are you having any sound issues in game?



Just a guess, and I may be wrong but this looks like a sound error.

Only other thing I can think of is making sure you're using the "nvidia" driver in your xorg.conf and not the "nv" (default driver).

```
cat /etc/X11/xorg.conf | grep Driver
```

should return something like this:



You may have more or less lines returned than I did depending on your configuration, but if you see "nv" instead of "nvidia" this could be a major cause to the problem.

Again just speculating, I havn't much experience with feisty or Cube for that matter.

Good luck,

--Aaron

I am using the correct driver. Otherwise, I wouldn't have nvidia-installer that you can in my first post which gives the version number to the nvidia driver, not the nv driver. No, the problem is not with sound. Here is a little help for you.

grep Driver /etc/X11/xorg.conf

does the same as

cat /etc/X11/xorg.conf | grep Driver

and it's less to type out.

---

