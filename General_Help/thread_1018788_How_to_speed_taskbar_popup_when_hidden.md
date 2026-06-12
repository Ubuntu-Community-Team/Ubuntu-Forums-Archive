---
title: "How to speed taskbar popup when hidden?"
date: 2008-12-22
forum: General Help
---

### Post by doriard on 2008-12-22
I like to auto-hide the taskbar to maximize desktop space, but under Gnome, the taskbar is very slow to to pop back up.  Is there a way to may a hidden taskbar pop up instantly on moveover?

(KDE 3 let me do this, but there is no new development on KDE 3, and KDE 4 is not ready for prime time.)

Thanks in advance.

---

### Post by Usufruct on 2008-12-22
You can do this.

The easiest way is to open up the gconf-editor (Alt+F2, and run gconf-editor).

The location appears to have changed very slightly from version to version, but in 8.10, navigate to apps/panel/toplevels

This should show you all of the panels you have open.  In the attached screenshot, you can see I'm adjusting the top panel on my second screen.  If you change the values for hide_delay and unhide_delay to 0, I believe you'll achieve the result you're looking for.

Cheers!

---

### Post by doriard on 2008-12-22
This suggestion worked great!  Not only did it solve my taskbar unhide speed problem, but now I know about the gconf-editor, which will be useful for lots of things.  Thank you.

---

### Post by Vantrax on 2008-12-22
Exactly what Usufruct said however you will need to do a gksudo gconf-editor when you hit Alt-F2

You need root permissions to change settings.

---

### Post by Usufruct on 2008-12-23
> **Vantrax said:**
> Exactly what Usufruct said however you will need to do a gksudo gconf-editor when you hit Alt-F2

You need root permissions to change settings.

No you don't, and you won't even see the panels you have set up under your user if you run gconf-editor as root.

---

