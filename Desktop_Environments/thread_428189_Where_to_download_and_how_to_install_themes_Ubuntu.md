---
title: "Where to download and how to install themes Ubuntu Gnome"
date: 2007-04-30
forum: Desktop Environments
---

### Post by stchman on 2007-04-30
Where to get them and how to install them.  I go to gnome-look.org and download them.  After that Ubuntu says the themes are no the proper format.

Thanks

---

### Post by aysiu on 2007-04-30
A few tips:

1. Don't unzip the .tar.gz files *unless* the theme is called a "pack" on the download page. GTK, Metacity, and icon themes go to System > Preferences > Themes. Just drag and drop the .tar.gz into the Theme Manager window.

2. GDM themes go to System > Administration > Login Window

If you're still having problems, post a link to the particular theme you're trying to install.

---

### Post by stchman on 2007-04-30
> **aysiu said:**
> A few tips:

1. Don't unzip the .tar.gz files *unless* the theme is called a "pack" on the download page. GTK, Metacity, and icon themes go to System > Preferences > Themes. Just drag and drop the .tar.gz into the Theme Manager window.

2. GDM themes go to System > Administration > Login Window

If you're still having problems, post a link to the particular theme you're trying to install.

Excellent, that worked.  It was pretty non-intuitive to drag the .tar.gz or the .tar.bz2, or the .zip file into the themes window.  Now that I know I won't forget.  I wonder where did you find that little piece of information?  I intuitively unzipped the archive and then tried to install, how wrong I was.

I made Gnome look like OS X.  The icons are really detailed.

Thanks for the info.

---

### Post by aysiu on 2007-04-30
I learned about the drag and drop by reading about it on the forums.

Unfortunately, the README files in those .tar.gzs or the "How to install..." links on [http://www.gnome-look.org](http://www.gnome-look.org) aren't much help either. They either tell you to ./configure make make install or extract the folder to /usr/share/themes

The theme manager window actually does the extracting for you. If it's an icon theme, the theme manager will extract the theme to ~/.icons (or /home/username/.icons). If it's a GTK or Metacity theme, the manager will extract it to ~/.themes. If you're install a GDM (login screen) theme, the theme .tar.gz will be extracted to /usr/share/gdm/themes

By the way, the themes installed through the theme manager window are available only to the currently logged in user. If you want them available to all users, you have to manually extract them to /usr/share/themes or /usr/share/icons

To do that, read this:
[http://www.psychocats.net/ubuntu/permissions#gui](http://www.psychocats.net/ubuntu/permissions#gui)

---

### Post by stchman on 2007-04-30
> **aysiu said:**
> I learned about the drag and drop by reading about it on the forums.

Unfortunately, the README files in those .tar.gzs or the "How to install..." links on [http://www.gnome-look.org](http://www.gnome-look.org) aren't much help either. They either tell you to ./configure make make install or extract the folder to /usr/share/themes

The theme manager window actually does the extracting for you. If it's an icon theme, the theme manager will extract the theme to ~/.icons (or /home/username/.icons). If it's a GTK or Metacity theme, the manager will extract it to ~/.themes. If you're install a GDM (login screen) theme, the theme .tar.gz will be extracted to /usr/share/gdm/themes

By the way, the themes installed through the theme manager window are available only to the currently logged in user. If you want them available to all users, you have to manually extract them to /usr/share/themes or /usr/share/icons

To do that, read this:
[http://www.psychocats.net/ubuntu/permissions#gui](http://www.psychocats.net/ubuntu/permissions#gui)

I see, kind of like fonts being put into the ~/.fonts folder.  I unpack all of my font in the /usr/share/fonts/truetype/<font_folder>

I guess I should install the themes in the proper folders.

---

### Post by aysiu on 2007-04-30
> **stchman said:**
> 
I guess I should install the themes in the proper folders. If you have multiple users on your computer, then, yes. Otherwise, not really.

---

### Post by jimbean on 2007-04-30
have you tried beryl

---

### Post by stchman on 2007-05-01
> **jimbean said:**
> have you tried beryl

I did try Beryl and while it looked very nice it made my system crawl.  Google Earth was almost unusable.  Since Bery is still beta I will wait until it is mature before using it.

---

