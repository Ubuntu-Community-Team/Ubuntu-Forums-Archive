---
title: "Firefox Quit Working After Update"
date: 2005-10-12
forum: Desktop Environments
---

### Post by Scanner on 2005-10-12
I am running Hoary, and this afternoon I ran Update manager and to get the latest Firefox 1.07 but I get the following error

E: /var/cache/apt/archives/mozilla-firefox_1.0.7-0ubuntu0.1_i386.deb:  trying to overwrite `/var/lib/mozilla-firefox/extensions.d/00classic', which is also in package firefox
E: /var/cache/apt/archives/mozilla-firefox-gnome-support_1.0.7-0ubuntu0.1_i386.deb:  trying to overwrite `/usr/lib/mozilla-firefox/components/libmozgnome.so', which is also in package firefox-gnome-support

and Firefox 1.06 no longer works.

I tried to unistall Firefox 1.06 knowing that there was an issue in earlier Firefox upgrades that wouldn't allow them to older versions to be overwritten by newer but Ubuntu won't let me do that without un-installing the Ubuntu Desktop and when I run sudo dpkg-reconfigure firefox as noted in a previous post i get the following message

Updating mozilla-firefox chrome registry...E: /usr/lib/mozilla-firefox/extensions/installed-extensions.txt still present. Registration might have gone wrong.
mv: cannot stat `/usr/lib/mozilla-firefox/defaults.ini': No such file or directory

I am at a total loss here?!??!?!

---

### Post by Ampersand on 2005-10-12
The ubuntu-desktop package is a meta-package. It doesn't contain any programs itself, It just has Gnome and various other programs as its dependancies, making it easier to install them all at once (sorry if that's not particularly well explained (: ).  It's safe to remove ubuntu-desktop, so you can uninstall mozilla-firefox and install firefox without losing any other programs.

---

### Post by Lodis4 on 2005-10-12
I had this same issue, ended up reinstalling Hoary. Not a good solution I know, but removing, replacing, and updating did not work. Permissions changing would not work, I even tried installing from source. All a no-go, I was under deadline and reinstalled.

I hope someone comes up with a fix for this!

---

### Post by towsonu2003 on 2005-10-12
[QUOTE=Ampersand]The ubuntu-desktop package is a meta-package. It doesn't contain any programs itself, It just has Gnome and various other programs as its dependancies, making it easier to install them all at once (sorry if that's not particularly well explained (: ).  It's safe to remove ubuntu-desktop, so you can uninstall mozilla-firefox and install firefox without losing any other programs.[/QUOTE]

I had the same program but I had to reboot a couple of times without it started worked again. Why the hell did that happen????

---

### Post by Scanner on 2005-10-13
[QUOTE=Ampersand]The ubuntu-desktop package is a meta-package. It doesn't contain any programs itself, It just has Gnome and various other programs as its dependancies, making it easier to install them all at once (sorry if that's not particularly well explained (: ).  It's safe to remove ubuntu-desktop, so you can uninstall mozilla-firefox and install firefox without losing any other programs.[/QUOTE]

Thanks this worked and I appear to be back up and fully functional. Now is the time to start looking to the upgrade process to Breezy.

---

