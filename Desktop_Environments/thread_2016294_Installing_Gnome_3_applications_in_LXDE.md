---
title: "Installing Gnome 3 applications in LXDE?"
date: 2012-07-04
forum: Desktop Environments
---

### Post by mikeym on 2012-07-04
Hi,

I'm running Lubuntu on my netbook and I'm wondering if I can install applications for Gnome 3 under LXDE without disappearing down dependency hell? 

I don't have much processing power so don't want to be installing anything that's going to eat it up. 

I use gpodder at the moment to aggregate podcasts but I was advised while trying to post a bug report to try the Gnome 3 version and I don't want to mess up my system.

Thanks for any help.

---

### Post by msammels on 2012-07-04
There is no special reason why gnome-shell or unity applications should not run under LXDE or any other desktop environments.

The only exceptions are applications that make specific use of capabilities and functionality that is very specific to a particular desktop environment.

LXDE/Lubuntu applications you will find are often GTK+ based - thus the vast majority of GTK+ apps you see in blogs running in Unity/Gnome-shell should work for LXDE.

If you are a purist, you should look out for the dependencies that a particular application brings with it. Some applications will have a dependency that would involve installing the majority of one desktop environment/stack.

To test what dependencies an application requires try a simulated install i.e.

```
sudo apt-get -s install [package-name]
```

Look at the sections: The following extra packages will be installed:

and

The following NEW packages will be installed

If the list is particularly lengthy then perhaps you should consider an alternative - less bulky/dependent application.

Occasionally after installing an application, it does not appear in the menu. For these applications have a look at the applications .desktop file in /usr/share/applications. Some applications desktop file has an entry similar to OnlyShowIn=Unity. I would remove this entry and it should (after logging out/logging in) appear in the menu again.

---

### Post by mikeym on 2012-07-04
Is GTK+ something different than I think it is? I thought GTK+ were applications that used basic GTK but not GTK-2 stuff or any of the gnome dependencies. 

The ppa I'm asking about is [gpodder-3]("https://launchpad.net/~thp/+archive/gpodder3") which I believe is specifically gnome-3 (widgets and whathaveyou). 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-pymtp python-mutagen python-gpod
Use 'apt-get autoremove' to remove them.
Suggested packages:
  python-eyed3 gnome-bluetooth bluez-gnome
The following packages will be upgraded:
  gpodder
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Thanks for the heads up about .desktop files, is it a bug that should be reported or is there a rational behind only flagging these apps as Unity?

---

### Post by msammels on 2012-07-04
You could be right there, as the GIMP does use GTK+ on Windows. I don't think you need to report it as a bug, as I think they are working on it - but in all honesty, it's most likely the developers problem.

---

