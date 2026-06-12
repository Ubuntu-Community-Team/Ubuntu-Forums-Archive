---
title: "How do you install screenlets that are .tar.bz2 instead of .tar.gz?"
date: 2008-01-27
forum: Desktop Effects &amp; Customization
---

### Post by rainwalker on 2008-01-27
I've gotten the hang on installing .tar.gz screenlets (rename them to the name of the folder inside it) with the Screenlets Manager, but I can't figure out how to install ones that are .tar.bz2 packages. I tried renaming them to .tar.gz and that didn't work, and I haven't tried extracting them to my .screenlets directory because I've had issues with it (not created when I installed screenlets, messed up when I created it myself, random problems with it sometimes).

Help?

---

### Post by Ub1476 on 2008-01-27
Are you using the latest Screenlets-manager (0.012 or something I believe) which can be found on gnome-look? The version from the official website is outdated, in other words, the man who started Screenlets doesn't have time to work on it now, so another guy took over for the moment (don't we love open-source?)

EDIT: [Here it is]("http://gnome-look.org/content/show.php/Screenlets+0.0.12?content=73346")

---

### Post by rainwalker on 2008-01-27
> **Ub1476 said:**
> Are you using the latest Screenlets-manager (0.012 or something I believe) which can be found on gnome-look? The version from the official website is outdated, in other words, the man who started Screenlets doesn't have time to work on it now, so another guy took over for the moment (don't we love open-source?)

Oh...no I guess I'm not, I'll go look...

Is this it?
[http://www.gnome-look.org/content/show.php/Screenlets-manager+modified?content=70184](http://www.gnome-look.org/content/show.php/Screenlets-manager+modified?content=70184)

---

### Post by Ub1476 on 2008-01-27
> **rainwalker said:**
> Oh...no I guess I'm not, I'll go look...

Is this it?
[http://www.gnome-look.org/content/show.php/Screenlets-manager+modified?content=70184](http://www.gnome-look.org/content/show.php/Screenlets-manager+modified?content=70184)

Nope, I edited my above post.

---

### Post by rainwalker on 2008-01-27
It looks like I have to uninstall screenlets first; how do I do that? It's not a package

---

### Post by Ub1476 on 2008-01-27
If you compiled Screenlets, open the folder you compiled it in and type:

```
sudo make uninstall #or remove
```

If you have deleted the folder, there might be a uninstall script in the dir it was installed (not quite sure though). Check your trash first though.

EDIT: Or another idea, download the screenlets 0.0.10 source, "install" it again (configure/make/make install) and then remove it.

---

### Post by Muppeteer on 2008-01-28
Ok, first thing you have to do is extract the screenlet you download on the desktop or another directory. Then in the terminal, cd to the desktop and type```
screenlets-packager "folder name"
``` that should create a new .tar file that the installer will let you use :)

---

### Post by rainwalker on 2008-01-28
Thanks both of you for your help, but I got it
I did the "make uninstall" in the screenlets folder (luckily still in my trash) and then installed the .deb for the new one, and now everything works :)
Well, except the Calendar and Gmail screenlets won't start on login, but oh well

---

