---
title: "KDE dialog box rather than GNOME"
date: 2007-10-02
forum: Desktop Effects &amp; Customization
---

### Post by inflamous on 2007-10-02
Not that this is a real problem, but reading a post from:
[Kubuntu on a Dell 1501]("http://kubuntu1501.blogspot.com/")

I was just wondering on how this could be done.

I'm running KDE on my linux box and I actually wouldn't mind seeing KDE dialog boxes rather than GNOME ones (I find those quite annoying and dull in comparison).

---

### Post by inflamous on 2007-10-15
well I found a solution, it works for most programs:

Original:
[http://www.kde-apps.org/content/show.php?content=36077&forumpage=13&PHPSESSID=d78b45d40b5bfdc6032a763d6078a535](http://www.kde-apps.org/content/show.php?content=36077&forumpage=13&PHPSESSID=d78b45d40b5bfdc6032a763d6078a535)

Deb Package:
[http://www.kde-apps.org/content/show.php/KGtk+for+Kubuntu+Edgy?content=58584](http://www.kde-apps.org/content/show.php/KGtk+for+Kubuntu+Edgy?content=58584)

The deb package was made for edgy, but it also works perfectly fine in feisty (although in firefox, it sometimes crashes when I overwrite a file).

But to get the kde dialog when installed with the deb package, you would need to do:
kgtk-wrapper <***program***>

---

