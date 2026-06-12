---
title: "32x32 tiles don't work in GnomeHack!"
date: 2008-05-16
forum: Gaming &amp; Leisure
---

### Post by Tycho1214 on 2008-05-16
I'm running 8.04 Hardy, and I installed Gnome-Nethack via Synaptic.  I have a large LCD, resolution is 1440x900, so the default 16x16 tiles were hard on my eyes,  I decided to switch to the 32x32 tiles, but when I did, GnomeHack simply disappeared, as if it had been shut down.  And now whenever I try to start it up again it refuses to work at all - not even an error message, just nothing.  When I go into bash terminal and try to start it from there, it complains about a file called perm_lock in /var/games/nethack/.  I go to that directory and remove that file, and GnomeHack will start up again.  Anyone have any idea what is going on here? I'd really like to be able to use that large tileset.

EDIT: I can only start it through bash terminal now.  The menu link does not work.  Correction: There is a nethack-gnome in the Processes under System Monitor when I use the menu link, but no window.  Apparently it WILL start, but it won't start properly.

---

### Post by csi_ on 2008-05-17
I can reproduce the bug, it appears there is a pixmap file missing (/usr/lib/games/nethack/t32-1024.xpm) in nethack-gnome package. Console gives:

 ** ERROR **: Couldn't load required xpmFile!

You might find t32-1024.xpm in an older release, a package from another distro, or replace it with other graphics. Some example is given here: [http://nemaru.at.infoseek.co.jp/jnethack.html](http://nemaru.at.infoseek.co.jp/jnethack.html) but my japanese is not so good.

More info on the issue: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=140398](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=140398)

Let us know how you fix it.

---

### Post by Tycho1214 on 2008-05-17
[http://changelogs.ubuntu.com/changelogs/pool/universe/n/nethack/nethack_3.4.3-10ubuntu2/changelog](http://changelogs.ubuntu.com/changelogs/pool/universe/n/nethack/nethack_3.4.3-10ubuntu2/changelog)

That mentions t32-1024.xpm from jnethack not working in 3.4.3.  guess I have to locate the .xpm in a prev version.

Edit: I thought I would be clever, and simply download the 32x32 tiles for the Windows version of NetHack 3.4.3, and convert the file to an XPM and rename it t32-1024.xpm, and then place it in the specified folder.  Still didn't work.

---

