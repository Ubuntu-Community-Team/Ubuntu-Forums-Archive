---
title: "icons"
date: 2008-03-12
forum: Desktop Effects &amp; Customization
---

### Post by chris.9540 on 2008-03-12
im trying to add these icons 
[http://www.gnome-look.org/content/show.php/black-white+2+Gloss?content=72621](http://www.gnome-look.org/content/show.php/black-white+2+Gloss?content=72621)
ive been told to install them (dosent work not a theme package)
and i cant change permissions to copy the file into usr/shear/icons

---

### Post by rune0077 on 2008-03-12
Those icons are a theme, just don't unpack them before trying to install them. Otherwise, you can drop the icons in the /home/yourhomedirectory/.icons folder (notice the . in front of icons, that means it's a hidden file in your home directory), that'll have the same effect except you'll be the only user having access to them.

---

### Post by BluntBox on 2008-03-13
Had a look at the first archive listed on that gnome-look page. There is a second archive inside which is the one you actually need to use.

To install it simply, you can open "black_white_2_Gloss_by_DBGtheKafu.tar", and extract the "black-white_2-Gloss.tar.gz" file anyway you want.

Then open System -> Appearance, and just drag and drop "black-white_2-Gloss.tar.gz" onto the window. This will install them for the current user.

To install them for all users they need to be placed in /usr/share/icons, sudo copy them via the terminal if you are comfortable with that, or open a nautilus window with sudo and drag and drop.

---

### Post by Therion on 2008-03-13
Dude, I gave you step-by-step directions in your [other thread](http://ubuntuforums.org/showthread.php?t=722606) about this very same install.

---

