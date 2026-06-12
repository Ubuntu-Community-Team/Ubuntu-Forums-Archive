---
title: "mplayer refuses to play dvds"
date: 2005-12-05
forum: Desktop Environments
---

### Post by Dark_Link2135 on 2005-12-05
ive downloaded both the libdvdcss and libdvdread3 libraries, but i still get this output using 'mplayer dvd://1'

> 86 audio & 200 video codecs
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0 : No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing dvd://1.
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Could not open /dev/dvd with libdvdcss.
libdvdread: Can't open /dev/dvd for reading
Couldn't open DVD device: /dev/dvd
File not found: '1'
Failed to open dvd://1

any idea why?

---

### Post by Manny C on 2005-12-05
Supposedly Ogle is a good DVD player for Gnome desktop environment. Have you tried the suggestions on [Ubuntu Doc Storage]("http://doc.gwos.org/index.php/BreezyCust").

The site is currently down. But it has some good instructions regarding setting up DVD playback support.

---

### Post by Dark_Link2135 on 2005-12-05
[QUOTE=Manny C]Supposedly Ogle is a good DVD player for Gnome desktop environment. Have you tried the suggestions on [Ubuntu Doc Storage]("http://doc.gwos.org/index.php/BreezyCust").

The site is currently down. But it has some good instructions regarding setting up DVD playback support.[/QUOTE]

I have ogle installed but I get the same thing:

> root@Infiniti:~# sudo ogle
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Could not open /dev/dvd with libdvdcss.
libdvdread: Can't open /dev/dvd for reading
ERROR[ogle_nav]: faild to open/read the DVD
DVDSetDVDRoot:: Root not set

---

