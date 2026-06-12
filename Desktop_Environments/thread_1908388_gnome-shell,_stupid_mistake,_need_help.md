---
title: "gnome-shell, stupid mistake, need help"
date: 2012-01-13
forum: Desktop Environments
---

### Post by ratcheer on 2012-01-13
I have made a very stupid mistake, following the latest gnome-shell PPA on my "production" Ubuntu installation. Two lib packages were held back and I decided to do a full upgrade. This removed packages **ubuntu-desktop** and **eog**. I cannot reinstall them without ripping out about 50 packages of gnome-shell stuff.

So, I am stuck in my current session until I can figure out how to resolve this. Maybe I should just let it rip out gnome-shell?

I need help and advice. Thanks.

Tim

---

### Post by ratcheer on 2012-01-13
Here are the two packages that made the mess:

```
Preparing to replace libglib2.0-bin 2.31.8-0ubuntu1~11.10~ricotz0 (using .../libglib2.0-bin_2.31.8+git20120111.c3d6595f-0ubuntu1~11.10~ricotz0_amd64.deb) ...
Unpacking replacement libglib2.0-bin ...
Preparing to replace libglib2.0-0 2.31.8-0ubuntu1~11.10~ricotz0 (using .../libglib2.0-0_2.31.8+git20120111.c3d6595f-0ubuntu1~11.10~ricotz0_amd64.deb) ...
```

How do I back them out to their prior versions? Then, I should be able to install ubuntu-desktop and eog.

Tim

---

### Post by Krytarik on 2012-01-13
> **ratcheer said:**
> Here are the two packages that made the mess:

```
Preparing to replace libglib2.0-bin 2.31.8-0ubuntu1~11.10~ricotz0 (using .../libglib2.0-bin_2.31.8+git20120111.c3d6595f-0ubuntu1~11.10~ricotz0_amd64.deb) ...
Unpacking replacement libglib2.0-bin ...
Preparing to replace libglib2.0-0 2.31.8-0ubuntu1~11.10~ricotz0 (using .../libglib2.0-0_2.31.8+git20120111.c3d6595f-0ubuntu1~11.10~ricotz0_amd64.deb) ...
```How do I back them out to their prior versions? Then, I should be able to install ubuntu-desktop and eog.
Well, you could 'force down the version' with Synaptic and then lock those packages to that prior versions, but I wouldn't be surprised if that would remove the other packages from that PPA as well.

Otherwise, "ubuntu-desktop" is just a "[meta-package]("https://help.ubuntu.com/community/MetaPackages")", so this alone wouldn't remove any 'real' package, but it shouldn't stay removed in the long run. And reg. "eog", well it's just the Image Viewer, which I find quite nice and useful, of course, but if you don't need it ...

Hope that helps.

---

### Post by ratcheer on 2012-01-13
Ok, apparently the prior version is no longer in the PPA. The only versions that the "Force package version" shows are the one that is installed and the standard Oneiric version. I had gotten the same result from "aptitude versions libglib2.0-0 libglib2.0-bin", so I guess that is correct.

It seems you are saying I won't have much trouble if I just leave things the way they are for the time being. I'm going to try that and see. If I can't get back to my desktop, I can come back in Arch, heh heh.

Thank you very much, @Krytarik.

Tim

---

### Post by ratcheer on 2012-01-13
Well, I got back up, in a way. My wallpaper is gone and my windows look funny - I suppose the theme is messed up. Maybe this will straighten out in a few days.

I wish I wasn't so bull-headed about having all the latest updates. Sigh...

Tim

---

### Post by Krytarik on 2012-01-13
> **ratcheer said:**
> Ok, apparently the prior version is no longer in the PPA. The only versions that the "Force package version" shows are the one that is installed and the standard Oneiric version.
Yeah, I was indeed meaning the version in the official repos, as "superseded" packages in PPAs aren't easily accessible anymore then.

But I had a closer look into that PPA and the conflicting packages now; the package solely responsible for removing "eog" and thereby also of "ubuntu-desktop" (as "eog" is a dependency of it) is:

