---
title: "Cairo Dock Customization"
date: 2009-02-10
forum: General Help
---

### Post by dox_drum on 2009-02-10
Hi there,

I've just installed the cairo-dock on my sesion, but I'd like to learn a couple of things.

[LIST]
[*]How do I install some applets? I mean, in synaptic there are lots of things as result of "cairo-dock app", but it seems to me not all of them are for the dock itself.
[*]How do I add icons to a sub-dock? I've try by dragging them but they vanish, from both, the sub-dock and the dock.
[*]Is it possible to include the cairo menu to the dock? Because in a previous post someone wrote that adding an icon with command line "<Alt> F1" and removing the gnome menu, it'd work (some other guys say it does)... but I got no luck.
[/LIST]

Thank you very much

[CENTER]Enjoy![/CENTER]

---

### Post by Ng Oon-Ee on 2009-02-11
Sorry I can't help on the repo-cairo-dock, as I've been using the SVN version for ages. It's quite easy, their website has instructions, basically download a script, make it executable, and run it in a folder. You can run it again to update to latest SVN. Plug-ins come included, this way.

---

### Post by fabounet on 2009-02-11
see the wiki for the installation with the official repository.
The Ubuntu repository is just crappy (old version, no plug-ins)

---

### Post by dox_drum on 2009-02-11
Thank you for the advise on the repository...

But I still do not get how to create a sub-dock. 

[center]Enjoy[/center]

---

### Post by dox_drum on 2009-02-11
> **dox_drum said:**
> Thank you for the advise on the repository...

But I still do not get how to create a sub-dock. 


I finally got it!

[LIST=1]
[*]Add the sub-dock icon
[*]When adding the launcher you want in the sub-dock, intead of place it in _Main_dock_, place it in your sub-dock.
[/LIST]

[CENTER]Enjoy![/CENTER]

---

### Post by dox_drum on 2009-02-11
Has someone any idea about adding a Main Menu icon?

---

### Post by fabounet on 2009-02-12
the GMenu applet
(you might need to install libgnome-menu)

---

### Post by dox_drum on 2009-02-12
Thank you very much fabounet!!!

It works perfectly.

---

