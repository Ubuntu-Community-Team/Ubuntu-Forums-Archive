---
title: "Window Grouper"
date: 2007-05-20
forum: Desktop Effects &amp; Customization
---

### Post by fuzz2010 on 2007-05-20
The window grouper in beryl of course didn't come with it when i installed beryl and I attempted to install beryl-plugins-unsupported but recieved the following in terminal and synaptic:

E: /var/cache/apt/archives/beryl-plugins-unsupported_0.2.0~0beryl1_i386.deb: trying to overwrite `/usr/lib/beryl/libtext.so', which is also in package beryl-plugins

Anyone else have this problem or who can help?

---

### Post by knn on 2007-05-20
> **fuzz2010 said:**
> The window grouper in beryl of course didn't come with it when i installed beryl and I attempted to install beryl-plugins-unsupported but recieved the following in terminal and synaptic:

E: /var/cache/apt/archives/beryl-plugins-unsupported_0.2.0~0beryl1_i386.deb: trying to overwrite `/usr/lib/beryl/libtext.so', which is also in package beryl-plugins

Anyone else have this problem or who can help?

Try Trevino's repository:
```
# Treviño’s Ubuntu feisty EyeCandy Repository (GPG key: 81836EBF - DD800CD9)
# Many eyecandy 3D apps like Beryl, compiz and kiba-dock snapshots
# built using latest available (working) sources from git/svn/cvs…
deb http://download.tuxfamily.org/3v1deb feisty eyecandy
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy
```

---

### Post by fuzz2010 on 2007-05-21
> **knn said:**
> Try Trevino's repository:
```
# Treviño’s Ubuntu feisty EyeCandy Repository (GPG key: 81836EBF - DD800CD9)
# Many eyecandy 3D apps like Beryl, compiz and kiba-dock snapshots
# built using latest available (working) sources from git/svn/cvs…
deb http://download.tuxfamily.org/3v1deb feisty eyecandy
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy
```

Thank you, these repositories let me install the plugins, although now when i try to use the grouper it has no effect, im hit super + s but the windows arent being selected.

---

### Post by knn on 2007-05-22
> **fuzz2010 said:**
> Thank you, these repositories let me install the plugins, although now when i try to use the grouper it has no effect, im hit super + s but the windows arent being selected.

In the Beryl settings manager, check to see if the grouper is activated and check the keyboard shortcut. If it's still not working, unload beryl, and delete the .beryl hidden directory in your home directory. Then load beryl, it should reset to default settings, which should work.
Also make sure all the beryl packages come from Trevino's repository, and no beryl packages from ubuntu are installed.

---

### Post by fuzz2010 on 2007-05-22
Thanks a lot, i just had to reload the window manager, i saw in another topic that it must be a glitch, thanks a lot for those repositories :D

---

