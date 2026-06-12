---
title: "Pulseaudio causing bad lag"
date: 2009-03-11
forum: General Help
---

### Post by Irishbmx on 2009-03-11
Ok so I had some sound problem I tryd a bunch of different stuff and changed a buncha different stuff in the end I just put a new sound card in.

Before I put the new sound card in a ran into some off problem with pulseaudio I'm not sure what I did but for some reason it causes my internet to lag out really bad all I can do to stop the lag is go into system monitor and kill pulseaudio but when I do that I lose sound :( anyone have any idea what I can do to fix pulseaudio?

Ok I am running Ubuntu 8.04 32 bit on an xfx geforce 8200 MB AM2 AMD 64 bit

I also have Pulseaudio device chooser installed.

---

### Post by Vince4Amy on 2009-03-11
Try System>Preferences>Sessions

Uncheck Pulseaudio, it might make a difference, if you loose sound re enable it. Log Out and Log back in again after making changes.

---

### Post by Irishbmx on 2009-03-11
> **Vince4Amy said:**
> Try System>Preferences>Sessions

Uncheck Pulseaudio, it might make a difference, if you loose sound re enable it. Log Out and Log back in again after making changes.

Well I didn't lose audio but didn't seem to fix it, but thanks.

---

### Post by Irishbmx on 2009-03-11
Ok I think I found out what the issue is still wanna know if theres a way to fix it.

found this post
[http://ubuntuforums.org/showthread.php?t=828935](http://ubuntuforums.org/showthread.php?t=828935)

and when I disable multicast I lose the lag and my internet runs fine.
any ideas?

---

