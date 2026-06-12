---
title: "How can I modify the Ambiance theme colors?"
date: 2010-03-25
forum: Desktop Environments
---

### Post by webme on 2010-03-25
hello!!! i am trying disperately to modify the gtkrc file from ambiance theme, but without succes!
i want to change(pls see the atachement) nr 1(selection) to become red, and number 2,3,4,5 to remain the same!!! if i go to appearence and theme/color and select red to selected item all 1,2,3,4,5 become red, and i don't want that!!!
pls help!!!also i don't want gnome color chooser, i want a clean change in gtkrc!!!

---

### Post by jpeddicord on 2010-03-25
Perhaps Ambiance isn't the right theme for you: try out [Shiki-Wine]("apt://shiki-wine-theme"), [Wasp]("apt://community-themes"), or another Murrine variation. Shiki-Wine has a color scheme like you described by default, even.

---

### Post by psyke83 on 2010-03-25
> **webme said:**
> hello!!! i am trying disperately to modify the gtkrc file from ambiance theme, but without succes!
i want to change(pls see the atachement) nr 1(selection) to become red, and number 2,3,4,5 to remain the same!!! if i go to appearence and theme/color and select red to selected item all 1,2,3,4,5 become red, and i don't want that!!!
pls help!!!also i don't want gnome color chooser, i want a clean change in gtkrc!!!

In the section "menu-item", change bg[SELECTED] (and if you also want the menubar item changed, bg[PRELIGHT]) to the red colour you desire. The progressbar and scale uses "#FE765E".

This kind of question is more suitable to be asked elsewhere (such as the Art & Design forum). If you want more information on GTK theming, see: [http://live.gnome.org/GnomeArt/Tutorials/GtkThemes](http://live.gnome.org/GnomeArt/Tutorials/GtkThemes)

---

### Post by webme on 2010-03-25
in karmic, wasp was my favorite, i tried all, but ambiance is ''taller'' in metacity, and you can drag a window much better!!!

---

### Post by webme on 2010-03-25
> **psyke83 said:**
> In the section "menu-item", change bg[SELECTED] (and if you also want the menubar item changed, bg[PRELIGHT]) to the red colour you desire. The progressbar and scale uses "#FE765E".

This kind of question is more suitable to be asked elsewhere (such as the Art & Design forum). If you want more information on GTK theming, see: [http://live.gnome.org/GnomeArt/Tutorials/GtkThemes](http://live.gnome.org/GnomeArt/Tutorials/GtkThemes)
thankssss mannnn, you are a GENIUOSSS!!!! it works great!!!

---

### Post by webme on 2010-03-25
psyke83, please answer one more question   ---- what to modify in gtkrc to change the color when i select some files(please see the atachement)!!! thanks

---

