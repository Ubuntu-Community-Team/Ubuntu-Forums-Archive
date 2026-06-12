---
title: "LyX 1.5.3 on Gutsy"
date: 2008-01-19
forum: Education &amp; Science
---

### Post by akniss on 2008-01-19
These debs are for LyX version 1.5.3 on Gutsy (386). If they don't install, I won't be of much help as I these are the first debs I've ever built.  However, you can feel free to post problems or questions here and I'm sure others can help.

[lyx_1.5.3-1_i386.deb](http://w3.uwyo.edu/~akniss/lyx_1.5.3-1_i386.deb)
[lyx-common_1.5.3-1_all.deb](http://w3.uwyo.edu/~akniss/lyx-common_1.5.3-1_all.deb)

Good Luck!

---

### Post by gmayer on 2008-01-20
Those .debs work fine for me, thanks for that

EDIT: Just can't find a menu entry, I think your deb creation left out the .desktop file stuff... Oh well, firing up the command manually also does the trick

---

### Post by akniss on 2008-02-01
> **gmayer said:**
> Those .debs work fine for me, thanks for that

EDIT: Just can't find a menu entry, I think your deb creation left out the .desktop file stuff... Oh well, firing up the command manually also does the trick

Hmmm... that's odd.  I do have a menu entry under Applications > Office.  Not sure why it didn't work for you...  I guess if I try and build more .debs I'll look up info on including the .desktop portion.  Thanks for letting me know.

---

### Post by thisismalhotra on 2008-02-01
Same for me no entry in the menu ... will try few things and let you know if I can make it work... did u use checkinstall to make debs...

Thanks

---

### Post by akniss on 2008-02-02
Would it make a difference if you use KDE or GNOME?  I just used the .debs  a couple days ago to install Lyx on my other laptop, and it also has a menu entry under Applications>Office.  I use gnome on both computers.  I actually don't recall if I used checkinstall or not... I can't seem to find the instructions that I used when building the .debs.  I remember following a link from the forums that had a step-by-step guide, but I sure don't remember where it was.

---

### Post by akniss on 2008-02-02
Found it.  Here's what I did to build the debs:
[LIST=1]
[*]Downloaded the three source files
[*]```
dpkg-source -x *.dsc
```
[*]change into the resulting subdirectory
[*]```
dpkg-buildpackage -rfakeroot
```
[/LIST]
I followed kleeman's post here: [http://ubuntuforums.org/showpost.php?p=4154416&postcount=11](http://ubuntuforums.org/showpost.php?p=4154416&postcount=11)

---

