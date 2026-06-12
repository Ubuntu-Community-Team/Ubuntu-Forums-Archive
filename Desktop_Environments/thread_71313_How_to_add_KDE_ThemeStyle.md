---
title: "How to add KDE Theme/Style?"
date: 2005-10-03
forum: Desktop Environments
---

### Post by s0c0 on 2005-10-03
So I want to add a KDE them from kde-look.org, but I don't know how.  Can someone tell me how to do this?  BTW, I am using Debian 3.1 and not Kubuntu, but Ubuntu has such wonderfull support forums.  So I thought I would ask here after no luck on google.  Thanks!

---

### Post by audax321 on 2005-10-03
Can you post a link to the theme. Depending on which one it is you either have to compile it:

./configure
make
make install

or (if it´s a deb file):

sudo dpkg -i <name_of_file>.deb

---

### Post by s0c0 on 2005-10-03
[http://kde-look.org/content/show.php?content=26892](http://kde-look.org/content/show.php?content=26892)

---

### Post by aysiu on 2005-10-03
That's a theme manager theme. I don't know if you have the theme manager installed. It comes with the default install of Mepis, but I don't know about Debian (Kubuntu doesn't have it).

---

### Post by s0c0 on 2005-10-03
Okay I figured it out.  I download what looked like some theme managers via synaptic.  I then went into the KDE Control Center > Appearance & Themes > Theme Manager. Once I selected the theme, kde was able to auto-install the *.kth file.  Thanks!  Me like KDE.  Much better than Gnome.

---

### Post by aysiu on 2005-10-03
[QUOTE=s0c0]Okay I figured it out.  I download what looked like some theme managers via synaptic.  I then went into the KDE Control Center > Appearance & Themes > Theme Manager. Once I selected the theme, kde was able to auto-install the *.kth file.  Thanks!  Me like KDE.  Much better than Gnome.[/QUOTE] Well, I happen to like KDE a lot, too, but I think Gnome's theme management is a lot better. Oh, well. It worked out for you. That's cool.

---

