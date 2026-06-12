---
title: "Setting the GNOME menu globally."
date: 2009-02-11
forum: General Help
---

### Post by Keatonguy on 2009-02-11
Is it possible to do this? I'm building an Ubuntu LTSP server for the first time, and while I think using gnome as opposed to IceWM (which we've been using for a long time now) will offer a more robust desktop, I need to be able to control what users have access to.

---

### Post by Tibuda on 2009-02-11
You can edit applications launchers in /usr/share/applications

---

### Post by Keatonguy on 2009-02-12
Thanks, this helps me out a lot. Now, however, this raises another question: The .desktop launcher files list numerous different catagories, which I assume are to indicate which submenus they'll be filed under, but for example with Abiword, it only shows up on one of the seven listed (Office). How does it decide which to file it under, and how can I make sure my custom launchers are being filed in the correct submenus?

---

### Post by Tibuda on 2009-02-12
I have done some googling, and found out that the .desktop format follows [these standards]("http://standards.freedesktop.org/desktop-entry-spec/latest/"), and the categories follow [these]("http://standards.freedesktop.org/menu-spec/latest/"). I'm not sure but, I think the categories listed in the desktop entry are categories in which the application can be displayed, but each desktop environment have its own categories.

---

### Post by Keatonguy on 2009-02-13
Thanks, I think this gives me enough to accomplish my goal. But just for the sake of completeness, if you or anyone else out there reading this can shed some light on Ubuntu's GNOME menu structure I would be grateful. There doesn't appear to be any info on it in the official documentation.

But again, thanks dredging those links up for me.

---

