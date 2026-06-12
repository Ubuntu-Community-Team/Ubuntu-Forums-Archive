---
title: "Very interesting &quot;automount&quot; idea for Kubuntu!"
date: 2005-04-04
forum: Desktop Environments
---

### Post by sb73542 on 2005-04-04
[http://code.mizzenblog.com/thing/ivman](http://code.mizzenblog.com/thing/ivman)

This looks really slick!  Notice the photos toward the bottom of the page, showing the KDE hardware event notification.  The HAL/D-bus/Ivman combo is already being used by CCux Linux.  This would be a great alternative for the gnome-volume-manager.

Any developers?  What do you think?  Thanks!

---

### Post by aramazan on 2005-04-05
[QUOTE=sb73542][http://code.mizzenblog.com/thing/ivman](http://code.mizzenblog.com/thing/ivman)[/QUOTE]Great idea! Developers are already looking for a way and I guess they'll be interested in this. From [http://www.ubuntulinux.org/wiki/KubuntuTODO](http://www.ubuntulinux.org/wiki/KubuntuTODO) ::

* Autoplug/mount stuff with dbus notifcation - we need a similar system for kubuntu. KDE 3.4 has media:/ ioslave with hal backend, requires Qt dbus bindings. (mornfall: media:/ ioslave courtesy of Kevin Ottens from the Kalyxo team)

I would suggest you add this to the comments section of the mentioned wiki page or post it to kubuntu-devel list.

Best regards

---

### Post by sb73542 on 2005-04-05
[QUOTE=aramazan]Great idea! Developers are already looking for a way and I guess they'll be interested in this. From [http://www.ubuntulinux.org/wiki/KubuntuTODO](http://www.ubuntulinux.org/wiki/KubuntuTODO) ::

* Autoplug/mount stuff with dbus notifcation - we need a similar system for kubuntu. KDE 3.4 has media:/ ioslave with hal backend, requires Qt dbus bindings. (mornfall: media:/ ioslave courtesy of Kevin Ottens from the Kalyxo team)

I would suggest you add this to the comments section of the mentioned wiki page or post it to kubuntu-devel list.

Best regards[/QUOTE]
 Thanks for the tips!  I have now posted this to both locations.

---

### Post by aramazan on 2005-04-05
[QUOTE=sb73542]Thanks for the tips!  I have now posted this to both locations.[/QUOTE]Well, I seem to be a bit too late to point this out (sorry), but surfing around ccux web site I've found that they have abandoned hal/dbus/ivman and now going for hal/dbus/kde3.4 solution: [http://babelfish.altavista.com/babelfish/trurl_pagecontent?lp=de_en&trurl=http://forum.ccux-linux.de/ftopic1173.html](http://babelfish.altavista.com/babelfish/trurl_pagecontent?lp=de_en&trurl=http://forum.ccux-linux.de/ftopic1173.html)

---

### Post by sb73542 on 2005-04-05
[QUOTE=aramazan]Well, I seem to be a bit too late to point this out (sorry), but surfing around ccux web site I've found that they have abandoned hal/dbus/ivman and now going for hal/dbus/kde3.4 solution: [http://babelfish.altavista.com/babelfish/trurl_pagecontent?lp=de_en&trurl=http://forum.ccux-linux.de/ftopic1173.html](http://babelfish.altavista.com/babelfish/trurl_pagecontent?lp=de_en&trurl=http://forum.ccux-linux.de/ftopic1173.html)[/QUOTE]
 Huh, looks like you're right, assuming that it survived the translation correctly.  I think ivman might still be a good idea, though.  Gentoo actively uses and supports it.

---

### Post by Cklein on 2005-04-07
I'm a bit confused.... I *come from* gentoo and ivman is working almost perfect, but if kde 3.4 can do it on its own, it's perfect for me.. But is it already working on kubuntu? I mean, I have all hal/dbus/kde3.4 installed and I can mount cd and dvd through konqueror but anyway they don't get automounted like they do with ivman. And also i have to unmount before ejecting the cd/dvd. Can someone explain it in a better way?? Is there already automount at kubuntu?

---

### Post by scarecrow on 2005-04-07
[QUOTE=Cklein]I'm a bit confused.... I *come from* gentoo and ivman is working almost perfect, but if kde 3.4 can do it on its own, it's perfect for me.. But is it already working on kubuntu? I mean, I have all hal/dbus/kde3.4 installed and I can mount cd and dvd through konqueror but anyway they don't get automounted like they do with ivman. And also i have to unmount before ejecting the cd/dvd. Can someone explain it in a better way?? Is there already automount at kubuntu?[/QUOTE]
 Automount, submount, hal/dbus, autofs, ivman, all do pretty much the same thing... since KDE 3.4 supports hal/dbus natively I don't think one should mess with other solutions. Ivman can work on top of a hal/dbus system, but sounds like one program too many.

---

