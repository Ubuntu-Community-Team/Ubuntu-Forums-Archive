---
title: "How do I change default CD player to XMMS?"
date: 2005-06-24
forum: Desktop Environments
---

### Post by chaumurky on 2005-06-24
The default command for audio CD insertion is:

```
gnome-cd --unique --play --device %d
```

If I want to change this to use XMMS what line (with switches) do I need here?

---

### Post by gnu2tux on 2005-06-24
If you are talking about the desktop, then it's pretty easy:

Go to System > Preferences > Removable Drives and Media Preferences
Click the Multimedia Tab

change the line there to read xmms -p %d and all should be good. If it doesn't work with %d, try replacing %d for /media/cdrom (or whatever your cdrom drive comes up as in the /media folder).

Regards,

Alistair

---

### Post by chaumurky on 2005-06-24
Yes exactly, the Desktop. That was where I got the original line. I just wasn't sure of the switches  for XMMS. It works, thank you Alistair.

---

### Post by merlin666 on 2007-09-07
This does not work for mp3 it seems.

---

