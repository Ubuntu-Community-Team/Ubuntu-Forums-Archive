---
title: "I can't log into kde 4.0, suspecting display driver problem"
date: 2008-07-14
forum: Desktop Environments
---

### Post by gnuvistawouldbecool on 2008-07-14
Hi.

I was just messing around with the display settings, seeing what I could set up(from the system settings in the main menu) enabled desktop effects (i think that's what it was called), and clicked apply.  It then logged out, and when trying to log back in got through all the loading then just went back to the login screen.  

I suspect a display driver issue, so I'm wondering if there happens to be something I can put in the failsafe login to just reset the display settings to default?

The system is a 1.8 GHz processor (AMD64) with an ATi Radeon X200M (I think).

Thanks

---

### Post by gnuvistawouldbecool on 2008-07-14
Otherwise, is it possible to 'repair' the install?  Just I don't really want to start it from scratch again, as I only have limited downloads per month on my broadband connection.

---

### Post by GeneralZod on 2008-07-14
Things like this are very rarely an "install" issue, and almost always a "configuration" issue.

Exit KDE, and using e.g. GNOME, KDE, XFCE or a virtual terminal, delete kwinrc from your <KDE4 home directory>/share/config, then restart KDE4 and see if it works.

---

### Post by gnuvistawouldbecool on 2008-07-14
What exactly is the delete code, is it anything to do with that rm function?

I've never had to delete anything with command line before.

---

### Post by GeneralZod on 2008-07-14
> **gnuvistawouldbecool said:**
> What exactly is the delete code, is it anything to do with that rm function?

I've never had to delete anything with command line before.

Yep, rm :)

So if your KDE4 home directory is ~/.kde4, you would type:

```

rm ~/.kde4/share/config/kwinrc

```

---

### Post by gnuvistawouldbecool on 2008-07-14
Most useful, you have my thanks for that one.

Now if only I'd known that before, thats not the first time I've done that.:)

---

