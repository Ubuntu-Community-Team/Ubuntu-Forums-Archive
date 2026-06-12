---
title: "nwn under wine works for a while, then display screwy"
date: 2017-02-07
forum: Gaming &amp; Leisure
---

### Post by Kris_M on 2017-02-07
16.04.1
using NWN from GOG
install using "wine setup_nwn_diamond_2.0.0.15.exe"

Works fine and displays full screen fine for maybe a week, so maybe 20 starts.

Then when start it changes the display to something and nwn window is off center. alt-enter will bring it back to full screen (1920x1080) but still screwed up - need to restart ubuntu to get display working again.  

Need to delete NWN folder from GOG in wine and reinstall it and copy saves back in. Then it works fine again for a while.

I tried copying out nwn.ini after a fresh install . restoring that fixed it once but not the second time.
The wine setup stays the same through it all after first use on ubuntu.

wine is whatever version PlayonLinux installed - 1.6.2 per wine --version

winetricks.log
```
ddr=gdi
d3dx9
directx9
vcrun2005
ddr=gdi
devenum
w_workaround_wine_bug-1429
dxdiagn
w_workaround_wine_bug-25715
quartz
w_workaround_wine_bug-25716
dxdiag
win7
ddr=gdi
```

wine config set to win7.
no virtual.
fullscreen=1

Any idea what is changing and causing the display prob?

---

### Post by Perfect Storm on 2017-02-07
Thread moved to Wine.

---

### Post by Kris_M on 2017-02-07
sorry - my bad

---

### Post by Perfect Storm on 2017-02-07
No problem.

