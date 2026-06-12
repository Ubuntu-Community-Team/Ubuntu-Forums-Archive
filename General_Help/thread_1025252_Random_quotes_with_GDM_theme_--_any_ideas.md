---
title: "Random quotes with GDM theme -- any ideas?"
date: 2008-12-29
forum: General Help
---

### Post by oleander on 2008-12-29
Hello all! :)

I was thinking that it might be a great feature to have a random quote shown on my GDM login screen when logging in -- taken from predefined quotes in a file. I have never seen or heard of this feature before, though. Does anyone know if someone has already implemented this? I don't have experience making my own GDM themes -- only altering existing themes, so if anyone has any ideas of how to implement this, it would be much appreciated!

Cheers,
Oleander

Oh, and a Happy New Year to all!

---

### Post by pytheas22 on 2008-12-30
[This page]("http://live.gnome.org/GnomeArt/Tutorials/GdmThemes") explains how to create a custom gdm-theme file.  It's just an empty XML file, which means that you can't (as far as I know, but I'm not programmer) insert code into the configuration file itself to tell it to pick quotes randomly from an array and display them.  But I imagine that you could write some kind of script pretty easily that would just edit the XML file to insert different quotes; you could have a cronjob do this every ten minutes or something, for example, so that the quote displayed in the login screen would change every ten minutes.

I have to go to bed now but this is an interesting idea and I'll plan on thinking more about it tomorrow.  In the meantime, hopefully someone more knowledgeable can shed more light.

---

