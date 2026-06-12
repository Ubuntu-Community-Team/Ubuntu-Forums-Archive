---
title: "vdrift segmentation fault (core dump)"
date: 2007-05-30
forum: Gaming &amp; Leisure
---

### Post by chinaski on 2007-05-30
hello,

I've just installed Vdrift but when I try to run it that's what I get:

```

acp@central:~$ vdrift -verbose
BinReloc successfully initialized.
Executable path: /usr/share/games/vdrift/bin/vdrift
Data dir: /usr/share/games/vdrift/data
Localedir: /usr/share/games/vdrift/share/locale
No data_dir found in VDrift.config, using /usr/share/games/vdrift/data
Found config file /home/acp/.vdrift/controls.
Found config file /home/acp/.vdrift/VDrift.config.
No data_dir found in VDrift.config, using /usr/share/games/vdrift/data
Version of game: 2007-03-23
Skin name not found in config file...
/usr/share/games/vdrift/share/locale
Warning: option-47 is missing its default value. Assuming "".
Force feedback device: /dev/input/event0
Force feedback gain: 2
Force feedback inverted: 0
Run with -verbose for troubleshooting.
Run with -nosound to disable sound.
Run with -benchmark to play a replay and output benchmark data.
0 joystick(s) found:
Loading...
Textures
Loading...
Font
Segmentation fault (core dumped)

```I've searched on Vdrift forum and run this command:

```
acp@central:~$ objdump -x /usr/bin/vdrift | grep NEEDED
  NEEDED      libSDL-1.2.so.0
  NEEDED      libpthread.so.0
  NEEDED      libGL.so.1
  NEEDED      libGLU.so.1
  NEEDED      libSDL_image-1.2.so.0
  NEEDED      libSDL_net-1.2.so.0
  NEEDED      libstdc++.so.6
  NEEDED      libm.so.6
  NEEDED      libc.so.6
  NEEDED      libdl.so.2

```then I run sudo apt-get install the_whole_lot but it says it couldn't find libSDL-1.2.so.0, so I just removed it from the list (just as a try) but it can't find second package as well, so I stopped and here I am posting

what could the problem be?

---

### Post by fakie_flip on 2007-06-04
You need to find the packages that contain those lib files.

[http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=libSDL-1.2.so.0&searchmode=searchfiles&case=insensitive&version=feisty&arch=i386](http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=libSDL-1.2.so.0&searchmode=searchfiles&case=insensitive&version=feisty&arch=i386)

---

### Post by Cappy on 2007-06-04
Are you using Ubuntu 64?
If so, you need to 
```
sudo apt-get install ia32-libs*
```

---