Do you know you can run nwn native on ubuntu - [https://www.gog.com/forum/neverwinter_nights_series/enfrlinux_install_neverwinter_nights_on_debianubuntumintetc/page1](https://www.gog.com/forum/neverwinter_nights_series/enfrlinux_install_neverwinter_nights_on_debianubuntumintetc/page1)

---

### Post by Kris_M on 2017-02-07
> **Artificial Intelligence said:**
> No problem.

Do you know you can run nwn native on ubuntu - [https://www.gog.com/forum/neverwinter_nights_series/enfrlinux_install_neverwinter_nights_on_debianubuntumintetc/page1](https://www.gog.com/forum/neverwinter_nights_series/enfrlinux_install_neverwinter_nights_on_debianubuntumintetc/page1)

Thanks.

no.

I don't know what I'm doing.

Started downloading stuff, got to movies and got this:
```
kris@kris-Z97X-UD3H:~/Downloads/nwnnative$ tar -xvzf nwmovies-mpv.tar.gz
nwmovies/
nwmovies/nwmovies.c
nwmovies/nwmovies_lookup.c
nwmovies/nwmovies.h
nwmovies/nwmovies.README.txt
nwmovies/nwplaymovie
nwmovies/libdis/
nwmovies/libdis/vm.h
nwmovies/libdis/i386.h
nwmovies/libdis/libdis.h
nwmovies/libdis/libdis.c
nwmovies/libdis/LICENSE.original
nwmovies/libdis/i386_opcode.h
nwmovies/libdis/README
nwmovies/libdis/extension.h
nwmovies/libdis/i386.c
nwmovies/libdis/bastard.h
nwmovies/libdis/i386.opcode.map
nwmovies/nwmovies_install.pl
nwmovies/ChangeLog
nwmovies/nwmovies_link.S
nwmovies/nwmovies_cookie.c
nwmovies_install.pl
kris@kris-Z97X-UD3H:~/Downloads/nwnnative$ ./nwmovies_install.pl build
NOTICE: NWMovies: Executing:
gcc -m32  -I/emul/ia32-linux/usr/include -L/emul/ia32-linux/usr/lib -L/emul/ia32-linux/lib -L/lib32 -L/usr/lib32 -Wall -Inwmovies/libdis -g -fPIC -shared -Wl,-soname,libdisasm.so nwmovies/libdis/libdis.c nwmovies/libdis/i386.c -o nwmovies/libdis/libdisasm.so
In file included from /usr/include/stdio.h:27:0,
                 from nwmovies/libdis/libdis.h:4,
                 from nwmovies/libdis/libdis.c:1:
/usr/include/features.h:367:25: fatal error: sys/cdefs.h: No such file or directory
compilation terminated.
In file included from /usr/include/stdio.h:27:0,
                 from nwmovies/libdis/i386.c:1:
/usr/include/features.h:367:25: fatal error: sys/cdefs.h: No such file or directory
compilation terminated.
ERROR: child exited with value 1
ERROR: system() call failed.
kris@kris-Z97X-UD3H:~/Downloads/nwnnative$ 

```

thoughts?

I did not understand the instructions:
```
On 64-bit systems you also need 32-bit versions of elfutils and sdl.
```

---

### Post by Perfect Storm on 2017-02-07
hmmm....

try install
```
sudo apt-get install g++-multilib
```

---

### Post by Kris_M on 2017-02-07
thanks. did look like it was installing 32 stuff but no joy. same errors.

```
kris@kris-Z97X-UD3H:~/Downloads/nwnnative$ sudo apt-get install g++-multilib
[sudo] password for kris: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  ksh libcunit1 libjavascriptcoregtk-1.0-0 libqt4-designer libqt4-help
  libqt4-opengl libqt4-scripttools libqt4-svg libqt4-test
  libqtassistantclient4 libqtwebkit4 libunique-3.0-0 libvdpau1:i386
  libwebkitgtk-1.0-0 libwebkitgtk-1.0-common linux-headers-4.4.0-31
  linux-headers-4.4.0-31-generic linux-image-4.4.0-31-generic
  linux-image-extra-4.4.0-31-generic mesa-vdpau-drivers:i386 python-qt4
  python-sip vdpau-driver-all:i386
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  g++-5-multilib gcc-5-multilib gcc-multilib lib32asan2 lib32atomic1
  lib32cilkrts5 lib32gcc-5-dev lib32gomp1 lib32itm1 lib32mpx0 lib32quadmath0
  lib32stdc++-5-dev lib32stdc++6 lib32ubsan0 libc6-dev-i386 libc6-dev-x32
  libc6-x32 libx32asan2 libx32atomic1 libx32cilkrts5 libx32gcc-5-dev
  libx32gcc1 libx32gomp1 libx32itm1 libx32quadmath0 libx32stdc++-5-dev
  libx32stdc++6 libx32ubsan0
Suggested packages:
  lib32stdc++6-5-dbg libx32stdc++6-5-dbg
The following NEW packages will be installed:
  g++-5-multilib g++-multilib gcc-5-multilib gcc-multilib lib32asan2
  lib32atomic1 lib32cilkrts5 lib32gcc-5-dev lib32gomp1 lib32itm1 lib32mpx0
  lib32quadmath0 lib32stdc++-5-dev lib32stdc++6 lib32ubsan0 libc6-dev-i386
  libc6-dev-x32 libc6-x32 libx32asan2 libx32atomic1 libx32cilkrts5
  libx32gcc-5-dev libx32gcc1 libx32gomp1 libx32itm1 libx32quadmath0
  libx32stdc++-5-dev libx32stdc++6 libx32ubsan0
0 upgraded, 29 newly installed, 0 to remove and 0 not upgraded.
Need to get 12.7 MB of archives.
After this operation, 67.3 MB of additional disk space will be used.
Do you want to continue? [Y/n] 
Get:1 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libc6-dev-i386 amd64 2.23-0ubuntu5 [1,262 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libc6-x32 amd64 2.23-0ubuntu5 [2,550 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libc6-dev-x32 amd64 2.23-0ubuntu5 [1,559 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 libx32gcc1 amd64 1:6.0.1-0ubuntu1 [38.7 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 lib32gomp1 amd64 5.4.0-6ubuntu1~16.04.4 [59.7 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libx32gomp1 amd64 5.4.0-6ubuntu1~16.04.4 [55.4 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 lib32itm1 amd64 5.4.0-6ubuntu1~16.04.4 [29.5 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libx32itm1 amd64 5.4.0-6ubuntu1~16.04.4 [27.7 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 lib32atomic1 amd64 5.4.0-6ubuntu1~16.04.4 [8,634 B]
Get:10 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libx32atomic1 amd64 5.4.0-6ubuntu1~16.04.4 [8,888 B]
Get:11 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 lib32asan2 amd64 5.4.0-6ubuntu1~16.04.4 [259 kB]
Get:12 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libx32asan2 amd64 5.4.0-6ubuntu1~16.04.4 [253 kB]
Get:13 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 lib32stdc++6 amd64 5.4.0-6ubuntu1~16.04.4 [404 kB]
Get:14 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 lib32ubsan0 amd64 5.4.0-6ubuntu1~16.04.4 [105 kB]
Get:15 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libx32stdc++6 amd64 5.4.0-6ubuntu1~16.04.4 [384 kB]
Get:16 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libx32ubsan0 amd64 5.4.0-6ubuntu1~16.04.4 [97.0 kB]
Get:17 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 lib32cilkrts5 amd64 5.4.0-6ubuntu1~16.04.4 [44.8 kB]
Get:18 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libx32cilkrts5 amd64 5.4.0-6ubuntu1~16.04.4 [40.8 kB]
Get:19 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 lib32mpx0 amd64 5.4.0-6ubuntu1~16.04.4 [11.1 kB]
Get:20 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 lib32quadmath0 amd64 5.4.0-6ubuntu1~16.04.4 [203 kB]
Get:21 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libx32quadmath0 amd64 5.4.0-6ubuntu1~16.04.4 [134 kB]
Get:22 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 lib32gcc-5-dev amd64 5.4.0-6ubuntu1~16.04.4 [2,051 kB]
Get:23 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libx32gcc-5-dev amd64 5.4.0-6ubuntu1~16.04.4 [1,866 kB]
Get:24 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 gcc-5-multilib amd64 5.4.0-6ubuntu1~16.04.4 [966 B]
Get:25 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 lib32stdc++-5-dev amd64 5.4.0-6ubuntu1~16.04.4 [636 kB]
Get:26 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libx32stdc++-5-dev amd64 5.4.0-6ubuntu1~16.04.4 [609 kB]
Get:27 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 g++-5-multilib amd64 5.4.0-6ubuntu1~16.04.4 [988 B]
Get:28 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 gcc-multilib amd64 4:5.3.1-1ubuntu1 [1,212 B]
Get:29 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 g++-multilib amd64 4:5.3.1-1ubuntu1 [940 B]
Fetched 12.7 MB in 6s (1,916 kB/s)                                             
Selecting previously unselected package libc6-dev-i386.
(Reading database ... 257564 files and directories currently installed.)
Preparing to unpack .../libc6-dev-i386_2.23-0ubuntu5_amd64.deb ...
Unpacking libc6-dev-i386 (2.23-0ubuntu5) ...
Selecting previously unselected package libc6-x32.
Preparing to unpack .../libc6-x32_2.23-0ubuntu5_amd64.deb ...
Unpacking libc6-x32 (2.23-0ubuntu5) ...
Selecting previously unselected package libc6-dev-x32.
Preparing to unpack .../libc6-dev-x32_2.23-0ubuntu5_amd64.deb ...
Unpacking libc6-dev-x32 (2.23-0ubuntu5) ...
Selecting previously unselected package libx32gcc1.
Preparing to unpack .../libx32gcc1_1%3a6.0.1-0ubuntu1_amd64.deb ...
Unpacking libx32gcc1 (1:6.0.1-0ubuntu1) ...
Selecting previously unselected package lib32gomp1.
Preparing to unpack .../lib32gomp1_5.4.0-6ubuntu1~16.04.4_amd64.deb ...
Unpacking lib32gomp1 (5.4.0-6ubuntu1~16.04.4) ...
Selecting previously unselected package libx32gomp1.
Preparing to unpack .../libx32gomp1_5.4.0-6ubuntu1~16.04.4_amd64.deb ...
Unpacking libx32gomp1 (5.4.0-6ubuntu1~16.04.4) ...
Selecting previously unselected package lib32itm1.
Preparing to unpack .../lib32itm1_5.4.0-6ubuntu1~16.04.4_amd64.deb ...
Unpacking lib32itm1 (5.4.0-6ubuntu1~16.04.4) ...
Selecting previously unselected package libx32itm1.
Preparing to unpack .../libx32itm1_5.4.0-6ubuntu1~16.04.4_amd64.deb ...
Unpacking libx32itm1 (5.4.0-6ubuntu1~16.04.4) ...
Selecting previously unselected package lib32atomic1.
Preparing to unpack .../lib32atomic1_5.4.0-6ubuntu1~16.04.4_amd64.deb ...
Unpacking lib32atomic1 (5.4.0-6ubuntu1~16.04.4) ...
Selecting previously unselected package libx32atomic1.
Preparing to unpack .../libx32atomic1_5.4.0-6ubuntu1~16.04.4_amd64.deb ...
Unpacking libx32atomic1 (5.4.0-6ubuntu1~16.04.4) ...
Selecting previously unselected package lib32asan2.
Preparing to unpack .../lib32asan2_5.4.0-6ubuntu1~16.04.4_amd64.deb ...
Unpacking lib32asan2 (5.4.0-6ubuntu1~16.04.4) ...
Selecting previously unselected package libx32asan2.
Preparing to unpack .../libx32asan2_5.4.0-6ubuntu1~16.04.4_amd64.deb ...
Unpacking libx32asan2 (5.4.0-6ubuntu1~16.04.4) ...
Selecting previously unselected package lib32stdc++6.
Preparing to unpack .../lib32stdc++6_5.4.0-6ubuntu1~16.04.4_amd64.deb ...
Unpacking lib32stdc++6 (5.4.0-6ubuntu1~16.04.4) ...
Selecting previously unselected package lib32ubsan0.
Preparing to unpack .../lib32ubsan0_5.4.0-6ubuntu1~16.04.4_amd64.deb ...
Unpacking lib32ubsan0 (5.4.0-6ubuntu1~16.04.4) ...
Selecting previously unselected package libx32stdc++6.
Preparing to unpack .../libx32stdc++6_5.4.0-6ubuntu1~16.04.4_amd64.deb ...
Unpacking libx32stdc++6 (5.4.0-6ubuntu1~16.04.4) ...
Selecting previously unselected package libx32ubsan0.
Preparing to unpack .../libx32ubsan0_5.4.0-6ubuntu1~16.04.4_amd64.deb ...
Unpacking libx32ubsan0 (5.4.0-6ubuntu1~16.04.4) ...
Selecting previously unselected package lib32cilkrts5.
Preparing to unpack .../lib32cilkrts5_5.4.0-6ubuntu1~16.04.4_amd64.deb ...
Unpacking lib32cilkrts5 (5.4.0-6ubuntu1~16.04.4) ...
Selecting previously unselected package libx32cilkrts5.
Preparing to unpack .../libx32cilkrts5_5.4.0-6ubuntu1~16.04.4_amd64.deb ...
Unpacking libx32cilkrts5 (5.4.0-6ubuntu1~16.04.4) ...
Selecting previously unselected package lib32mpx0.
Preparing to unpack .../lib32mpx0_5.4.0-6ubuntu1~16.04.4_amd64.deb ...
Unpacking lib32mpx0 (5.4.0-6ubuntu1~16.04.4) ...
Selecting previously unselected package lib32quadmath0.
Preparing to unpack .../lib32quadmath0_5.4.0-6ubuntu1~16.04.4_amd64.deb ...
Unpacking lib32quadmath0 (5.4.0-6ubuntu1~16.04.4) ...
Selecting previously unselected package libx32quadmath0.
Preparing to unpack .../libx32quadmath0_5.4.0-6ubuntu1~16.04.4_amd64.deb ...
Unpacking libx32quadmath0 (5.4.0-6ubuntu1~16.04.4) ...
Selecting previously unselected package lib32gcc-5-dev.
Preparing to unpack .../lib32gcc-5-dev_5.4.0-6ubuntu1~16.04.4_amd64.deb ...
Unpacking lib32gcc-5-dev (5.4.0-6ubuntu1~16.04.4) ...
Selecting previously unselected package libx32gcc-5-dev.
Preparing to unpack .../libx32gcc-5-dev_5.4.0-6ubuntu1~16.04.4_amd64.deb ...
Unpacking libx32gcc-5-dev (5.4.0-6ubuntu1~16.04.4) ...
Selecting previously unselected package gcc-5-multilib.
Preparing to unpack .../gcc-5-multilib_5.4.0-6ubuntu1~16.04.4_amd64.deb ...
Unpacking gcc-5-multilib (5.4.0-6ubuntu1~16.04.4) ...
Selecting previously unselected package lib32stdc++-5-dev.
Preparing to unpack .../lib32stdc++-5-dev_5.4.0-6ubuntu1~16.04.4_amd64.deb ...
Unpacking lib32stdc++-5-dev (5.4.0-6ubuntu1~16.04.4) ...
Selecting previously unselected package libx32stdc++-5-dev.
Preparing to unpack .../libx32stdc++-5-dev_5.4.0-6ubuntu1~16.04.4_amd64.deb ...
Unpacking libx32stdc++-5-dev (5.4.0-6ubuntu1~16.04.4) ...
Selecting previously unselected package g++-5-multilib.
Preparing to unpack .../g++-5-multilib_5.4.0-6ubuntu1~16.04.4_amd64.deb ...
Unpacking g++-5-multilib (5.4.0-6ubuntu1~16.04.4) ...
Selecting previously unselected package gcc-multilib.
Preparing to unpack .../gcc-multilib_4%3a5.3.1-1ubuntu1_amd64.deb ...
Unpacking gcc-multilib (4:5.3.1-1ubuntu1) ...
Selecting previously unselected package g++-multilib.
Preparing to unpack .../g++-multilib_4%3a5.3.1-1ubuntu1_amd64.deb ...
Unpacking g++-multilib (4:5.3.1-1ubuntu1) ...
Processing triggers for libc-bin (2.23-0ubuntu5) ...
Setting up libc6-dev-i386 (2.23-0ubuntu5) ...
Setting up libc6-x32 (2.23-0ubuntu5) ...
Setting up libc6-dev-x32 (2.23-0ubuntu5) ...
Setting up libx32gcc1 (1:6.0.1-0ubuntu1) ...
Setting up lib32gomp1 (5.4.0-6ubuntu1~16.04.4) ...
Setting up libx32gomp1 (5.4.0-6ubuntu1~16.04.4) ...
Setting up lib32itm1 (5.4.0-6ubuntu1~16.04.4) ...
Setting up libx32itm1 (5.4.0-6ubuntu1~16.04.4) ...
Setting up lib32atomic1 (5.4.0-6ubuntu1~16.04.4) ...
Setting up libx32atomic1 (5.4.0-6ubuntu1~16.04.4) ...
Setting up lib32asan2 (5.4.0-6ubuntu1~16.04.4) ...
Setting up libx32asan2 (5.4.0-6ubuntu1~16.04.4) ...
Setting up lib32stdc++6 (5.4.0-6ubuntu1~16.04.4) ...
Setting up lib32ubsan0 (5.4.0-6ubuntu1~16.04.4) ...
Setting up libx32stdc++6 (5.4.0-6ubuntu1~16.04.4) ...
Setting up libx32ubsan0 (5.4.0-6ubuntu1~16.04.4) ...
Setting up lib32cilkrts5 (5.4.0-6ubuntu1~16.04.4) ...
Setting up libx32cilkrts5 (5.4.0-6ubuntu1~16.04.4) ...
Setting up lib32mpx0 (5.4.0-6ubuntu1~16.04.4) ...
Setting up lib32quadmath0 (5.4.0-6ubuntu1~16.04.4) ...
Setting up libx32quadmath0 (5.4.0-6ubuntu1~16.04.4) ...
Setting up lib32gcc-5-dev (5.4.0-6ubuntu1~16.04.4) ...
Setting up libx32gcc-5-dev (5.4.0-6ubuntu1~16.04.4) ...
Setting up gcc-5-multilib (5.4.0-6ubuntu1~16.04.4) ...
Setting up lib32stdc++-5-dev (5.4.0-6ubuntu1~16.04.4) ...
Setting up libx32stdc++-5-dev (5.4.0-6ubuntu1~16.04.4) ...
Setting up g++-5-multilib (5.4.0-6ubuntu1~16.04.4) ...
Setting up gcc-multilib (4:5.3.1-1ubuntu1) ...
Setting up g++-multilib (4:5.3.1-1ubuntu1) ...
Processing triggers for libc-bin (2.23-0ubuntu5) ...
kris@kris-Z97X-UD3H:~/Downloads/nwnnative$ ./nwmovies_install.pl build
NOTICE: NWMovies: Executing:
gcc -m32  -I/emul/ia32-linux/usr/include -L/emul/ia32-linux/usr/lib -L/emul/ia32-linux/lib -L/lib32 -L/usr/lib32 -Wall -Inwmovies/libdis -g -fPIC -shared -Wl,-soname,libdisasm.so nwmovies/libdis/libdis.c nwmovies/libdis/i386.c -o nwmovies/libdis/libdisasm.so
nwmovies/libdis/i386.c: In function ‘apply_seg’:
nwmovies/libdis/i386.c:347:21: warning: variable ‘reg’ set but not used [-Wunused-but-set-variable]
  unsigned int type, reg = 0;
                     ^
NOTICE: NWMovies: Executing:
gcc -m32  -I/emul/ia32-linux/usr/include -L/emul/ia32-linux/usr/lib -L/emul/ia32-linux/lib -L/lib32 -L/usr/lib32 -Wall -shared -g -I/usr/include/libelf -Inwmovies/libdis -o nwmovies/nwmovies.so nwmovies/nwmovies.c nwmovies/nwmovies_lookup.c nwmovies/nwmovies_cookie.c nwmovies/nwmovies_link.S  -ldl -Wl,-static -lelf -Wl,-Bdynamic
nwmovies/nwmovies.c:59:21: fatal error: SDL/SDL.h: No such file or directory
compilation terminated.
nwmovies/nwmovies_lookup.c:18:20: fatal error: libelf.h: No such file or directory
compilation terminated.
nwmovies/nwmovies_cookie.c:17:20: fatal error: libelf.h: No such file or directory
compilation terminated.
ERROR: child exited with value 1
ERROR: system() call failed.
kris@kris-Z97X-UD3H:~/Downloads/nwnnative$ 

```

---

### Post by Perfect Storm on 2017-02-07
> I did not understand the instructions
Code:
On 64-bit systems you also need 32-bit versions of elfutils and sdl.]

```
sudo dpkg --add-architecture i386
sudo apt-get update
sudo apt-get install elfutils:i386 libsdl1.2debian:i386
```

That should fix it

Moving the tread back to gaming as the thread evolved to something else.

---

### Post by Kris_M on 2017-02-07
thanks again, but nope...

```
kris@kris-Z97X-UD3H:~/Downloads/nwnnative$ 
kris@kris-Z97X-UD3H:~/Downloads/nwnnative$ sudo dpkg --add-architecture i386
kris@kris-Z97X-UD3H:~/Downloads/nwnnative$ sudo apt-get update
Hit:1 http://us.archive.ubuntu.com/ubuntu xenial InRelease
Get:2 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]    
Get:3 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]  
Get:4 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages [463 kB]
Hit:5 http://archive.canonical.com/ubuntu xenial InRelease                     
Get:6 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]     
Hit:7 http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu xenial InRelease
Hit:8 http://archive.canonical.com xenial InRelease                            
Get:9 http://us.archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages [455 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 DEP-11 Metadata [306 kB]
Get:11 http://us.archive.ubuntu.com/ubuntu xenial-updates/main DEP-11 64x64 Icons [194 kB]
Get:12 http://security.ubuntu.com/ubuntu xenial-security/main amd64 DEP-11 Metadata [68.1 kB]
Get:13 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 DEP-11 Metadata [133 kB]
Get:14 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe DEP-11 64x64 Icons [162 kB]
Get:15 http://security.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64 Icons [47.6 kB]
Get:16 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 DEP-11 Metadata [32.1 kB]
Get:17 http://us.archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 DEP-11 Metadata [2,516 B]
Get:18 http://us.archive.ubuntu.com/ubuntu xenial-backports/main amd64 DEP-11 Metadata [3,328 B]
Get:19 http://security.ubuntu.com/ubuntu xenial-security/universe DEP-11 64x64 Icons [37.0 kB]
Fetched 2,211 kB in 1s (1,710 kB/s)                                    
Reading package lists... Done
kris@kris-Z97X-UD3H:~/Downloads/nwnnative$ sudo apt-get install elfutils:i386 libsdl1.2debian:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  ksh libcunit1 libjavascriptcoregtk-1.0-0 libqt4-designer libqt4-help
  libqt4-opengl libqt4-scripttools libqt4-svg libqt4-test
  libqtassistantclient4 libqtwebkit4 libunique-3.0-0 libvdpau1:i386
  libwebkitgtk-1.0-0 libwebkitgtk-1.0-common linux-headers-4.4.0-31
  linux-headers-4.4.0-31-generic linux-image-4.4.0-31-generic
  linux-image-extra-4.4.0-31-generic mesa-vdpau-drivers:i386 python-qt4
  python-sip vdpau-driver-all:i386
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  libasm1:i386 libbz2-1.0:i386 libcaca0:i386 libdw1:i386 libncursesw5:i386
  libslang2:i386
The following NEW packages will be installed:
  elfutils:i386 libasm1:i386 libbz2-1.0:i386 libcaca0:i386 libdw1:i386
  libncursesw5:i386 libsdl1.2debian:i386 libslang2:i386
0 upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,489 kB of archives.
After this operation, 5,137 kB of additional disk space will be used.
Do you want to continue? [Y/n] 
Get:1 http://us.archive.ubuntu.com/ubuntu xenial/main i386 libslang2 i386 2.3.0-2ubuntu1 [409 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu xenial/main i386 libbz2-1.0 i386 1.0.6-8 [30.9 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu xenial/main i386 libncursesw5 i386 6.0+20160213-1ubuntu1 [125 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu xenial/main i386 libdw1 i386 0.165-3ubuntu1 [219 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu xenial/main i386 libasm1 i386 0.165-3ubuntu1 [17.7 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu xenial/universe i386 elfutils i386 0.165-3ubuntu1 [296 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu xenial/main i386 libcaca0 i386 0.99.beta19-2build2~gcc5.2 [208 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu xenial/main i386 libsdl1.2debian i386 1.2.15+dfsg1-3 [184 kB]
Fetched 1,489 kB in 0s (1,788 kB/s)           
Selecting previously unselected package libslang2:i386.
(Reading database ... 258254 files and directories currently installed.)
Preparing to unpack .../libslang2_2.3.0-2ubuntu1_i386.deb ...
Unpacking libslang2:i386 (2.3.0-2ubuntu1) ...
Selecting previously unselected package libbz2-1.0:i386.
Preparing to unpack .../libbz2-1.0_1.0.6-8_i386.deb ...
Unpacking libbz2-1.0:i386 (1.0.6-8) ...
Selecting previously unselected package libncursesw5:i386.
Preparing to unpack .../libncursesw5_6.0+20160213-1ubuntu1_i386.deb ...
Unpacking libncursesw5:i386 (6.0+20160213-1ubuntu1) ...
Selecting previously unselected package libdw1:i386.
Preparing to unpack .../libdw1_0.165-3ubuntu1_i386.deb ...
Unpacking libdw1:i386 (0.165-3ubuntu1) ...
Selecting previously unselected package libasm1:i386.
Preparing to unpack .../libasm1_0.165-3ubuntu1_i386.deb ...
Unpacking libasm1:i386 (0.165-3ubuntu1) ...
Selecting previously unselected package elfutils:i386.
Preparing to unpack .../elfutils_0.165-3ubuntu1_i386.deb ...
Unpacking elfutils:i386 (0.165-3ubuntu1) ...
Selecting previously unselected package libcaca0:i386.
Preparing to unpack .../libcaca0_0.99.beta19-2build2~gcc5.2_i386.deb ...
Unpacking libcaca0:i386 (0.99.beta19-2build2~gcc5.2) ...
Selecting previously unselected package libsdl1.2debian:i386.
Preparing to unpack .../libsdl1.2debian_1.2.15+dfsg1-3_i386.deb ...
Unpacking libsdl1.2debian:i386 (1.2.15+dfsg1-3) ...
Processing triggers for libc-bin (2.23-0ubuntu5) ...
Setting up libslang2:i386 (2.3.0-2ubuntu1) ...
Setting up libbz2-1.0:i386 (1.0.6-8) ...
Setting up libncursesw5:i386 (6.0+20160213-1ubuntu1) ...
Setting up libdw1:i386 (0.165-3ubuntu1) ...
Setting up libasm1:i386 (0.165-3ubuntu1) ...
Setting up elfutils:i386 (0.165-3ubuntu1) ...
Setting up libcaca0:i386 (0.99.beta19-2build2~gcc5.2) ...
Setting up libsdl1.2debian:i386 (1.2.15+dfsg1-3) ...
Processing triggers for libc-bin (2.23-0ubuntu5) ...
kris@kris-Z97X-UD3H:~/Downloads/nwnnative$ 
kris@kris-Z97X-UD3H:~/Downloads/nwnnative$ 
kris@kris-Z97X-UD3H:~/Downloads/nwnnative$ ./nwmovies_install.pl build
NOTICE: NWMovies: Executing:
gcc -m32  -I/emul/ia32-linux/usr/include -L/emul/ia32-linux/usr/lib -L/emul/ia32-linux/lib -L/lib32 -L/usr/lib32 -Wall -Inwmovies/libdis -g -fPIC -shared -Wl,-soname,libdisasm.so nwmovies/libdis/libdis.c nwmovies/libdis/i386.c -o nwmovies/libdis/libdisasm.so
nwmovies/libdis/i386.c: In function ‘apply_seg’:
nwmovies/libdis/i386.c:347:21: warning: variable ‘reg’ set but not used [-Wunused-but-set-variable]
  unsigned int type, reg = 0;
                     ^
NOTICE: NWMovies: Executing:
gcc -m32  -I/emul/ia32-linux/usr/include -L/emul/ia32-linux/usr/lib -L/emul/ia32-linux/lib -L/lib32 -L/usr/lib32 -Wall -shared -g -I/usr/include/libelf -Inwmovies/libdis -o nwmovies/nwmovies.so nwmovies/nwmovies.c nwmovies/nwmovies_lookup.c nwmovies/nwmovies_cookie.c nwmovies/nwmovies_link.S  -ldl -Wl,-static -lelf -Wl,-Bdynamic
nwmovies/nwmovies.c:59:21: fatal error: SDL/SDL.h: No such file or directory
compilation terminated.
nwmovies/nwmovies_lookup.c:18:20: fatal error: libelf.h: No such file or directory
compilation terminated.
nwmovies/nwmovies_cookie.c:17:20: fatal error: libelf.h: No such file or directory
compilation terminated.
ERROR: child exited with value 1
ERROR: system() call failed.
kris@kris-Z97X-UD3H:~/Downloads/nwnnative$ 

```

---

### Post by Perfect Storm on 2017-02-07
okay. A hard nut to crack: try
```
sudo apt-get install libsdl1.2-dev:i386 libelf1:i386
```

---

### Post by Kris_M on 2017-02-07
nope

```
kris@kris-Z97X-UD3H:~/Downloads/nwnnative$ sudo apt-get install libsdl1.2-dev:i386 libelf1:i386
[sudo] password for kris: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libelf1:i386 is already the newest version (0.165-3ubuntu1).
libelf1:i386 set to manually installed.
The following packages were automatically installed and are no longer required:
  ksh libcunit1 libjavascriptcoregtk-1.0-0 libqt4-designer libqt4-help
  libqt4-opengl libqt4-scripttools libqt4-svg libqt4-test
  libqtassistantclient4 libqtwebkit4 libunique-3.0-0 libvdpau1:i386
  libwebkitgtk-1.0-0 libwebkitgtk-1.0-common linux-headers-4.4.0-31
  linux-headers-4.4.0-31-generic linux-image-4.4.0-31-generic
  linux-image-extra-4.4.0-31-generic mesa-vdpau-drivers:i386 python-qt4
  python-sip vdpau-driver-all:i386
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  libasound2-dev:i386 libc6-dev:i386 libcaca-dev:i386 libdrm-dev:i386
  libgl1-mesa-dev:i386 libglib2.0-dev:i386 libglu1-mesa-dev:i386
  libpcre16-3:i386 libpcre3-dev:i386 libpcre32-3:i386 libpcrecpp0v5:i386
  libpng12-dev:i386 libpthread-stubs0-dev:i386 libpulse-dev:i386
  libpulse-mainloop-glib0:i386 libslang2-dev:i386 libx11-dev:i386 libx11-doc
  libx11-xcb-dev:i386 libxau-dev:i386 libxcb-dri2-0-dev:i386
  libxcb-dri3-dev:i386 libxcb-glx0-dev:i386 libxcb-present-dev:i386
  libxcb-randr0:i386 libxcb-randr0-dev:i386 libxcb-render0-dev:i386
  libxcb-shape0:i386 libxcb-shape0-dev:i386 libxcb-sync-dev:i386
  libxcb-xfixes0:i386 libxcb-xfixes0-dev:i386 libxcb1-dev:i386
  libxdamage-dev:i386 libxdmcp-dev:i386 libxext-dev:i386 libxfixes-dev:i386
  libxshmfence-dev:i386 libxxf86vm-dev:i386 linux-libc-dev:i386
  mesa-common-dev:i386 x11proto-core-dev x11proto-damage-dev x11proto-dri2-dev
  x11proto-fixes-dev x11proto-gl-dev x11proto-input-dev x11proto-kb-dev
  x11proto-xext-dev x11proto-xf86vidmode-dev xorg-sgml-doctools xtrans-dev
  zlib1g-dev:i386
Suggested packages:
  libasound2-doc:i386 glibc-doc:i386 manpages-dev:i386 libglib2.0-doc:i386
  libxcb-doc:i386 libxext-doc:i386
The following NEW packages will be installed:
  libasound2-dev:i386 libc6-dev:i386 libcaca-dev:i386 libdrm-dev:i386
  libgl1-mesa-dev:i386 libglib2.0-dev:i386 libglu1-mesa-dev:i386
  libpcre16-3:i386 libpcre3-dev:i386 libpcre32-3:i386 libpcrecpp0v5:i386
  libpng12-dev:i386 libpthread-stubs0-dev:i386 libpulse-dev:i386
  libpulse-mainloop-glib0:i386 libsdl1.2-dev:i386 libslang2-dev:i386
  libx11-dev:i386 libx11-doc libx11-xcb-dev:i386 libxau-dev:i386
  libxcb-dri2-0-dev:i386 libxcb-dri3-dev:i386 libxcb-glx0-dev:i386
  libxcb-present-dev:i386 libxcb-randr0:i386 libxcb-randr0-dev:i386
  libxcb-render0-dev:i386 libxcb-shape0:i386 libxcb-shape0-dev:i386
  libxcb-sync-dev:i386 libxcb-xfixes0:i386 libxcb-xfixes0-dev:i386
  libxcb1-dev:i386 libxdamage-dev:i386 libxdmcp-dev:i386 libxext-dev:i386
  libxfixes-dev:i386 libxshmfence-dev:i386 libxxf86vm-dev:i386
  linux-libc-dev:i386 mesa-common-dev:i386 x11proto-core-dev
  x11proto-damage-dev x11proto-dri2-dev x11proto-fixes-dev x11proto-gl-dev
  x11proto-input-dev x11proto-kb-dev x11proto-xext-dev
  x11proto-xf86vidmode-dev xorg-sgml-doctools xtrans-dev zlib1g-dev:i386
0 upgraded, 54 newly installed, 0 to remove and 0 not upgraded.
Need to get 11.4 MB of archives.
After this operation, 59.1 MB of additional disk space will be used.
Do you want to continue? [Y/n] 
Get:1 http://us.archive.ubuntu.com/ubuntu xenial/main i386 libpcrecpp0v5 i386 2:8.38-3.1 [16.0 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu xenial/main i386 libasound2-dev i386 1.1.0-0ubuntu1 [114 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu xenial-updates/main i386 linux-libc-dev i386 4.4.0-62.83 [831 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu xenial-updates/main i386 libc6-dev i386 2.23-0ubuntu5 [1,673 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu xenial/main i386 zlib1g-dev i386 1:1.2.8.dfsg-2ubuntu4 [167 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu xenial/main i386 libpng12-dev i386 1.2.54-1ubuntu1 [187 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu xenial/main i386 libslang2-dev i386 2.3.0-2ubuntu1 [364 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu xenial/main i386 libcaca-dev i386 0.99.beta19-2build2~gcc5.2 [721 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu xenial-updates/main i386 libdrm-dev i386 2.4.67-1ubuntu0.16.04.2 [213 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu xenial/main i386 libpcre16-3 i386 2:8.38-3.1 [144 kB]
Get:11 http://us.archive.ubuntu.com/ubuntu xenial/main i386 libpcre32-3 i386 2:8.38-3.1 [136 kB]
Get:12 http://us.archive.ubuntu.com/ubuntu xenial/main i386 libpcre3-dev i386 2:8.38-3.1 [530 kB]
Get:13 http://us.archive.ubuntu.com/ubuntu xenial-updates/main i386 libglib2.0-dev i386 2.48.2-0ubuntu1 [1,422 kB]
Get:14 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 xorg-sgml-doctools all 1:1.11-1 [12.9 kB]
Get:15 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 x11proto-core-dev all 7.0.28-2ubuntu1 [254 kB]
Get:16 http://us.archive.ubuntu.com/ubuntu xenial/main i386 libxau-dev i386 1:1.0.8-1 [10.2 kB]
Get:17 http://us.archive.ubuntu.com/ubuntu xenial/main i386 libxdmcp-dev i386 1:1.1.2-1.1 [25.0 kB]
Get:18 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 x11proto-input-dev all 2.3.1-1 [118 kB]
Get:19 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 x11proto-kb-dev all 1.0.7-0ubuntu1 [224 kB]
Get:20 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 xtrans-dev all 1.3.5-1 [70.5 kB]
Get:21 http://us.archive.ubuntu.com/ubuntu xenial/main i386 libpthread-stubs0-dev i386 0.3-4 [4,054 B]
Get:22 http://us.archive.ubuntu.com/ubuntu xenial/main i386 libxcb1-dev i386 1.11.1-1ubuntu1 [76.3 kB]
Get:23 http://us.archive.ubuntu.com/ubuntu xenial/main i386 libx11-dev i386 2:1.6.3-1ubuntu2 [663 kB]
Get:24 http://us.archive.ubuntu.com/ubuntu xenial-updates/main i386 mesa-common-dev i386 11.2.0-1ubuntu2.2 [460 kB]
Get:25 http://us.archive.ubuntu.com/ubuntu xenial/main i386 libx11-xcb-dev i386 2:1.6.3-1ubuntu2 [9,738 B]
Get:26 http://us.archive.ubuntu.com/ubuntu xenial/main i386 libxcb-dri3-dev i386 1.11.1-1ubuntu1 [5,758 B]
Get:27 http://us.archive.ubuntu.com/ubuntu xenial/main i386 libxcb-randr0 i386 1.11.1-1ubuntu1 [15.6 kB]
Get:28 http://us.archive.ubuntu.com/ubuntu xenial/main i386 libxcb-render0-dev i386 1.11.1-1ubuntu1 [15.6 kB]
Get:29 http://us.archive.ubuntu.com/ubuntu xenial/main i386 libxcb-randr0-dev i386 1.11.1-1ubuntu1 [18.6 kB]
Get:30 http://us.archive.ubuntu.com/ubuntu xenial/main i386 libxcb-xfixes0 i386 1.11.1-1ubuntu1 [9,350 B]
Get:31 http://us.archive.ubuntu.com/ubuntu xenial/main i386 libxcb-shape0 i386 1.11.1-1ubuntu1 [5,944 B]
Get:32 http://us.archive.ubuntu.com/ubuntu xenial/main i386 libxcb-shape0-dev i386 1.11.1-1ubuntu1 [6,924 B]
Get:33 http://us.archive.ubuntu.com/ubuntu xenial/main i386 libxcb-xfixes0-dev i386 1.11.1-1ubuntu1 [11.3 kB]
Get:34 http://us.archive.ubuntu.com/ubuntu xenial/main i386 libxcb-sync-dev i386 1.11.1-1ubuntu1 [10.2 kB]
Get:35 http://us.archive.ubuntu.com/ubuntu xenial/main i386 libxcb-present-dev i386 1.11.1-1ubuntu1 [6,678 B]
Get:36 http://us.archive.ubuntu.com/ubuntu xenial/main i386 libxshmfence-dev i386 1.2-1 [3,730 B]
Get:37 http://us.archive.ubuntu.com/ubuntu xenial/main i386 libxcb-dri2-0-dev i386 1.11.1-1ubuntu1 [8,414 B]
Get:38 http://us.archive.ubuntu.com/ubuntu xenial/main i386 libxcb-glx0-dev i386 1.11.1-1ubuntu1 [27.2 kB]
Get:39 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 x11proto-xext-dev all 7.3.0-1 [212 kB]
Get:40 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 x11proto-fixes-dev all 1:5.0-2ubuntu2 [14.2 kB]
Get:41 http://us.archive.ubuntu.com/ubuntu xenial/main i386 libxfixes-dev i386 1:5.0.1-2 [11.2 kB]
Get:42 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 x11proto-damage-dev all 1:1.2.1-2 [8,286 B]
Get:43 http://us.archive.ubuntu.com/ubuntu xenial/main i386 libxdamage-dev i386 1:1.1.4-2 [4,900 B]
Get:44 http://us.archive.ubuntu.com/ubuntu xenial/main i386 libxext-dev i386 2:1.3.3-1 [82.8 kB]
Get:45 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 x11proto-xf86vidmode-dev all 2.3.1-2 [6,116 B]
Get:46 http://us.archive.ubuntu.com/ubuntu xenial/main i386 libxxf86vm-dev i386 1:1.1.4-1 [13.9 kB]
Get:47 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 x11proto-dri2-dev all 2.8-2 [12.6 kB]
Get:48 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 x11proto-gl-dev all 1.4.17-1 [17.9 kB]
Get:49 http://us.archive.ubuntu.com/ubuntu xenial-updates/main i386 libgl1-mesa-dev i386 11.2.0-1ubuntu2.2 [4,412 B]
Get:50 http://us.archive.ubuntu.com/ubuntu xenial/main i386 libglu1-mesa-dev i386 9.0.0-2.1 [204 kB]
Get:51 http://us.archive.ubuntu.com/ubuntu xenial-updates/main i386 libpulse-mainloop-glib0 i386 1:8.0-0ubuntu3.2 [12.0 kB]
Get:52 http://us.archive.ubuntu.com/ubuntu xenial-updates/main i386 libpulse-dev i386 1:8.0-0ubuntu3.2 [71.3 kB]
Get:53 http://us.archive.ubuntu.com/ubuntu xenial/main i386 libsdl1.2-dev i386 1.2.15+dfsg1-3 [716 kB]
Get:54 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 libx11-doc all 2:1.6.3-1ubuntu2 [1,465 kB]
Fetched 11.4 MB in 5s (1,910 kB/s)     
Extracting templates from packages: 100%
Selecting previously unselected package libpcrecpp0v5:i386.
(Reading database ... 258344 files and directories currently installed.)
Preparing to unpack .../libpcrecpp0v5_2%3a8.38-3.1_i386.deb ...
Unpacking libpcrecpp0v5:i386 (2:8.38-3.1) ...
Selecting previously unselected package libasound2-dev:i386.
Preparing to unpack .../libasound2-dev_1.1.0-0ubuntu1_i386.deb ...
Unpacking libasound2-dev:i386 (1.1.0-0ubuntu1) ...
Selecting previously unselected package linux-libc-dev:i386.
Preparing to unpack .../linux-libc-dev_4.4.0-62.83_i386.deb ...
Unpacking linux-libc-dev:i386 (4.4.0-62.83) ...
Selecting previously unselected package libc6-dev:i386.
Preparing to unpack .../libc6-dev_2.23-0ubuntu5_i386.deb ...
Unpacking libc6-dev:i386 (2.23-0ubuntu5) ...
Selecting previously unselected package zlib1g-dev:i386.
Preparing to unpack .../zlib1g-dev_1%3a1.2.8.dfsg-2ubuntu4_i386.deb ...
Unpacking zlib1g-dev:i386 (1:1.2.8.dfsg-2ubuntu4) ...
Selecting previously unselected package libpng12-dev:i386.
Preparing to unpack .../libpng12-dev_1.2.54-1ubuntu1_i386.deb ...
Unpacking libpng12-dev:i386 (1.2.54-1ubuntu1) ...
Selecting previously unselected package libslang2-dev:i386.
Preparing to unpack .../libslang2-dev_2.3.0-2ubuntu1_i386.deb ...
Unpacking libslang2-dev:i386 (2.3.0-2ubuntu1) ...
Selecting previously unselected package libcaca-dev:i386.
Preparing to unpack .../libcaca-dev_0.99.beta19-2build2~gcc5.2_i386.deb ...
Unpacking libcaca-dev:i386 (0.99.beta19-2build2~gcc5.2) ...
Selecting previously unselected package libdrm-dev:i386.
Preparing to unpack .../libdrm-dev_2.4.67-1ubuntu0.16.04.2_i386.deb ...
Unpacking libdrm-dev:i386 (2.4.67-1ubuntu0.16.04.2) ...
Selecting previously unselected package libpcre16-3:i386.
Preparing to unpack .../libpcre16-3_2%3a8.38-3.1_i386.deb ...
Unpacking libpcre16-3:i386 (2:8.38-3.1) ...
Selecting previously unselected package libpcre32-3:i386.
Preparing to unpack .../libpcre32-3_2%3a8.38-3.1_i386.deb ...
Unpacking libpcre32-3:i386 (2:8.38-3.1) ...
Selecting previously unselected package libpcre3-dev:i386.
Preparing to unpack .../libpcre3-dev_2%3a8.38-3.1_i386.deb ...
Unpacking libpcre3-dev:i386 (2:8.38-3.1) ...
Selecting previously unselected package libglib2.0-dev:i386.
Preparing to unpack .../libglib2.0-dev_2.48.2-0ubuntu1_i386.deb ...
Unpacking libglib2.0-dev:i386 (2.48.2-0ubuntu1) ...
Selecting previously unselected package xorg-sgml-doctools.
Preparing to unpack .../xorg-sgml-doctools_1%3a1.11-1_all.deb ...
Unpacking xorg-sgml-doctools (1:1.11-1) ...
Selecting previously unselected package x11proto-core-dev.
Preparing to unpack .../x11proto-core-dev_7.0.28-2ubuntu1_all.deb ...
Unpacking x11proto-core-dev (7.0.28-2ubuntu1) ...
Selecting previously unselected package libxau-dev:i386.
Preparing to unpack .../libxau-dev_1%3a1.0.8-1_i386.deb ...
Unpacking libxau-dev:i386 (1:1.0.8-1) ...
Selecting previously unselected package libxdmcp-dev:i386.
Preparing to unpack .../libxdmcp-dev_1%3a1.1.2-1.1_i386.deb ...
Unpacking libxdmcp-dev:i386 (1:1.1.2-1.1) ...
Selecting previously unselected package x11proto-input-dev.
Preparing to unpack .../x11proto-input-dev_2.3.1-1_all.deb ...
Unpacking x11proto-input-dev (2.3.1-1) ...
Selecting previously unselected package x11proto-kb-dev.
Preparing to unpack .../x11proto-kb-dev_1.0.7-0ubuntu1_all.deb ...
Unpacking x11proto-kb-dev (1.0.7-0ubuntu1) ...
Selecting previously unselected package xtrans-dev.
Preparing to unpack .../xtrans-dev_1.3.5-1_all.deb ...
Unpacking xtrans-dev (1.3.5-1) ...
Selecting previously unselected package libpthread-stubs0-dev:i386.
Preparing to unpack .../libpthread-stubs0-dev_0.3-4_i386.deb ...
Unpacking libpthread-stubs0-dev:i386 (0.3-4) ...
Selecting previously unselected package libxcb1-dev:i386.
Preparing to unpack .../libxcb1-dev_1.11.1-1ubuntu1_i386.deb ...
Unpacking libxcb1-dev:i386 (1.11.1-1ubuntu1) ...
Selecting previously unselected package libx11-dev:i386.
Preparing to unpack .../libx11-dev_2%3a1.6.3-1ubuntu2_i386.deb ...
Unpacking libx11-dev:i386 (2:1.6.3-1ubuntu2) ...
Selecting previously unselected package mesa-common-dev:i386.
Preparing to unpack .../mesa-common-dev_11.2.0-1ubuntu2.2_i386.deb ...
Unpacking mesa-common-dev:i386 (11.2.0-1ubuntu2.2) ...
Selecting previously unselected package libx11-xcb-dev:i386.
Preparing to unpack .../libx11-xcb-dev_2%3a1.6.3-1ubuntu2_i386.deb ...
Unpacking libx11-xcb-dev:i386 (2:1.6.3-1ubuntu2) ...
Selecting previously unselected package libxcb-dri3-dev:i386.
Preparing to unpack .../libxcb-dri3-dev_1.11.1-1ubuntu1_i386.deb ...
Unpacking libxcb-dri3-dev:i386 (1.11.1-1ubuntu1) ...
Selecting previously unselected package libxcb-randr0:i386.
Preparing to unpack .../libxcb-randr0_1.11.1-1ubuntu1_i386.deb ...
Unpacking libxcb-randr0:i386 (1.11.1-1ubuntu1) ...
Selecting previously unselected package libxcb-render0-dev:i386.
Preparing to unpack .../libxcb-render0-dev_1.11.1-1ubuntu1_i386.deb ...
Unpacking libxcb-render0-dev:i386 (1.11.1-1ubuntu1) ...
Selecting previously unselected package libxcb-randr0-dev:i386.
Preparing to unpack .../libxcb-randr0-dev_1.11.1-1ubuntu1_i386.deb ...
Unpacking libxcb-randr0-dev:i386 (1.11.1-1ubuntu1) ...
Selecting previously unselected package libxcb-xfixes0:i386.
Preparing to unpack .../libxcb-xfixes0_1.11.1-1ubuntu1_i386.deb ...
Unpacking libxcb-xfixes0:i386 (1.11.1-1ubuntu1) ...
Selecting previously unselected package libxcb-shape0:i386.
Preparing to unpack .../libxcb-shape0_1.11.1-1ubuntu1_i386.deb ...
Unpacking libxcb-shape0:i386 (1.11.1-1ubuntu1) ...
Selecting previously unselected package libxcb-shape0-dev:i386.
Preparing to unpack .../libxcb-shape0-dev_1.11.1-1ubuntu1_i386.deb ...
Unpacking libxcb-shape0-dev:i386 (1.11.1-1ubuntu1) ...
Selecting previously unselected package libxcb-xfixes0-dev:i386.
Preparing to unpack .../libxcb-xfixes0-dev_1.11.1-1ubuntu1_i386.deb ...
Unpacking libxcb-xfixes0-dev:i386 (1.11.1-1ubuntu1) ...
Selecting previously unselected package libxcb-sync-dev:i386.
Preparing to unpack .../libxcb-sync-dev_1.11.1-1ubuntu1_i386.deb ...
Unpacking libxcb-sync-dev:i386 (1.11.1-1ubuntu1) ...
Selecting previously unselected package libxcb-present-dev:i386.
Preparing to unpack .../libxcb-present-dev_1.11.1-1ubuntu1_i386.deb ...
Unpacking libxcb-present-dev:i386 (1.11.1-1ubuntu1) ...
Selecting previously unselected package libxshmfence-dev:i386.
Preparing to unpack .../libxshmfence-dev_1.2-1_i386.deb ...
Unpacking libxshmfence-dev:i386 (1.2-1) ...
Selecting previously unselected package libxcb-dri2-0-dev:i386.
Preparing to unpack .../libxcb-dri2-0-dev_1.11.1-1ubuntu1_i386.deb ...
Unpacking libxcb-dri2-0-dev:i386 (1.11.1-1ubuntu1) ...
Selecting previously unselected package libxcb-glx0-dev:i386.
Preparing to unpack .../libxcb-glx0-dev_1.11.1-1ubuntu1_i386.deb ...
Unpacking libxcb-glx0-dev:i386 (1.11.1-1ubuntu1) ...
Selecting previously unselected package x11proto-xext-dev.
Preparing to unpack .../x11proto-xext-dev_7.3.0-1_all.deb ...
Unpacking x11proto-xext-dev (7.3.0-1) ...
Selecting previously unselected package x11proto-fixes-dev.
Preparing to unpack .../x11proto-fixes-dev_1%3a5.0-2ubuntu2_all.deb ...
Unpacking x11proto-fixes-dev (1:5.0-2ubuntu2) ...
Selecting previously unselected package libxfixes-dev:i386.
Preparing to unpack .../libxfixes-dev_1%3a5.0.1-2_i386.deb ...
Unpacking libxfixes-dev:i386 (1:5.0.1-2) ...
Selecting previously unselected package x11proto-damage-dev.
Preparing to unpack .../x11proto-damage-dev_1%3a1.2.1-2_all.deb ...
Unpacking x11proto-damage-dev (1:1.2.1-2) ...
Selecting previously unselected package libxdamage-dev:i386.
Preparing to unpack .../libxdamage-dev_1%3a1.1.4-2_i386.deb ...
Unpacking libxdamage-dev:i386 (1:1.1.4-2) ...
Selecting previously unselected package libxext-dev:i386.
Preparing to unpack .../libxext-dev_2%3a1.3.3-1_i386.deb ...
Unpacking libxext-dev:i386 (2:1.3.3-1) ...
Selecting previously unselected package x11proto-xf86vidmode-dev.
Preparing to unpack .../x11proto-xf86vidmode-dev_2.3.1-2_all.deb ...
Unpacking x11proto-xf86vidmode-dev (2.3.1-2) ...
Selecting previously unselected package libxxf86vm-dev:i386.
Preparing to unpack .../libxxf86vm-dev_1%3a1.1.4-1_i386.deb ...
Unpacking libxxf86vm-dev:i386 (1:1.1.4-1) ...
Selecting previously unselected package x11proto-dri2-dev.
Preparing to unpack .../x11proto-dri2-dev_2.8-2_all.deb ...
Unpacking x11proto-dri2-dev (2.8-2) ...
Selecting previously unselected package x11proto-gl-dev.
Preparing to unpack .../x11proto-gl-dev_1.4.17-1_all.deb ...
Unpacking x11proto-gl-dev (1.4.17-1) ...
Selecting previously unselected package libgl1-mesa-dev:i386.
Preparing to unpack .../libgl1-mesa-dev_11.2.0-1ubuntu2.2_i386.deb ...
Unpacking libgl1-mesa-dev:i386 (11.2.0-1ubuntu2.2) ...
Selecting previously unselected package libglu1-mesa-dev:i386.
Preparing to unpack .../libglu1-mesa-dev_9.0.0-2.1_i386.deb ...
Unpacking libglu1-mesa-dev:i386 (9.0.0-2.1) ...
Selecting previously unselected package libpulse-mainloop-glib0:i386.
Preparing to unpack .../libpulse-mainloop-glib0_1%3a8.0-0ubuntu3.2_i386.deb ...
Unpacking libpulse-mainloop-glib0:i386 (1:8.0-0ubuntu3.2) ...
Selecting previously unselected package libpulse-dev:i386.
Preparing to unpack .../libpulse-dev_1%3a8.0-0ubuntu3.2_i386.deb ...
Unpacking libpulse-dev:i386 (1:8.0-0ubuntu3.2) ...
Selecting previously unselected package libsdl1.2-dev:i386.
Preparing to unpack .../libsdl1.2-dev_1.2.15+dfsg1-3_i386.deb ...
Unpacking libsdl1.2-dev:i386 (1.2.15+dfsg1-3) ...
Selecting previously unselected package libx11-doc.
Preparing to unpack .../libx11-doc_2%3a1.6.3-1ubuntu2_all.deb ...
Unpacking libx11-doc (2:1.6.3-1ubuntu2) ...
Processing triggers for libc-bin (2.23-0ubuntu5) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for libglib2.0-0:amd64 (2.48.2-0ubuntu1) ...
Processing triggers for libglib2.0-0:i386 (2.48.2-0ubuntu1) ...
Processing triggers for doc-base (0.10.7) ...
Processing 1 added doc-base file...
Setting up libpcrecpp0v5:i386 (2:8.38-3.1) ...
Setting up libasound2-dev:i386 (1.1.0-0ubuntu1) ...
Setting up linux-libc-dev:i386 (4.4.0-62.83) ...
Setting up libc6-dev:i386 (2.23-0ubuntu5) ...
Setting up zlib1g-dev:i386 (1:1.2.8.dfsg-2ubuntu4) ...
Setting up libpng12-dev:i386 (1.2.54-1ubuntu1) ...
Setting up libslang2-dev:i386 (2.3.0-2ubuntu1) ...
Setting up libcaca-dev:i386 (0.99.beta19-2build2~gcc5.2) ...
Setting up libdrm-dev:i386 (2.4.67-1ubuntu0.16.04.2) ...
Setting up libpcre16-3:i386 (2:8.38-3.1) ...
Setting up libpcre32-3:i386 (2:8.38-3.1) ...
Setting up libpcre3-dev:i386 (2:8.38-3.1) ...
Setting up libglib2.0-dev:i386 (2.48.2-0ubuntu1) ...
Setting up xorg-sgml-doctools (1:1.11-1) ...
Setting up x11proto-core-dev (7.0.28-2ubuntu1) ...
Setting up libxau-dev:i386 (1:1.0.8-1) ...
Setting up libxdmcp-dev:i386 (1:1.1.2-1.1) ...
Setting up x11proto-input-dev (2.3.1-1) ...
Setting up x11proto-kb-dev (1.0.7-0ubuntu1) ...
Setting up xtrans-dev (1.3.5-1) ...
Setting up libpthread-stubs0-dev:i386 (0.3-4) ...
Setting up libxcb1-dev:i386 (1.11.1-1ubuntu1) ...
Setting up libx11-dev:i386 (2:1.6.3-1ubuntu2) ...
Setting up mesa-common-dev:i386 (11.2.0-1ubuntu2.2) ...
Setting up libx11-xcb-dev:i386 (2:1.6.3-1ubuntu2) ...
Setting up libxcb-dri3-dev:i386 (1.11.1-1ubuntu1) ...
Setting up libxcb-randr0:i386 (1.11.1-1ubuntu1) ...
Setting up libxcb-render0-dev:i386 (1.11.1-1ubuntu1) ...
Setting up libxcb-randr0-dev:i386 (1.11.1-1ubuntu1) ...
Setting up libxcb-xfixes0:i386 (1.11.1-1ubuntu1) ...
Setting up libxcb-shape0:i386 (1.11.1-1ubuntu1) ...
Setting up libxcb-shape0-dev:i386 (1.11.1-1ubuntu1) ...
Setting up libxcb-xfixes0-dev:i386 (1.11.1-1ubuntu1) ...
Setting up libxcb-sync-dev:i386 (1.11.1-1ubuntu1) ...
Setting up libxcb-present-dev:i386 (1.11.1-1ubuntu1) ...
Setting up libxshmfence-dev:i386 (1.2-1) ...
Setting up libxcb-dri2-0-dev:i386 (1.11.1-1ubuntu1) ...
Setting up libxcb-glx0-dev:i386 (1.11.1-1ubuntu1) ...
Setting up x11proto-xext-dev (7.3.0-1) ...
Setting up x11proto-fixes-dev (1:5.0-2ubuntu2) ...
Setting up libxfixes-dev:i386 (1:5.0.1-2) ...
Setting up x11proto-damage-dev (1:1.2.1-2) ...
Setting up libxdamage-dev:i386 (1:1.1.4-2) ...
Setting up libxext-dev:i386 (2:1.3.3-1) ...
Setting up x11proto-xf86vidmode-dev (2.3.1-2) ...
Setting up libxxf86vm-dev:i386 (1:1.1.4-1) ...
Setting up x11proto-dri2-dev (2.8-2) ...
Setting up x11proto-gl-dev (1.4.17-1) ...
Setting up libgl1-mesa-dev:i386 (11.2.0-1ubuntu2.2) ...
Setting up libglu1-mesa-dev:i386 (9.0.0-2.1) ...
Setting up libpulse-mainloop-glib0:i386 (1:8.0-0ubuntu3.2) ...
Setting up libpulse-dev:i386 (1:8.0-0ubuntu3.2) ...
Setting up libsdl1.2-dev:i386 (1.2.15+dfsg1-3) ...
Setting up libx11-doc (2:1.6.3-1ubuntu2) ...
Processing triggers for libc-bin (2.23-0ubuntu5) ...
kris@kris-Z97X-UD3H:~/Downloads/nwnnative$ 
kris@kris-Z97X-UD3H:~/Downloads/nwnnative$ ./nwmovies_install.pl build
NOTICE: NWMovies: Executing:
gcc -m32  -I/emul/ia32-linux/usr/include -L/emul/ia32-linux/usr/lib -L/emul/ia32-linux/lib -L/lib32 -L/usr/lib32 -Wall -Inwmovies/libdis -g -fPIC -shared -Wl,-soname,libdisasm.so nwmovies/libdis/libdis.c nwmovies/libdis/i386.c -o nwmovies/libdis/libdisasm.so
nwmovies/libdis/i386.c: In function ‘apply_seg’:
nwmovies/libdis/i386.c:347:21: warning: variable ‘reg’ set but not used [-Wunused-but-set-variable]
  unsigned int type, reg = 0;
                     ^
NOTICE: NWMovies: Executing:
gcc -m32  -I/emul/ia32-linux/usr/include -L/emul/ia32-linux/usr/lib -L/emul/ia32-linux/lib -L/lib32 -L/usr/lib32 -Wall -shared -g -I/usr/include/libelf -Inwmovies/libdis -o nwmovies/nwmovies.so nwmovies/nwmovies.c nwmovies/nwmovies_lookup.c nwmovies/nwmovies_cookie.c nwmovies/nwmovies_link.S  -ldl -Wl,-static -lelf -Wl,-Bdynamic
nwmovies/nwmovies_lookup.c:18:20: fatal error: libelf.h: No such file or directory
compilation terminated.
nwmovies/nwmovies_cookie.c:17:20: fatal error: libelf.h: No such file or directory
compilation terminated.
ERROR: child exited with value 1
ERROR: system() call failed.
kris@kris-Z97X-UD3H:~/Downloads/nwnnative$ 

```

---

### Post by Perfect Storm on 2017-02-07
and if it complains again about libelf do:
```
sudo apt-get install libelf-dev:i386
```

at least it doesn't complain about libsdl anymore.

---

### Post by Kris_M on 2017-02-07
yep.  now let me try to continue with those instructions.

```
kris@kris-Z97X-UD3H:~/Downloads/nwnnative$ sudo apt-get install libelf-dev:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  ksh libcunit1 libjavascriptcoregtk-1.0-0 libqt4-designer libqt4-help
  libqt4-opengl libqt4-scripttools libqt4-svg libqt4-test
  libqtassistantclient4 libqtwebkit4 libunique-3.0-0 libvdpau1:i386
  libwebkitgtk-1.0-0 libwebkitgtk-1.0-common linux-headers-4.4.0-31
  linux-headers-4.4.0-31-generic linux-image-4.4.0-31-generic
  linux-image-extra-4.4.0-31-generic mesa-vdpau-drivers:i386 python-qt4
  python-sip vdpau-driver-all:i386
Use 'sudo apt autoremove' to remove them.
The following NEW packages will be installed:
  libelf-dev:i386
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 59.2 kB of archives.
After this operation, 298 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu xenial/main i386 libelf-dev i386 0.165-3ubuntu1 [59.2 kB]
Fetched 59.2 kB in 0s (654 kB/s)         
Selecting previously unselected package libelf-dev:i386.
(Reading database ... 261957 files and directories currently installed.)
Preparing to unpack .../libelf-dev_0.165-3ubuntu1_i386.deb ...
Unpacking libelf-dev:i386 (0.165-3ubuntu1) ...
Setting up libelf-dev:i386 (0.165-3ubuntu1) ...
kris@kris-Z97X-UD3H:~/Downloads/nwnnative$ 
kris@kris-Z97X-UD3H:~/Downloads/nwnnative$ ./nwmovies_install.pl build
NOTICE: NWMovies: Executing:
gcc -m32  -I/emul/ia32-linux/usr/include -L/emul/ia32-linux/usr/lib -L/emul/ia32-linux/lib -L/lib32 -L/usr/lib32 -Wall -Inwmovies/libdis -g -fPIC -shared -Wl,-soname,libdisasm.so nwmovies/libdis/libdis.c nwmovies/libdis/i386.c -o nwmovies/libdis/libdisasm.so
nwmovies/libdis/i386.c: In function ‘apply_seg’:
nwmovies/libdis/i386.c:347:21: warning: variable ‘reg’ set but not used [-Wunused-but-set-variable]
  unsigned int type, reg = 0;
                     ^
NOTICE: NWMovies: Executing:
gcc -m32  -I/emul/ia32-linux/usr/include -L/emul/ia32-linux/usr/lib -L/emul/ia32-linux/lib -L/lib32 -L/usr/lib32 -Wall -shared -g -I/usr/include/libelf -Inwmovies/libdis -o nwmovies/nwmovies.so nwmovies/nwmovies.c nwmovies/nwmovies_lookup.c nwmovies/nwmovies_cookie.c nwmovies/nwmovies_link.S  -ldl -Wl,-static -lelf -Wl,-Bdynamic


NOTICE: NWMovies: Please check for errors above
NOTICE: NWMovies: nwmovies executable built. Please modify your nwn startup command to
NOTICE: NWMovies: set LD_PRELOAD to 'nwmovies.so', before executing nwmain.
kris@kris-Z97X-UD3H:~/Downloads/nwnnative$ 

```

---

### Post by Perfect Storm on 2017-02-07
oh good. Please report back :)

