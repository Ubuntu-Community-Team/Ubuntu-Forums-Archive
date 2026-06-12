---
title: "Natural Selection!"
date: 2006-08-11
forum: Desktop Environments
---

### Post by Mickeysofine1972 on 2006-08-11
Hi

Does anyone have a clue where in Gnome I can change the colour of the selection rectange that appears when you click and drag on the desktop?

I recently changed to Ubuntu-desktop having used Kubuntu-desktop for a while and the only thing thats left of kubuntu is the blue rectangle I get when I drag-select on my desktop.

Any suggestions?

Mike

---

### Post by ardchoille on 2006-08-11
> **Mickeysofine1972 said:**
> Hi

Does anyone have a clue where in Gnome I can change the colour of the selection rectange that appears when you click and drag on the desktop?

I recently changed to Ubuntu-desktop having used Kubuntu-desktop for a while and the only thing thats left of kubuntu is the blue rectangle I get when I drag-select on my desktop.

Any suggestions?

Mike

That is controlled by the theme you are using. You can always edit it in /usr/share/themes/theme-name/gtk-2.0/gtkrc

You can open that file for editing with:

```

gksudo gedit /usr/share/themes/theme-name/gtk-2.0/gtkrc

```

where "theme-name" is the name of the theme you want to edit, but I would advise to make a backup of it first, just in case.

---

