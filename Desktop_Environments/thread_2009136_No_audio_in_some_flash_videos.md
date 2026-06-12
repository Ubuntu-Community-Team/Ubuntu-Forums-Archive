---
title: "No audio in some flash videos"
date: 2012-06-24
forum: Desktop Environments
---

### Post by LanceHaverkamp on 2012-06-24
Some youtube audio works in Windows, but not in Xubuntu 12.04:

Example: [https://www.youtube.com/watch?v=takXtjDrZkA](https://www.youtube.com/watch?v=takXtjDrZkA)
Some videos have good audio, others (like this one) are EXTREMELY quiet in Xubuntu, but OK on Windows.

Tried both Chromium & Firefox, Flash version 11,2,202,236 installed

Any idea what's going on here?

Thanks,
Lance

---

### Post by carl4926 on 2012-06-24
I just tried it - But I'm on my SUSE install
It works fine though
I'll check Ubuntu. BRB

---

### Post by carl4926 on 2012-06-24
Yes
Works in 12.04 too

---

### Post by carl4926 on 2012-06-24
Only thing I can say is
On my R61 with Ubuntu it needed the volume really high. SLED didn't need that.

---

### Post by anaconda on 2012-06-24
works well with my xubuntu 12.04
And I have the same flash version than you.

Have you tried older versions of flash? Or do you think old version would be too much of a security "risk"?

Older versions can be found here:
[http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html](http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html)

All you need to do to change flash version is to copy the version you want to here:
/usr/lib/flashplugin-installer/libflashplayer.so
And restart your browser..
Actually I have several versions of flash on that folder. I just renamed the libflashplayer.so files to something else, with the flash version on the name, and then I just make a symlink named "libflashplayer.so" which points to the version I want to use.

For example I sometimes use the flash version "10" (10r15_3) from that page. You can find the libflashplayer.so file by unzipping the archive...
Flash version 10 was the last one, which saved the tmp files to the /tmp folder. It made saving youtube videos really easy. Just copying them from /tmp to wherever I want...
Version 10 is also faster than the newest version. Another reason I sometimes use it if I have problems watching fullscreen flash videos with the most recent player..

PS. flash versions 9 and older dont work with pulseaudio, so you would either need alsa, or not to use them....

---

