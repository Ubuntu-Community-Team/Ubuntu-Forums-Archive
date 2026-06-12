---
title: "Installing a printer?"
date: 2011-05-11
forum: Desktop Environments
---

### Post by ronni on 2011-05-11
Hi,

System:
Ubuntu 11.04
Gnome 3

Everything seems to work, except that I can't install a printer.

When going to 'System Settings' -> 'Printers' everything is shaded, and I can't do anything :confused:

Anyone knows if I'm missing some packages or how to add a printer?

---

### Post by walt.smith1960 on 2011-05-11
What make/model printer?  You might find this useful although the databases can be a little out-of-date.  [http://www.linuxfoundation.org/collaborate/workgroups/openprinting. ]("http://www.linuxfoundation.org/collaborate/workgroups/openprinting")
I just noticed you're using Gnome3.  Gnome3 on Ubuntu 11.04 is reputed to be not real stable at this point so I wonder if that's part of your problem.

---

### Post by ronni on 2011-05-11
Found a thread on the issue, in Arch Linux: [https://bbs.archlinux.org/viewtopic.php?id=116736](https://bbs.archlinux.org/viewtopic.php?id=116736)

Found that the package 'cups-pk-helper' should be installed, which then enables an unlock button in the 'System Settings' -> 'Printers'.

After unlocking printers can be installed.

---

### Post by -unseen- on 2011-05-11
Right, cups and cups-pk-helper are required to make it work. After that I still had issues. When I actually tried to add a new printer nothing happened. When running the gnome-control-center from the terminal there appeared a warning about packagekit.

(gnome-control-center:4772): printers-cc-panel-WARNING **: The name org.freedesktop.PackageKit was not provided by any .service files

So I still can't add a printer from the control center. Installing system-config-printer-gnome package gives back the old printer setup program, and there it works just fine ...

---

