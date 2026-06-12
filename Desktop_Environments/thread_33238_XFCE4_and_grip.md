---
title: "XFCE4 and grip"
date: 2005-05-10
forum: Desktop Environments
---

### Post by Brunellus on 2005-05-10
Stupid question:

I'm trying to run grip in XFCE4, but I keep getting a "could not initialize /dev/cdrom" warning message.

This is weird, since grip runs just fine in gnome and fluxbox on the very same computer, without any tweaking or fiddling. 

pointing grip to use /dev/cdrom0 in its options dialog does nothing--I just get a nice note to the effect that /dev/cdrom0 can't be initialized the next time I start grip.

Oddly, Soundjuicer works *just fine*--but runs as molasses-slow as it usually does.  I'd come to like grip because it's much faster & more efficient (for me) than soundjuicer.

anybody have any ideas?

---

### Post by harryc on 2005-05-10
Maybe it just needs to be mounted. Try running;

```
gnome-volume-manager &
```

Save your session on logout so that it loads each time. It will automount your drives.

---

### Post by Brunellus on 2005-05-10
I reverse my previous statement:  grip no longer works in flux *either*.

Anyway, I tried gnome-volume-control (which turns out to be just the gnome audiomixer) and gnome-volume-manager (the automount utility) and no joy-- grip refuses to believe /dev/cdrom is there.  Soundjuicer does, but, again, it's dog-slow compared to grip, and I had come to prefer grip anyway.  

*sigh*  It worked *great* before I updated from warty to hoary.  I can't work out why it's changed.

grip seems to be the only app that's misbehaving in this way. I can mount and use data cdroms with no problem whatsoever, any way I'd like (via gvm, via the commandline, via xffstab)

---

