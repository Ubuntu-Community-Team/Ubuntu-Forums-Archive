---
title: "How do I make a link in &quot;computer&quot; to show my windows partition"
date: 2005-07-08
forum: Desktop Environments
---

### Post by adrawer on 2005-07-08
I'm trying to customize my main menu with a link to my windows partition.  I have it already mounted in /mnt/winxp.  Does anyone know how to do this?

---

### Post by titus1950 on 2005-07-08
[QUOTE=adrawer]I'm trying to customize my main menu with a link to my windows partition.  I have it already mounted in /mnt/winxp.  Does anyone know how to do this?[/QUOTE]



Hi,first mount your Win part.in Media,follow this link...
[http://ubuntuguide.org/#automountfat](http://ubuntuguide.org/#automountfat)

Then if it doesn't show in places-computer and desktop,do this: is a little trick...

  /dev/hda1       /media/windows  vfat    iocharset=utf8,umask=000   0       0

  errase the line in front of deb/hda,like this:
  

  dev/hda1       /media/windows  vfat    iocharset=utf8,umask=000   0       0
  and save........

reboot and now windows will show on:Desktop,places-computer,media.

Good luck...

---

