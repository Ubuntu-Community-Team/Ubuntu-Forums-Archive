---
title: "Ubuntu 20.04 Package Repository and Snapd Software version mismatches!"
date: 2020-07-09
forum: Desktop Environments
---

### Post by heinzhartfiel on 2020-07-09
For example:

If I install rsync via snapd, v3.1.1 gets installed
e.g. sudo snap install rsync

When I install it via apt
e.g. sudo apt install rsync 
rsync  version 3.1.3-8 gets installed

Same situation with blender, except that the latest version is available via snapd

When I install blender via snapd, v2.38.1 gets installed
e.g. sudo snap install blender --classic
When I install blender via the Ubuntu 20.04 official package repo
e.g. sudo apt install blender 
blender v2.82 (sub 7) gets installed (via sudo apt upgrade...no updates available )


Is somebody able to explain what's wrong?

Or do I miss something?

Do I have to check each time which repo is more recent to install the latest stable state of a package?

Some more mismatch examples and these are not the only ones:

sudo snap find gimp
gimp       2.10.20 

sudo apt show gimp
Package: gimp
Version: 2.10.18-1
Priority: optional
Section: universe/graphics
Origin: Ubuntu


sudo snap find audacity
audacity         2.4.1

sudo apt show audacity
Package: audacity
Version: 2.3.3-1build1 
Priority: optional
Section: universe/sound

...

Is this working as designed?


I'm just wondering if I'm the only one, or if there is something wrong with my Ubuntu installation.

Many thanks for a short reply and stay healthy!

---

### Post by CatKiller on 2020-07-09
There's nothing wrong; they are parallel distribution methods.

The versions in the repositories are fixed at (a little while before) the date that the version of Ubuntu is released, although they get security and bug fixes. Those packages are maintained by Ubuntu.

In addition to that, some software is distributed as snaps; in general there's no reason for or against there being overlap with the software in the repositories. Some software (proprietary, for example) will only be available as snaps, and some will only be available through the repositories, and some will be available as either, from different people. The snaps are maintained (or not) by whoever created the snaps: it might be the original developer, or it might be someone's one-off experiment, or it might be well-maintained by a third party. There are examples of all of those.

In general, higher version numbers are in no way superior. The packages get patches backported to them, they just don't get new features. If you need a particular version of a particular application for a particular feature then you'll need to find that version, sure, by snap, PPA, flatpak, upgrading Ubuntu, compiling from source, or whatever, but you shouldn't try to search out the highest version number just for the sake of it.

---

### Post by heinzhartfiel on 2020-07-10
Many thanks for your reply!

In the past years I used the Ubuntu maintained packages most of the time and it served me well. Since Ubuntu integrated snap and even flatpacks I found myself struggling.
I totally agree that the latest version is not always the best way to go. What confused me is the fact that sometimes a package is more recent in the Ubuntu repo, sometimes in the snapstore and vice versa. Libreoffice for example, as of today . Both maintained by Canonical. Maybe you are right and I shouldn't worry too much. It's not so difficult to check the available versions in either repo before the installation. But I don't know if it's a good idea to install someone's one-off experiment. :)

---

