---
title: "libdvdread error with xine"
date: 2007-03-17
forum: Desktop Environments
---

### Post by ebike on 2007-03-17
Hi All,

I just finished a re-installation of mythtv to my brand new Ubuntu box from initially a gentoo box.

Mostly everything is working except DVD playback and a mono issue.

The problem is I get this error from libdvdread while trying to play a DVD.

> libdvdread: Could not open input: Permission denied
libdvdread: Can't open /dev/hda1 for reading
libdvdread: Device /dev/hda1 inaccessible, CSS authentication not available.
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdread: Encrypted DVD support unavailable.
2007-03-18 10:06:41.342 Connecting to backend server: 192.168.0.3:6543 (try 1 of 5)
2007-03-18 10:06:41.437 Using protocol version 31


I do not know why it is trying to access my hard-disk /dev/hda1 instead of my cdrom on /dev/cdrom ?? I cannot see any config options to tell libdvdread where to look.

Can anyone help with this. I will open another thread on the mono issue.

Thanks.

---

### Post by adibudeen on 2007-03-19
> libdvdread: Encrypted DVD support unavailable

That seems to be the key.  Have you installed libdvdcss2?  That is the only way to read encrypted DVDs.

With Xine, you'll need to enable "master of the known universe" or whatever it's called to see the settings under "device" where you can tell it where your dvd drive is.  I don't have Xine on this computer, so I can't tell you exactly what it is, but you'll see it after you enable viewing of all of the setup options.

---