**libglib2.0-0**-2.31.8+git20120111.c3d6595f-0ubuntu1~11.10~ricotz0:
```
Package: libglib2.0-0
Source: glib2.0
Version: 2.31.8+git20120111.c3d6595f-0ubuntu1~11.10~ricotz0
Architecture: amd64
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Installed-Size: 3876
Pre-Depends: multiarch-support
Depends: libc6 (>= 2.9), libffi6 (>= 3.0.4), libpcre3 (>= 8.10), libselinux1 (>= 1.32), zlib1g (>= 1:1.2.2)
Recommends: libglib2.0-data, shared-mime-info
Conflicts: bamfdaemon (<= 0.2.92-0ubuntu1), libzeitgeist-gio, wncksyncdaemon
**Breaks: eog (<< 3.2.2-2ubuntu3)**, gdm3 (<< 3.0.3), gnome-control-center (<< 1:3), gnome-session (<< 3.0.0-3), gvfs (<< 1.8), libgtk-3-0 (<< 3.0.12)
Replaces: libglib2.0-dev (<< 2.23.2-2)
Section: libs
Priority: optional
Multi-Arch: same
Homepage: http://www.gtk.org/
Description: GLib library of C routines
 GLib is a library containing many useful C routines for things such
 as trees, hashes, lists, and strings.  It is a useful general-purpose
 C library used by projects such as GTK+, GIMP, and GNOME.
 .
 This package contains the shared libraries.
Original-Maintainer: Debian GNOME Maintainers <pkg-gnome-maintainers@lists.alioth.debian.org>
```And the very last version prior to that doesn't break "eog"; you can download the respective both deb-packages from here and install them manually, and then lock those versions, if the installation of them wouldn't remove the other current packages from that PPA:

[https://launchpad.net/~ricotz/+archive/testing/+build/3082806]("https://launchpad.net/%7Ericotz/+archive/testing/+build/3082806")

Maybe that also fixes the other issues you've just noticed.

---

### Post by Frogs Hair on 2012-01-13
I just had a withheld package for my E17 PPA this morning and had to wait an hour . It is hard for me to have things untidy in the update manager synaptic . I found it's best to wait for the package and avoid running partial upgrades .

---

### Post by ratcheer on 2012-01-13
> **Krytarik said:**
> And the very last version prior to that doesn't break "eog"; you can download the respective both deb-packages from here and install them manually, and then lock those versions, if the installation of them wouldn't remove the other current packages from that PPA:

[https://launchpad.net/~ricotz/+archive/testing/+build/3082806]("https://launchpad.net/%7Ericotz/+archive/testing/+build/3082806")

Maybe that also fixes the other issues you've just noticed.

Thanks so much. That fixed everything back up. I didn't even have to do anything to reset my wallpaper and theme, they just came back.

Please tell me how you found that page on Launchpad with the prior version of the packages. That is a level deeper than the stuff I had managed to find. I still have a lot to learn, even though I've been wrestling with this stuff for about three years, now.

Tim

---

### Post by ratcheer on 2012-01-13
> **Frogs Hair said:**
> I just had a withheld package for my E17 PPA this morning and had to wait an hour . It is hard for me to have things untidy in the update manager synaptic . I found it's best to wait for the package and avoid running partial upgrades .

I know, I know. I knew it before I did it, that's why part of the thread title is "stupid mistake".

Thanks,
Tim

---

### Post by Krytarik on 2012-01-13
> **ratcheer said:**
> Thanks so much. That fixed everything back up. I didn't even have to do anything to reset my wallpaper and theme, they just came back.

Please tell me how you found that page on Launchpad with the prior version of the packages. ...
Great that it worked! :D

To find all the previous versions of packages in a PPA (and also to filter them by their names if needed), click on "View package details" on the main page of the PPA, then change "Published" to "Superseded".

---

### Post by ratcheer on 2012-01-13
> **Krytarik said:**
> Great that it worked! :D

To find all the previous versions of packages in a PPA (and also to filter them by their names if needed), click on "View package details" on the main page of the PPA, then change "Published" to "Superseded".

Excellent. That is an option I have never noticed.

Tim

---

