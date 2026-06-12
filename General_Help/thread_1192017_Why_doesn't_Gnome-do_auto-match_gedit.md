---
title: "Why doesn't Gnome-do auto-match gedit?"
date: 2009-06-19
forum: General Help
---

### Post by cknight on 2009-06-19
I'm reallyt liking gnome-do so far.  However, I'm puzzled by its auto-matching selections.  For example, all I have to do to get opera up is type "o" and there's the opera icon ready to launch.  For gedit, I have to type the full string "gedit" and scroll down to the bottom of a list of potential matches just to get a generic text icon and not a specific gedit icon, which then presumably launches gedit via a terminal command (as I have ther terminal plugin enabled).

So how does it build its matching database and why isn't gedit in it?

Same thing happens with gconf-editor and probably others too.  Seems random to me what it matches and what it doesn't.

---

### Post by TeoBigusGeekus on 2009-06-19
Because gedit is listed as text editor.
Try typing "t" in gnome-do.
Something similar applies to gconf editor - listed as configuration editor (type "c").

---

### Post by cknight on 2009-06-19
> **TeoBigusGeekus said:**
> Because gedit is listed as text editor.
Try typing "t" in gnome-do.
Something similar applies to gconf editor - listed as configuration editor (type "c").

OK, thanks for that.  I can now get gedit launching quickly,though I'm still confused why it won't index the actual program name rather than just its function.  After all, I launch "Opera" not "Browser" (which only matches "Firefox Web Browser" since its part of the name).

And I'm afraid that there is no "configuration editor" in my gnome-do setup, nor anything relevant under "editor" either.

---

### Post by cknight on 2009-06-21
> **cknight said:**
> And I'm afraid that there is no "configuration editor" in my gnome-do setup, nor anything relevant under "editor" either.

To get gconf-editor (aka "Configuration Editor") to appear in gnome-do it must also appear in your main menu (e.g. Applications).  Once I added it to the Applications menu and restarted gnome-do, "configuration editor" successfully auto-completed in gnome-do.

---

