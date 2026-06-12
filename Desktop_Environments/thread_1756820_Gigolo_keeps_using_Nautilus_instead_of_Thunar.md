---
title: "Gigolo keeps using Nautilus instead of Thunar"
date: 2011-05-12
forum: Desktop Environments
---

### Post by rent0n on 2011-05-12
Hi there,

So, to make a long story short, I've got this Ubuntu 10.04 machine at work where I installed xubuntu-desktop as I'm much more familiar with Xfce than with Gnome.
This means now all Gnome and Xfce related applications are installed (both Nautilus and Thunar, to make an example).

I use Gigolo to access network shares.

Problem is, when I open a network share with Gigolo, Nautilus opens instead of Thunar. This is annoying for a number of reasons and I'm not going to bother you with those.

I want Gigolo to use Thunar instead.

I already did everything that's suggested on the [Gigolo help page]("http://www.uvena.de/gigolo/help.html#open-resources-in-thunar-on-xfce-4-4-and-4-6"), but the problem persists. Uninstalling Nautilus, besides not being an option as this is a multi-user machine, doesn't solve the problem and actually results in this error on the terminal:
```
gvfs-open: smb://192.168.1.252/backup/: error opening location: No application is registered as handling this file
```
[B]
What can I do? How do I associate gvfs-open to Thunar?[/B]

Any help is very appreciated, thanks a lot.

---

### Post by jerrrys on 2011-05-12
maybe

[http://ubuntuforums.org/showthread.php?p=10798437#post10798437](http://ubuntuforums.org/showthread.php?p=10798437#post10798437)

---

### Post by rent0n on 2011-05-13
Nope, but thanks... 
I think I tried everything, any ideas people?

---

### Post by Toz on 2011-05-13
If you go to Edit->Preferences in the Gigolo app, there is an option to specify the File Manager. By default, it is set to gvfs-open. What happens if you change it to Thunar?

Also, here is a link on how to change the default file manager: [https://help.ubuntu.com/community/DefaultFileManager](https://help.ubuntu.com/community/DefaultFileManager)

---

