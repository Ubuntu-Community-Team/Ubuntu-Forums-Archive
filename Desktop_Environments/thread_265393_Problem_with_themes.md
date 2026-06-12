---
title: "Problem with themes"
date: 2006-09-25
forum: Desktop Environments
---

### Post by The Tronyx on 2006-09-25
Ubuntu tells me that in order to install a theme, it needs to be in tar.gz format however, when I try to install a theme that is in tar.gz format, it tells me invalid file format.  Any ideas?

---

### Post by lonce on 2006-09-25
How are you trying to install it?  Make sure that its not a compiz theme also if you are using metacity.

---

### Post by The Tronyx on 2006-09-25
I've tried dragging it into the theme window, installing it from the theme window and that's about it so far.  This is my first 24 hours with linux...well, 6 to be exact so most of the things I have googled are a bit over my head.  Any help is appreciated. Thanks.

---

### Post by Mr Frosti on 2006-09-25
The easiest way that I have found to install at theme is browse for a theme at [http://art.gnome.org/themes]("http://art.gnome.org/themes")

Once you have located a theme (or section of a theme) look for the hyperlink that says "Download", and had the ".tar.gz" extension on the link. Click and drag this download into the Gnome theme manager window. It is automatically download, extract, and install the theme for you.

Be cautious that there are some items for dowload that are not a complete theme package. Some might just be icons, or a Window border. If this is the cause, you can click on "Theme details" after the installation and select the appropriate pieces.

---

### Post by sabelsen on 2006-09-25
Have you tried any other themes in the tar.gz format? Do they work? It's not necessarily Gnome's fault, it might just as well be the creator of the theme. Anyways, the second option would be to extract the contents of the file into ~/.themes. You should then see your theme as a folder, and if you enter it you should see one or more folders. For example, gtk, gtk-2.0 (versions) or metacity or metacity-1 if it's a metacity theme. If you re-enter the themer (preferences -> themes -> theme control) you should see your theme listed under controls or window border.

~/.themes/VistaBut$ ls
gtk  gtk-2.0  index.theme  index.theme~  metacity-1  xfwm4

You can also just double-click your theme.tar.gz file and see if the structure fits the outline above.

---

