---
title: "menu editor move item up/down does not work"
date: 2014-08-22
forum: Desktop Environments
---

### Post by frank52 on 2014-08-22
hello,

i am running ubuntu 14.04 w/ gnome and gnome flashback installed.

i am trying to do something very simple: arrange items in the applications menu using the menu editor by using the up/down arrows.

it doesn't work - changes aren't stored.

any ideas?

---

### Post by kansasnoob on 2014-08-22
I tried and it's working here. In this example you can see I've moved Accessories clear down below Internet:

[ATTACH=CONFIG]255724[/ATTACH]

Is this a fresh install or an upgrade? I ask because I've seen problems reported regarding Precise -> Trusty upgrades:

[http://ubuntuforums.org/showthread.php?t=2239208](http://ubuntuforums.org/showthread.php?t=2239208)

[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1357450](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1357450)

No idea how to fix it though :cry:

My personal policy regarding borked upgrades is that they're not worth a lot of fuss. I'll usually try a few things like this:

[http://ubuntuforums.org/showthread.php?t=2240033&page=2&p=13103395#post13103395](http://ubuntuforums.org/showthread.php?t=2240033&page=2&p=13103395#post13103395)

If I can't resolve issues after running those commands in various orders a few times (and following any advice given by them) I just create a full backup of anything important and start over with a fresh install.

Dual booters and those using multiple partitions should be acutely aware of this bug:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

---

### Post by frank52 on 2014-08-22
i'm only trying to move items within a submenu.  for example, thunderbird up 2 positions in the internet submenu.

the system will let me hide a submenu,  i simply want to change the position.

the other computer that runs 14.04 w/ flashback doesn't have the menulibre editor installed.  the menu is edited from the mainmenu accessory selection and works fine.

---

### Post by frank52 on 2014-08-23
this bug/issue was supposedly 'fixed' at some point this year.  apparently it didn't make this distribution, but should have been added to a update?

---

### Post by frank52 on 2014-08-23
here's the fix:

[http://askubuntu.com/questions/430230/gnome-menu-broken](http://askubuntu.com/questions/430230/gnome-menu-broken)

---

