---
title: "Can't get totem to play DVD"
date: 2006-08-08
forum: Desktop Environments
---

### Post by chloraldo on 2006-08-08
I'm trying to make totem play a DVD with the filestructure:
- AUDIO_TS
- VIDEO_TS

I get an error message:
[I]Totem was not able to play this disc.
Failed to open device /dev/scd0 for reading: permission denied.[/I]

Any ideas? Any help? Would be great!

---

### Post by computergroove on 2006-08-08
> Failed to open device /dev/scd0 for reading: permission denied.

First thing I would try is editing /etc/fstab and add read access to the drive. Try it and reply.

---

### Post by Dubbayoo on 2006-08-08
try doing it as root just to see if perms is really the issue.

---

### Post by chloraldo on 2006-08-09
This is the entry in /etc/fstab:
*/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0*

This is the error message I get if I open Totem with sudo and try to play the DVD:
[I]Totem could not play 'dvd:/'.
The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?[/I]

I found some messages in the terminal which I had used to open totem as root:
[I]** (totem:17735): WARNING **: Failed to connect to the session bus: No reply wit hin specified time
closing
closing
closing
closing
libdvdnav: Using dvdnav version 1.1.1 from [http://xine.sf.net](http://xine.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Could not open /dev/scd0 with libdvdcss.
libdvdread: Can't open /dev/scd0 for reading
libdvdnav: vm: faild to open/read the DVD
libdvdnav: Using dvdnav version 1.1.1 from [http://xine.sf.net](http://xine.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Could not open /dev/scd0 with libdvdcss.
libdvdread: Can't open /dev/scd0 for reading
libdvdnav: vm: faild to open/read the DVD[/I]

---

### Post by mg3kc on 2006-08-09
Out of curiosity, do DVDs work using any other programs (Ogle is another DVD player to try)?

You could try updating libdvdcss to libdvdcss2...

---

### Post by chloraldo on 2006-08-09
Ogle didn't do anything for me and I didn't find libdvdcss, only libdvdcss2...

---

### Post by mg3kc on 2006-08-09
Are you having problems playing regular CDs through Totem as well, or do they work ok? 
If they work, you can try loading the DVD by using the open location option, and opening /media/cdrom0

---

