---
title: "Trouble w/ libgtk-1.2.so.0"
date: 2007-12-26
forum: Gaming &amp; Leisure
---

### Post by transitional on 2007-12-26
I'm trying to install the game Uplink by Introversion, and am having some troubles. I can install the game perfectly except that the installer keeps complaining about one thing...
```

Verifying archive integrity... All good.
Uncompressing Uplink full 1.31.................................................
...................
/home/tommy/.setup11313: error while loading shared libraries: libgtk-1.2.so.0:
cannot open shared object file: No such file or directory
Press Return to close this window

```
I've searched far and wide for this library, to no avail. On other threads about similar problems, I've seen solutions such as libgtx1.2-common, but none of those work for me.

I'm running Ubuntu 7.10 i386 (which is 32-bit, right?) and the game is 32-bit also. But, this "libgtk-1.2.so.0" doesn't seem to be available for i386.

Is there someway to fix this problem? The only immediately apparent options are to remove dependency on the library (which would be nearly impossible; I'm not much of a coder) and to get the library (which, as explained, is unavailable).

Also, I am working with a Linux release of Uplink, though I have tried the Windows version through Wine.I got a generic "encountered a problem, had to close" error.

---

### Post by Cappy on 2007-12-27
That is ```
sudo apt-get install libgtk1.2 libglib1.2
```

You can use getlibs [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790) to save yourself the trouble of looking up the library or you can go to [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and "Search the contents of packages" to find it. Other alternatives are apt-file (given the name of a file it tells you what package) and auto-apt (think it can solve dependencies even though that is a shell install).

---

