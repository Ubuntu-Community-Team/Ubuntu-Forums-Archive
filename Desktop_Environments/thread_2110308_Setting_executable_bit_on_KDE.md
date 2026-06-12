---
title: "Setting executable bit on KDE"
date: 2013-01-29
forum: Desktop Environments
---

### Post by llanitedave on 2013-01-29
I have a Python program that I run at various times from three different desktops:  Windows 7, Xubuntu, and Kubuntu.  It resides on a common NTFS partition accessible from all three.

In Windows 7 and Xubuntu, I need only double click on the program icon or shortcut, and it opens with no issues.  On KDE, though, it insists on opening up into the default programming editor nd being run from there.

Checking the Properties of the file, the executable bit is not set on KDE, and it doesn't want to set manually.  If I set it manually, it goes back to unset as soon as I leave the window.  It IS set when I look at it through Xfce, though.

I really thought this was a file property, not a DE property.  Why is it set on one environment but not the other?  I should have the same privileges on each, unless KDE has a different privilege system.

And in case anyone asks, yes the "#!/usr/bin/env python" shebang line is in place.

---

### Post by steeldriver on 2013-01-29
I think the difference will likely turn out to be how the NTFS partition is *mounted* under the different environments - since NTFS doesn't understand unix-style permissions, the permissions have to be set globally at mount time (e.g. via the fstab umask)

---

### Post by llanitedave on 2013-01-29
That idea never crossed my mind.  I'll take a look!

---

### Post by llanitedave on 2013-01-29
OK, the fstab in my Xubuntu partition reads:
```
#Entry for /dev/sda6 :
UUID=0AEC9CD8EC9CBF7F	/media/Win_Lin_Share	ntfs-3g	defaults,locale=en_US.UTF-8	0	0
```

On my KDE partition, there is no line for any ntfs partition at all.

Would it be safe to copy it over, and ... would it make a difference?

---

