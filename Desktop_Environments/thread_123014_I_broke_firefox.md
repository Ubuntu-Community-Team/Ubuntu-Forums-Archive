---
title: "I broke firefox"
date: 2006-01-29
forum: Desktop Environments
---

### Post by koolguynet on 2006-01-29
I did something stupid and now I don't know how to undo it.  In my zeal to upgrade to firefox 1.5 I deleted some files (that I thought I could delete- I bet everyone says that) and began getting an xml error when I tried to launch firefox.  So I thought let's remove and reinstall firefox with Synaptics...sounds good right?  So I did that and Synaptics gives me the following:

E: firefox: subprocess post-installation script returned error exit status 1
E: gnome-app-install: dependency problems - leaving unconfigured
E: firefox-gnome-support: dependency problems - leaving unconfigured
E: yelp: dependency problems - leaving unconfigured
E: ubuntu-desktop: dependency problems - leaving unconfigure

Oh and the same problem still exists with firefox (xml error).  Anyone want to make a recommendation?  Everything else on this box is running fine.

---

### Post by tufkakf on 2006-01-29
You could try to run sudo apt-get -f install in a terminal and see if that solves it.

If it doesn't, post the error message here.

---

### Post by koolguynet on 2006-01-29
I tried that and here is the error message:

sudo apt-get -f install firefox
Reading package lists... Done
Building dependency tree... Done
firefox is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up firefox (1.0.7-0ubuntu20) ...
Updating mozilla-firefox chrome registry.../usr/sbin/update-mozilla-firefox-chrome: line 106: 18144 Segmentation fault      firefox-bin -register >/dev/null 2>&1
E: Registration process existed with status: 139
E: /usr/lib/mozilla-firefox/extensions/installed-extensions.txt still present. Registration might have gone wrong.
mv: cannot stat `/usr/lib/mozilla-firefox/defaults.ini': No such file or directory
dpkg: error processing firefox (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of firefox-gnome-support:
 firefox-gnome-support depends on firefox (= 1.0.7-0ubuntu20); however:
  Package firefox is not configured yet.
dpkg: error processing firefox-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-app-install:
 gnome-app-install depends on firefox | mozilla-firefox; however:
  Package firefox is not configured yet.
  Package mozilla-firefox is not installed.
  Package firefox which provides mozilla-firefox is not configured yet.
dpkg: error processing gnome-app-install (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of yelp:
 yelp depends on firefox; however:
  Package firefox is not configured yet.
dpkg: error processing yelp (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on firefox; however:
  Package firefox is not configured yet.
 ubuntu-desktop depends on firefox-gnome-support; however:
  Package firefox-gnome-support is not configured yet.
 ubuntu-desktop depends on gnome-app-install; however:
  Package gnome-app-install is not configured yet.
 ubuntu-desktop depends on yelp; however:
  Package yelp is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 firefox
 firefox-gnome-support
 gnome-app-install
 yelp
 ubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)



By the way it is a similar error message when I try to install any of the other programs listed in the first post.  Thanks!

---

### Post by koolguynet on 2006-02-02
I fixed it.  I just deleted '/var/lib/mozilla-firefox/' , '/usr/lib/mozilla-firefox/' and the .mozilla directory in my home. Then I reinstalled fiefox using Synaptic.  It now works fine.  Just thought I would share what fixed it.

---

