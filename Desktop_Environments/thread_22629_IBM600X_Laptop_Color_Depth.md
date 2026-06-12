---
title: "IBM600X Laptop Color Depth"
date: 2005-03-28
forum: Desktop Environments
---

### Post by Frihet on 2005-03-28
I've just installed Kubuntu on my old IBM600X laptop.  I could not get Gnome to start reliably.  KDE starts just fine.  The machine is working well except ..(it's always something).

How do I set the color depth?  I'm almost sure the install defaulted to 1024X768 24bits.  The old 600X presents artifacts at 24 bits.  How do I wind it down to 16 bit color?

Thanks!!

---

### Post by Randabis on 2005-03-28
[QUOTE=Frihet]I've just installed Kubuntu on my old IBM600X laptop.  I could not get Gnome to start reliably.  KDE starts just fine.  The machine is working well except ..(it's always something).

How do I set the color depth?  I'm almost sure the install defaulted to 1024X768 24bits.  The old 600X presents artifacts at 24 bits.  How do I wind it down to 16 bit color?

Thanks!![/QUOTE]
 One way would be to edit /etc/X11/xorg.conf...

Find this section...

```
Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV35 [GeForce FX 5900]"
        Monitor         "Generic Monitor"
        DefaultDepth    24

```

Change DefaultDepth to 16. Save, then restart the xserver.

---

### Post by Frihet on 2005-03-28
Yep, that's what it is.  I can read the file.  However, I can't run Kate from a sudo terminal session.  Kate crashes.  Now I need to figure out how to log on as root so I can edit the file.

Also, I ran the update/upgrade and killed the machine (KDE inoperative).  So I'm starting a new install.  I won't update, then I'll try to get root.

Thanks!!

---

### Post by Frihet on 2005-03-28
On the KDE problem, the panel does not appear.  I just get a white bar at the bottom of the screen.  It's fine before I update.  So, I quess I'll also have to figure out how to update everything but KDE.

I'm reinstalling from CD now.

---

### Post by Randabis on 2005-03-28
[QUOTE=Frihet]On the KDE problem, the panel does not appear.  I just get a white bar at the bottom of the screen.  It's fine before I update.  So, I quess I'll also have to figure out how to update everything but KDE.

I'm reinstalling from CD now.[/QUOTE]
 you could have used nano...:p

OH well, you're reinstalling now anyway.

---

