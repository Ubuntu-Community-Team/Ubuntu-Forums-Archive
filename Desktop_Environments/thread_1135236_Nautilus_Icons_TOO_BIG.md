---
title: "Nautilus Icons TOO BIG"
date: 2009-04-24
forum: Desktop Environments
---

### Post by bLiZz247 on 2009-04-24
My questions is how can I change the icon size in the application menu and buttons in nautilus? Instead of 24x24 or whatever, I want them to be the same size as the panel icons... 16X16.

I found a thread in the ubuntu forums that had this answer, but I can't find it anymore. I know you can do it, because I had it set up this way on my old laptop with ubuntu 8.10. You had to edit a file and add or change one line.

Thanks for any help.

---

### Post by bLiZz247 on 2009-04-26
bump

---

### Post by bLiZz247 on 2009-04-26
Ok, I found exactly what I needed. This is what I did:

Under /usr/share/themes I edited the ***gtkrc*** file in the corresponding theme. I added the following line:

gtk-icon-sizes = "panel-menu=16,16:gtk-button=16,16"

It looks great! ...and everything is in proportion. 

panel-menu refers to menus in panels (Applications)
gtk-button refers to buttons in GTK-applications (OK/Cancel)

Got the previous commands from [here.]("http://www.mail-archive.com/debian-gtk-gnome@lists.debian.org/msg13233.html")
Hope this helps someone else out as well!

---

