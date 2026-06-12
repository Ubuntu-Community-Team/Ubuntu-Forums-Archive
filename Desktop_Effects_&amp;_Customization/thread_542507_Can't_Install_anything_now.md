---
title: "Can't Install anything now"
date: 2007-09-04
forum: Desktop Effects &amp; Customization
---

### Post by Mongo5000 on 2007-09-04
So i am trying to install compiz-fusion and following the tutorial found here [http://forum.compiz-fusion.org/showthread.php?t=3157](http://forum.compiz-fusion.org/showthread.php?t=3157) im not getting this in terminal

You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  desktop-effects: Depends: compiz but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```
apt-get -f install 
```
Gives
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  compiz-gnome
The following packages will be upgraded:
  compiz-gnome
1 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
1 not fully installed or removed.
Need to get 0B/161kB of archives.
After unpacking, 893kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 121921 files and directories currently installed.)
Preparing to replace compiz-gnome 1:0.3.6-1ubuntu13 (using .../compiz-gnome_1%3a0.5.5~git20070828+3v1ubuntu0_i386.deb) ...
Unpacking replacement compiz-gnome ...
dpkg: error processing /var/cache/apt/archives/compiz-gnome_1%3a0.5.5~git20070828+3v1ubuntu0_i386.deb (--unpack):
 trying to overwrite `/usr/lib/compiz/libgconf.so', which is also in package compiz-plugins
Errors were encountered while processing:
 /var/cache/apt/archives/compiz-gnome_1%3a0.5.5~git20070828+3v1ubuntu0_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I can't figure out how to correct this...HELP!:confused:

---

### Post by Mongo5000 on 2007-09-04
I trying what it suggests I loaded up Synaptic Package Manager and it says I have 2 broken packages.

compiz
compiz-gnome

When I go to remove them it wants to remove ubuntu-desktop which im pretty sure I don't want to remove.

Arggg.... should have stuck with beryl which was working fine

---

### Post by Inxsible on 2007-09-04
removing ubuntu-desktop is not an issue. ubuntu-desktop is a meta package which only points to which packages should be installed in a new ubuntu installation. removing it does not hamper anything, except when you try to upgrade your OS from feisty to gutsy lets say...

but you can always install ubuntu-desktop at that time and you would be good to go.

---

### Post by jocko on 2007-09-04
You can safely remove ubuntu-desktop, it's just a meta package that installs a bunch of other packages (including compiz).
Removing it will not remove anything else.
Once you have removed and reinstalled your broken packages, reinstall ubuntu-desktop to make sure you don't get problems later if you upgrade to a new release of ubuntu.

---

