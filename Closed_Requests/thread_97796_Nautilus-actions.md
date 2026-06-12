---
title: "Nautilus-actions"
date: 2005-12-01
forum: Closed Requests
---

### Post by dexae on 2005-12-01
**Nautilus-actions** is an extensions for nautilus which allow to add arbitrary program to launch through the nautilus popup menu of selected files.
  Each time you right-click on one or several selected files in nautilus, **nautilus-actions** will look at its configured actions to see if a program has been setup for this selection. If it is the case, it will add an item in the menu that allow you to execute the program on the selected files.

 And the .deb works perfectly in ubuntu [http://www.grumz.net/index.php?q=taxonomy/term/6/9](http://www.grumz.net/index.php?q=taxonomy/term/6/9)

---

### Post by jdong on 2005-12-01
Yep, also in Dapper... Approved :)

---

### Post by jdong on 2005-12-14
done.

---

### Post by Who on 2005-12-21
Am I going mad, or is this not in the repositories?
If it is, can anyone suggest why I'm not seeing it?

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main restricted universe multiverse

has always worked before!?

Who

---

### Post by jdong on 2005-12-21
nautilus-actions | 0.99-0ubuntu1~breezy1 | breezy-backports | source



the i386 binary failed to build with a "given-back" error from buildd (could not fetch all source packages). I've raised this to the build admins, no response yet. This seems to be happening left and right for any GNOME-related build, whether Backports or Dapper. I'm sure the devs know about it already and are working hard on fixing it :)

---

### Post by gatiba on 2005-12-24
[QUOTE=Who]Am I going mad, or is this not in the repositories?
If it is, can anyone suggest why I'm not seeing it?

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main restricted universe multiverse

has always worked before!?

Who[/QUOTE]

Same problem here :(

---

### Post by Bou on 2005-12-24
[QUOTE=gatiba]Same problem here :([/QUOTE]

Yep, I'm not seeing it either.

---

