---
title: "gnome-theme-manager problem"
date: 2005-12-01
forum: Desktop Environments
---

### Post by ardchoille on 2005-12-01
I noticed that when I install a GTK2/Metacity theme, the gnome-theme-manager installer only installs one theme from the tarball when installing a multi-theme tarball. There are many GTK2/Metacity theme tarballs that contain multiple themes and these cannot be completely installed using the gnome-theme-manager installer (the installer only installs one theme from the set). However, when I unpack a multi-theme tarball into ~/.themes all the themes appear in gnome-theme-manager and work fine. Is there a bug in the gnome-theme-manager installer that disallows installation of more than one theme from a tarball at a time?

The following URL links to a theme that contains 10 themes in the tarball: 
[http://www.gnome-look.org/content/show.php?content=26530](http://www.gnome-look.org/content/show.php?content=26530)

I have noticed this problem with all multiple theme tarballs. Is this problem only in the gnome desktop environment that ships with Ubuntu?

---

### Post by mrmcctt on 2005-12-01
For those you will have to extract them and then move them to ~/.themes.

Then they will all be availabe for your theme manager.

---

### Post by ardchoille on 2005-12-02
[QUOTE=mrmcctt]For those you will have to extract them and then move them to ~/.themes.

Then they will all be availabe for your theme manager.[/QUOTE]
Yes, thank you. I unpacked them into ~/.themes and they work fine. I won't trust the gnome-theme-manager installer in the future.

---

### Post by 23meg on 2005-12-02
The theme manager is only meant to install archives that contain a single theme. If you have an archive file containing multiple other archives, extract them to a temporary folder and drag and drop each archive individually.

---

### Post by mrmcctt on 2005-12-02
23meg is right.  The theme installer is really nice to have and easy to use.  It has limitations but now you know about those.

---

