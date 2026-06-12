---
title: "Wine: System font contains only garbage characters"
date: 2010-02-20
forum: Desktop Environments
---

### Post by helenuh on 2010-02-20
Hi,

I am having the same problem as discussed in [http://ubuntuforums.org/showthread.php?t=274052](http://ubuntuforums.org/showthread.php?t=274052) but since I was not allowed to reply to that thread (has it been archieved?) I ask for help here.

Ubuntu 9.10, Wine 1.0.1. Problem appeared after I upgraded from 8 to 9.10

At first, none of the fonts selected in winecfg (menu texts etc) worked: all gave only hyphens and dots etc. I then selected one of the few fonts that did work (Courier) for all elements, so now they work. Except that for some elements (for example "control text"), the font can not be chosen.

I have created four files system.fon, System.fon, system.ttf and System.ttf and put them everywhere where I could imagine Wine might load them from, but it doens't help.

Maybe the system font has some other file name? Or must I edit the registry? Or I didn't manage to locate the directory from where Wine loads the system font?

Any help greatly appreciated!

Helene

Edit: upgrading to wine1.2 solves the issue. [https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)

---

