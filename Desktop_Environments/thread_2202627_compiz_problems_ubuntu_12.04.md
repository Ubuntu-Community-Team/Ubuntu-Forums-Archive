---
title: "compiz problems ubuntu 12.04"
date: 2014-01-30
forum: Desktop Environments
---

### Post by brick2 on 2014-01-30
Ubuntu 12.04
Dell inspiron 5537
VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller

This is really wierd. First I installed compiz and plugins, it worked well for a while than for reasons unknown to me it stoped so I uninstalled it. However when I installed it again it seam to have remembered all of my preferences and nothing worked at all, I mean I could jsut open a window of compiz manager and whether I toggeled options or not it had no effect. Bellow is the list of comands I used.

```
sudo apt-get purge compiz compiz-core compiz-dev compiz-fusion-plugins-main compiz-gnome compiz-plugins compiz-plugins-default compiz-plugins-main compiz-plugins-main-default compiz-plugins-main-dev compizconfig-backend-gconf libcompizconfig0 libcompizconfig0-dev libdecoration0 libdecoration0-dev compiz-fusion-bcop compiz-fusion-plugins-extra compiz-plugins-extra compizconfig-backend-kconfig compizconfig-settings-manager fusion-icon pdfcube python-compizconfig

```

```
sudo apt-get purge compiz*
sudo apt-get autoremove
```

I just wanted to make sure I deleted everything, but this did not solve things, next time I installed it all of the preferences were stil remembered and nothing worked. The instalation command was:
```
sudo apt-get install compiz compizconfig-settings-manager compiz-plugins-extra
```

Could anybody help me out, I am looking to enable 3D cube and wobbly windows. 

Thank you all for you time

---

### Post by deadflowr on 2014-01-30
What desktop environment were you running in the first place?
If you had to install compiz, then it wasn't Unity.
Or if you are running unity(the default desktop for Ubuntu 12.04) you might be running Ubuntu-2d.
Ubuntu-2d uses the metacity(?) window manager(If I recall), which doesn't have many effects.

---

### Post by brick2 on 2014-01-30
Gnome.

Any idea how to make compiz function?

---

### Post by Frogs Hair on 2014-01-30
The Gnome Shell uses the Muter WM and not Compiz. I can't tell you if Compiz works with the gnome-session-fallback though.

---

### Post by deadflowr on 2014-01-30
Don't know which gnome(classic or shell;shell is the new gnome that looks a little like unity)
But maybe open a terminal and run
```
compiz --replace
```
I think with shell you need to disable "file manager handles the desktop".
You can toggle that setting with the gnome-tweak-tool.

I don't run classic, so I don't know what settings should be set.

Added: compiz on Ubuntu is really built to work with unity, so problems with other desktop is probably par for the course.

---

### Post by brick2 on 2014-01-30
O well I shall try what you sugested but can you provide some reason why is it that even after I uninstall compiz when I reinstall it it remembers everythig, I have a bad fealing I am not uninstalling it in the proper manner, the commands I used for uninstalling are listed above.

---

### Post by deadflowr on 2014-01-30
It's most likely saving the settings because you still have configuration files in your home folder.
Probably somewhere in the .config(hidden) folder.

---

### Post by brick2 on 2014-01-30
Got the job done, reinstalled it, and ran 
compiz --replace

However I will continue searching for that file where my configuration is stored after I uninstall it.

Thank you for your time and help.

---

