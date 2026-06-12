---
title: "Installing GNOME 3.26 Core Apps"
date: 2018-01-05
forum: Desktop Environments
---

### Post by jtfolden on 2018-01-05
Hey all,

I just installed Ubuntu 17.10 a few days ago and switched to the vanilla GNOME desktop (installed gnome-session and vanilla-gnome-desktop). Is there a way to install all of the recommended "Gnome 3.26 Core Applications" on Ubuntu 17.10 in one go as well or do I need to just install them manually one by one?

Thanks!
John

---

### Post by Xian on 2018-01-05
Let's see what packages this will bring in:

$sudo apt-get install gnome-core

---

### Post by vasa1 on 2018-01-05
I don't know much about the whole GNOME thing, but ```
dpkg -l libgtk-3-0
```gives me:
for 16.04
```
libgtk-3-0:amd64                3.18.9
```

for 17.10
```
libgtk-3-0:amd64                3.22.25
```

and for 18.04 (as of yesterday)
```
libgtk-3-0:amd64                3.22.26
```
So I'm guessing getting one or more 3.26 packages onto 17.10 may not be a trivial venture :???:

---

### Post by jtfolden on 2018-01-09
> **Xian said:**
> Let's see what packages this will bring in:

$sudo apt-get install gnome-core

That does bring in a few more it seems... I've also been reading elsewhere and it doesn't look like there is a single meta-package to do what I hope, either.

---

### Post by jbicha on 2018-01-10
What apps do you consider to be GNOME Core that aren't installed?

gnome-core is the Debian metapackage. vanilla-gnome-desktop is derived from the old Ubuntu GNOME metapackage.

---

### Post by jtfolden on 2018-01-10
> **jbicha said:**
> What apps do you consider to be GNOME Core that aren't installed?

gnome-core is the Debian metapackage. vanilla-gnome-desktop is derived from the old Ubuntu GNOME metapackage.

Going off this list ( [https://blogs.gnome.org/mcatanzaro/2017/08/13/gnome-3-26-core-applications/](https://blogs.gnome.org/mcatanzaro/2017/08/13/gnome-3-26-core-applications/) ) there are several that aren't installed.

I've manually installed a few but I believe Web is the biggest, also Boxes, Clocks, and Weather.

---

### Post by jbicha on 2018-01-10
vanilla-gnome-desktop installs Weather. It does not install Clocks because Clocks has a usability problem (alarms only work if the app is running. Also, there's a bug where you can't hear the alarm on Wayland if the Clocks app is in a different workspace!)

Boxes and Web are controversial components of GNOME Core. The only major Linux distribution I am aware of to include GNOME Web by default is elementary OS.

Boxes is ok, but it's an unusual app to be part of the default install since it's a virtual machine app.

You're more than welcome to use any of those apps, but currently especially for Boxes and Web, I think opt in is better than having them be automatically installed.

Ubuntu GNOME has considered offering a minimal and full version of the metapackage but it needs someone to volunteer to create them.

---

### Post by jtfolden on 2018-01-10
Thanks for the reply. I'd normally be happy to create something like that but it is outside the scope of my knowledge currently. ;-) I was just looking for a way to get from point A to point B quickly when installing on a few computers here, since Ubuntu GNOME is no longer available as a separate download, plus have all the latest apps installed to test and explore their progress.

---

