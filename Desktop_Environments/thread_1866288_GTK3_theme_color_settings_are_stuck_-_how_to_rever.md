---
title: "GTK3 theme color settings are stuck - how to revert to default ones?"
date: 2011-10-21
forum: Desktop Environments
---

### Post by panaut0lordv on 2011-10-21
Hello,
I've already tried reinstalling themes, cleaning caches and so on,
but settings of eg. text colour or some backgrounds are stuck.
Example of how the bug looks is in the attachment with Ambiance set.

Actually I think it's due to my customized themes in 11.04 Classic Desktop (gnome2) which seem to be stuck after upgrade to 11.10 and Unity, but I can't manage to find the place where it could be.
I've removed all files in ~/.themes

Thanks in advance for your help.

---

### Post by _Impact_ on 2011-10-24
Hey I have the same problem just started a new thread and waiting for a reply...

---

### Post by merlinus on 2011-10-24
You might look in /usr/share/themes, but to delete them you will need to do so as root.

---

### Post by _Impact_ on 2011-10-24
Deleting them does not help...

The solution should be somewhere in one of these two folders I think:

/home/USER/.themes
or
/usr/share/themes

---

### Post by vasa1 on 2011-10-24
> **panaut0lordv said:**
> ...
Actually I think it's due to my customized themes in 11.04 Classic Desktop (gnome2) which **seem to be stuck** after upgrade to 11.10 and Unity...

I've not had that experience. I'd have been happy if my old color choices were retained after the upgrade to 11.10. They were all gone. And I've had to struggle a bit editing gtk.css and settings.ini to get things the way I like them. The Gnome tweak tool helps as well to some extent.

---

### Post by panaut0lordv on 2011-10-24
I've found this thread [http://ubuntuforums.org/showthread.php?t=1837831](http://ubuntuforums.org/showthread.php?t=1837831) but actually this is not real solution, because I don't want to lose my whole .gconf and .cache.
If someone could tell us, where are all theme and colouristic settings stored, then it would be more convenient for us ;)

---

### Post by jalberro on 2011-10-24
You can solve all the problems of Unity with this 

[http://ubuntuforums.org/showpost.php?p=11386080&postcount=4](http://ubuntuforums.org/showpost.php?p=11386080&postcount=4)

---

### Post by _Impact_ on 2011-10-24
> **jalberro said:**
> You can solve all the problems of Unity with this 

[http://ubuntuforums.org/showpost.php?p=11386080&postcount=4](http://ubuntuforums.org/showpost.php?p=11386080&postcount=4)

Thanks, that's exactly what I needed. Can anybody explain the process behind this command?

---

### Post by panaut0lordv on 2011-10-25
Actually you can bring your old dconf user profile back and the option that was responsible for my bug was:
Dconf Editor -> org.gnome.desktop.interface.gtk-color-scheme
After reverting it to default, it stops overriding Unity appearance settings and everything is cool ;)

---

