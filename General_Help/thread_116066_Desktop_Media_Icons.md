---
title: "Desktop Media Icons"
date: 2006-01-11
forum: General Help
---

### Post by Mazin on 2006-01-11
On the KDE desktop, i explicitly turned on icons for every media type, but a lot of them don't show up. The floppy icon shows up, and some CDs do, but hard drives and other things never do. I think it might have something to do with the fact that I installed KDE over the normal Ubuntu distro. Is there something I need to change/configure/install?

---

### Post by sharke on 2006-01-12
Right click on desktop select ceate new>link to device and select which device you need,
Regards
Sharke

---

### Post by Mazin on 2006-01-12
Shouldn't it automatically show mounted/unmounted storage devices?  I don't think linking would be the same.

---

### Post by sharke on 2006-01-12
I did a disk install of kubuntu and i did not have icons on desktop though they would show when you have a disk inserted in drive.
Regards
Sharke

---

### Post by Mazin on 2006-01-13
On knoppix, KDE will show all the hard drives and everything, with context menus for mounting, unmounting, etc.  Why won't it work in kubuntu?

---

### Post by stimpsonjcat on 2006-01-14
which version of kdebase-kio-plugins are you using? I had a similar problem and downgrading kdebase-kio-plugins to version 4:3.4.3-0ubuntu4 solved it.

---

### Post by Mazin on 2006-01-14
I have kdebase-kio-plugins version 4:3.4.3-0ubuntu6

what's the best way to downgrade it?

---

### Post by stimpsonjcat on 2006-01-15
[QUOTE=Mazin]what's the best way to downgrade it?[/QUOTE]
As far as I know, Adept does not support downgrading packages. You can use Synaptic or edit the /etc/apt/preferences file by hand. See this: [http://www.linuxquestions.org/questions/showthread.php?t=400200](http://www.linuxquestions.org/questions/showthread.php?t=400200)

---

### Post by dentaku65 on 2006-01-16
Try
right click on the desktop:
configure desktop -> Behavior -> Device icons tab
Then choose what icons do you want to display permanently

Enjoy

---

