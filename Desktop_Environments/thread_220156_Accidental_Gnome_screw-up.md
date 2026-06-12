---
title: "Accidental Gnome screw-up"
date: 2006-07-21
forum: Desktop Environments
---

### Post by shadowcreeper on 2006-07-21
So I installed 6.06 with Gnome as part of my pet project at home.  Unfortunately, I don't have Internet at home, thus I use the packages on the CD.  Otherwise, I download the files, put them on flash disk and install them with dpkg.

So, yesterday evening, in my tired state of mind, I open Synaptic Package manager to install a required library, but by accident, I uninstall some of the gnome packages.  Idiot.  ](*,) 

Of course, I don't really need Gnome, but it does help to do some things quicker.  Now I need to install it again from the 6.06 CD.  

I've tried apt-get install gnome, but it can't find the package.  

So, how do I reinstall gnome from the 6.06 CD, if I don't have internet access?

---

### Post by simonn on 2006-07-21
You should be able to determine which packages were uninstalled by looking in /var/log/dpkg.log.

---

