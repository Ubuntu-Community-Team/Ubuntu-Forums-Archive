---
title: "libnotify popups not displayed properly (grey without transparency)"
date: 2009-04-28
forum: General Help
---

### Post by darthmob on 2009-04-28
in short: the popups of the [new notification system in ubuntu 9.04]("http://www.markshuttleworth.com/archives/265") are not black and transparent but look like the classic ones.

a screenshot:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=111508&stc=1&d=1240908975[/IMG]

my specs:
ubuntu 9.04, [gnome/openbox]("http://icculus.org/openbox/index.php/Help:GNOME/Openbox"), [xcompmgr -n]("http://wiki.archlinux.org/index.php/Xcompmgr") for basic desktop effects

does anyone have a similar problem or knows what may help? thanks in advance!


//EDIT:

the solution is:
uninstall notification-daemon
install notify-osd

---

### Post by darthmob on 2009-04-29
giving this a gentle bump in the morning..

:KS (that's a happy looking star!)

---

### Post by darthmob on 2009-04-29
a gentle bump in the evening..

:KS :KS (look! another happy star!)

---

### Post by josephellengar on 2009-04-29
> **darthmob said:**
> in short: the popups of the [new notification system in ubuntu 9.04]("http://www.markshuttleworth.com/archives/265") are not black and transparent but look like the classic ones.

a screenshot:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=111508&stc=1&d=1240908975[/IMG]

my specs:
ubuntu 9.04, [gnome/openbox]("http://icculus.org/openbox/index.php/Help:GNOME/Openbox"), [xcompmgr -n]("http://wiki.archlinux.org/index.php/Xcompmgr") for basic desktop effects

does anyone have a similar problem or knows what may help? thanks in advance!

Do you have the notify-osd package installed?

---

### Post by darthmob on 2009-05-08
> **idigchess said:**
> Do you have the notify-osd package installed?sorry I did not see your post. the problem was that I had both notify-osd and notification-daemon installed.

the solution is:
uninstall notification-daemon
install notify-osd

---

### Post by juliobahar on 2009-06-06
> **darthmob said:**
> sorry I did not see your post. the problem was that I had both notify-osd and notification-daemon installed.

the solution is:
uninstall notification-daemon
install notify-osd

Thank you pal, this solved my problem. I've upgrade to Jaunty from Intrepid and & the same classical notification daemon was used all the time. After surfing here and there, your solution did the job.

USE SYMANTICS:
uninstall notification-daemon
&
Install notify-osd

Thanks again.

---

