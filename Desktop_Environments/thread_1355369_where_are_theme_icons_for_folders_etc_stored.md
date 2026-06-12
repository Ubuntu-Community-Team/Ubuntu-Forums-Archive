---
title: "where are theme icons for folders etc stored?"
date: 2009-12-14
forum: Desktop Environments
---

### Post by cgb223 on 2009-12-14
hey where are the folders for themes, both third party and regular stored, how do i edit them, and how do i set an image for an entire type of file (i.e. a purple folder icon for EVERY folder rather than just one) this is for gnome 2.0 which i think supports gtk 2.0 if it helps (I'm no expert on how these things work)

tried going to properties and changing the icon but the icon only changes for one.

oh also (not to start a huge debate or anything but...) what is the most graphically beautiful theme for gnome? all hardware aside.

Please answer for 9.10

thank you! 

Charlie

---

### Post by RyanVanDiemen on 2009-12-15
It`s /usr/share/icons for all users or userhomefolder/.icons for just one user. There are plenty of icon or desktop themes to choose from at [www.gnome-look.org](www.gnome-look.org) . The most beautiful? That`s the personal preference but on the above web page you will find hundreds to choose from.

---

### Post by VCoolio on 2009-12-15
Gtk-themes and icon themes are in /usr/share/themes and in /usr/share/icons (the default themes and the ones you installed from the repos) or in ~/.themes and ~/.icons (if you drag-and-dropped in the appearance manager). 
Gtk-themes can be changed by modifying the images if there are any or by editing the gtkrc files. Sometimes you can change colors with the "colors" tab in the appearance window. Also gnome-color-chooser can be helpful.
Icon themes can be changed by replacing the images with the ones you want (with the same size and either a .png or .svg). The folder icon probably is in a "places" subfolder in your icon theme.
For color variation I recommend gnome-colors; you can install it from the repos (apt-get install gnome-colors). It has gnome-brave-icon-theme (blue), gnome-wise-icon-theme (green), gnome-wine-icon-theme (red), gnome-noble-icon-theme (purple), 	gnome-illustrious-icon-theme (pink), gnome-human-icon-theme (orange), 	gnome-dust-icon-theme (chocolate).
What the most beautiful theme is, is up to you. Visit gnome-looks.org and find out. There are lots of icon themes too.

---