---

### Post by Kris_M on 2017-02-07
okay.
spent an hour on this so far.
figured out I had to take the bin files from gog. but don't think that's right. None of the links given give me a bin.
Have no idea how or what to execute as an install.
Break time.
Thanks.

---

### Post by Perfect Storm on 2017-02-07
I don't have the game but as far I can understand comes the .bin files from the CDs.

---

### Post by Kris_M on 2017-02-07
> **Artificial Intelligence said:**
> I don't have the game but as far I can understand comes the .bin files from the CDs.

Okay, if that is true, that would put a block to the whole effort since the CDs are something like 1.0.1 and the only functional version is 1.69 (now only avail from GOG - which I have), and there is no longer any way to update it as there used to be - the servers are gone.  

I think I had heard long back that BIOWARE tried and then scrapped native linux as there were just too many problems.

I will drop this and restore my system with clonezilla and go back to trying to figure which file or folder is the one causing it so I can just restore that folder when the problem occurs.
It should be fairly easy to install it, back up what it creates, and use that to "fix" the one in use.

Thanks for your time!

---

### Post by oldrocker99 on 2017-02-07
[https://ubuntuforums.org/showthread.php?t=2082534&highlight=nwn+movies](https://ubuntuforums.org/showthread.php?t=2082534&highlight=nwn+movies) is an exhaustive guide on getting NWN fully installed with all the movies working. I've been playing NWN since 2008, and the Linux engine performs very well indeed for a 2003 program.

The servers are up, by the way, and the commands in that thread still work for 12.04, 14.04, and 16.04. Give it a shot.

---

### Post by Kris_M on 2017-02-07
This was written in 2012 when I believe the BIOWARE servers for update still worked.  For a while there were sporadic replacement sites that supposedly worked, but I suggest that these instructions will not work today.

edit - it's also my understanding that the 1.69 update exists only as a windows exe file.

Thanks anyway.

nwdownloads.bioware.com doesn't respond

---

