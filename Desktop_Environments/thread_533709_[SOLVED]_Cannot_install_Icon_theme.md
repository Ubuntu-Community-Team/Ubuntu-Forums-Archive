---
title: "[SOLVED] Cannot install Icon theme"
date: 2007-08-24
forum: Desktop Environments
---

### Post by tekkenlord on 2007-08-24
Hello,

I have a simple question. I recently downloaded a nice icon theme from here:

[http://www.gnome-look.org/content/show.php/Oxygen+Refit+%5BIcons%5D?content=64589](http://www.gnome-look.org/content/show.php/Oxygen+Refit+%5BIcons%5D?content=64589)

To install it I opened the control center, chose Theme and then Install. I gave the tarball and everything went smoothly. However, I decided later to remove this theme and I could not find such an option. So I went to ~/.themes and remove the folder from there. 

The problem is that I am trying to install it again and it fails! I am thinking that some files or folders are still left around the system preventing it to reinstall. Any help is appreciated. 

PS: How can I completely remove a theme?

---

### Post by testube_babies on 2007-08-24
Icons are stored in ~/.icons instead of ~/.themes.

(System-wide icons are in /usr/share/icons and not /usr/share/themes).

You can delete the files from these locations to completely remove them.

---

### Post by tekkenlord on 2007-08-24
That was fast! Thanks a lot, it works!

---

