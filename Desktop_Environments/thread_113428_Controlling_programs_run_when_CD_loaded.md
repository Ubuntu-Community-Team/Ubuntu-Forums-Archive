---
title: "Controlling programs run when CD loaded"
date: 2006-01-06
forum: Desktop Environments
---

### Post by steevc on 2006-01-06
When I load a CD into my drive I get a Konqueror window, Soundjuicer and KsCD all starting up. I don't really want all those. Where do I change this in KDE?

I have a similar issue when inserting a memory card with photos. I prefer to use Digikam, but I get a pop-up asking if I want to transfer the pictures.

Thanks

---

### Post by gingermark on 2006-01-06
[http://www.ubuntuforums.org/showthread.php?t=90457](http://www.ubuntuforums.org/showthread.php?t=90457)

---

### Post by steevc on 2006-01-06
Okay, so editing some stuff out of /etc/ivman/IvmConfigActions.xml made KsCD go away, but I can't see anything in there about Soundjuicer or the photo load option. Those are still popping up.

Anywhere else I should look?

Thanks

---

### Post by nandasunu on 2006-01-06
try going to- System Settings: Storage Media, click the "Advanced" tab, deselect "Enable medium autostart after mount". This works for me.

---

### Post by steevc on 2006-01-06
I can't see Storage Media in my System Settings. There's Disk and Filesystems, but that has no Advanced tab.

There's something wrong with System Settings in general. Some options I can't go into more than once as I get an error saying it is already open, but can't get back to it.

Maybe I'm just missing something.

---

### Post by steevc on 2006-01-12
I eventually worked it out. Even though I am running KDE I still get Gnome trying to do it's thing. In Gnome Control Centre I went into Removable Drives and Media and unchecked everything. This probably mean I won't get much if I ever run Gnome.

BTW How much Gnome stuff should be running when I'm in KDE? I can see Nautilus is running.

Thanks

---

