---
title: "How can I get rid of all the panels and taskbars"
date: 2010-02-09
forum: Desktop Environments
---

### Post by Garnett on 2010-02-09
Looking for ideas of how to clear screen real estate!

I'm all ready using Gnome Do with the Docky appearance (my favourite dock option).

Are there other options to cover the Applications, places, system  and other information and facilities in the "taskbar" panel?

---

### Post by tilixibr on 2010-02-09
you mean the "original" taskbar?

i dont think you can do that, but you can hide it though, just right-click the taskbar and select properties, on the "General" tab, select "autohide", and try putting the taskbar where you wont acidentally hover your mouse over. 

hope i helped:)

---

### Post by pritamps on 2010-02-09
Run gconf-editor

Navigate to apps -> desktop -> gnome -> session -> required components.

There, edit the panel field and make it empty.

Then logout and log back in and your last panel (the others, you can delete by just right clicking and saying delete panel) should be gone.

I'm assuming you're on GNOME...

---

### Post by Garnett on 2010-02-10
> **tilixibr said:**
> you mean the "original" taskbar?

i dont think you can do that, but you can hide it though, just right-click the taskbar and select properties, on the "General" tab, select "autohide", and try putting the taskbar where you wont acidentally hover your mouse over. 

hope i helped:)
Thanks a lot. One of the reasons I want to do this is sheer aesthetics! When I use the compiz desktop switcher rotating cube/sphere, with an autohide taskbar, you still see a strip of pixels where the taskbar would normally be. For that reason I'm not happy with the autohide solution.

> **pritamps said:**
> Run gconf-editor

Navigate to apps -> desktop -> gnome -> session -> required components.

There, edit the panel field and make it empty.

Then logout and log back in and your last panel (the others, you can delete by just right clicking and saying delete panel) should be gone.

I'm assuming you're on GNOME...Thanks. That's what I want to do. Now I just need some other way to replicate the functionality I lose...

---

### Post by Garnett on 2010-02-10
Are there other options to cover the Applications, places, system  and other information and facilities in the standard "taskbar" panel?

I was wondering if I could put any of these into the Gnome-Do Docky or maybe add another dock (AWN or Cairo maybe) at the top of the screen.

Or maybe some screenlets.

The info at the right - time, update status, wifi connectivity I think could be screenlets, but I' not sure about Applications/Places/System.

Any suggestions appreciated.

---

### Post by Garnett on 2010-02-10
Going to try replacing the taskbar with other options to see if their "autohide" feature does a better job than the default.

perlpanel or fbpanel or tint task manager or GDesklets seem to be some of the more popular options. Tint sounds promising.

---

### Post by Jefferythewind on 2010-02-10
You can take everything off if you want.  Just remove everything from the panel at the top of the screen, and then make it transparent.  Or you can also auto-hide it.

  I still lie having the panel at the top of the screen, but i had Cairo-Dock on 9.04, and it was very nice.  since upgrading i haven't re-installed Cairo-Dock, but I think i am going to do it now...

Good luck

---

