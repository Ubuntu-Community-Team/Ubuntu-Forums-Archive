---
title: "How do I get apps to be 'slimmer' - wasted space in file menus etc"
date: 2008-06-30
forum: Desktop Environments
---

### Post by rickcr on 2008-06-30
Currently I'm using xfce4, but have the same issue in gnome on this laptop that has a 1280x800 resolution. How do I get the apps to be less 'fat' and more slim. Basically look at how the xfce4 file manager looks in the screenshot, It has so much wasted space. It's really quite bad in my opinion. Granted on a large resolution desktop this isn't that big of a deal but when I reboot this laptop to windows I can see so much more in windows explorer since the letting is so much less and the folder icons are smaller. All apps I open have this problem. Whatever IDE I'm using (eclipse/netbeans) has so much wasted space in the file menu.  

It's not just changing the font size since even if I go any smaller
(I'm at sans 9 now) it just makes the font smaller but does nothing
with the icons or spacing.

Thanks so much for any help.

---

### Post by Harii on 2008-06-30
Try edit your .gtkrc-2.0.mine file to look something like:
> gtk-icon-sizes="gtk-menu=16,16:
                gtk-button=16,16:
                gtk-small-toolbar=16,16:
                gtk-large-toolbar=16,16:
                gtk-dnd=16,16:
                gtk-dialog=16,16"
gtk-toolbar-style = GTK_TOOLBAR_ICONS
I don't use thunar but pcmanfm and i think it has settings for that in pcmanfm.

---

### Post by Harii on 2008-07-02
You might want to try a thinner GTK2 theme as well?

---

