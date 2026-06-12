---
title: "[SOLVED] Help my Icons are gone!!"
date: 2008-10-14
forum: Desktop Environments
---

### Post by 09buntu on 2008-10-14
Hi

I'm using the "Buuf Deuce" icon theme. Thing is actions/bookmark-new.png points to gtk-bookmark.png ie everything seems ok.

BUT in the Gnome Place menu bookmark icons are displayed with the imho not so good looking Gnome default folder icon!!

Any ideas how to fix this?
Thanks

---

### Post by 09buntu on 2008-10-15
Ok it's a known bug.

[**_Inode-directory.svg/.png files break other icon themes_**]("https://bugs.launchpad.net/ubuntu/+source/gnome-icon-theme/+bug/278033")

> The latest release of GNOME 2.24 now includes inode-directory.svg / .png links that break other icon themes that inherit from gnome-icon-theme.

When using an icon theme which inherits from gnome, but does not include an inode-directory icon (which includes the majority of icon themes) the default gnome folder icon will appear instead of the current icon set's folder icon. This happens most notably in the places menu of gnome-panel, and was an issue for the Human icon theme in the Intrepid alphas.

While the Human icon theme solved this issue by adding an inode-directory.svg file of their own, the mere use of that file itself causes many regressions. For example, when drag n' dropping into folders, you will not see the folder change to an open/receiving folder. Also, in nautilus' non-browser mode (fedora style), visiting folder icons will not work either.

---

### Post by jesterthejedi on 2008-10-16
According to the Gnome art site:

Filesystem

The FileSystem context is for icons intended to be used by a FileManager, such as Nautilus, to represent the core parts of a directory tree, essentially such icons as would be used to represent Folders, Network Servers, Network workstations, Fifo's, Character Devices, Executables and so forth.

Bookmarks
	
gnome-fs-bookmark
	
list common uses for bookmarks, and have an example of both icons

Thus when I installed Intrepid I noticed my Mashup icon theme got dropped from drawing these icons. Based on this naming system, I will be attempting to add icons into my icon set.
[http://www.gnome-look.org/content/show.php/Mashup+of+Crashbit?content=86452](http://www.gnome-look.org/content/show.php/Mashup+of+Crashbit?content=86452)

---

