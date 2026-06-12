---
title: "Gnome Hearts..."
date: 2007-10-22
forum: Gaming &amp; Leisure
---

### Post by rgraves22 on 2007-10-22
Since im the ultra cool uber geek boyfriend, and put linux on my wonderful girlfriends laptop, she wants to play gnome hearts that comes standard on ubu. I run it from both the desktop, and the gnome menu, and it will open, than close. I tried to run it from the terminal, and got ryanjess@ryanjess-laptop:~$ gnome-hearts

** ERROR **: file hearts.c: line 859 (load_card_styles): assertion failed: (directory != NULL)
aborting...
Aborted (core dumped)
ryanjess@ryanjess-laptop:~$ 

:confused::confused::confused:
I'm pretty linux savy, been using ubu since 6.10 came out. but this one definitally becomes me.

---

### Post by rgraves22 on 2007-10-22
If it matters, 

IBM R40 P4 2.4
1 GB RAM. Just recently pushed to gusty from 7.04.

---

### Post by basbeek on 2007-10-24
Yeah i had the same problem,
You see, the default cards are in the /usr/share/gnome-common-games directory while gnome-hearts searches in the /usr/share/pixmaps directory.

A simple symbolic link to the gnome-common-games directory does the trick. To make this, do the following:

cd /usr/share/pixmaps/
sudo ln -s ../gnome-games-common/

Hope this works

Bas

---

### Post by MillDaKill on 2007-11-03
> **basbeek said:**
> Yeah i had the same problem,
You see, the default cards are in the /usr/share/gnome-common-games directory while gnome-hearts searches in the /usr/share/pixmaps directory.

A simple symbolic link to the gnome-common-games directory does the trick. To make this, do the following:

cd /usr/share/pixmaps/
sudo ln -s ../gnome-games-common/

Hope this works

Bas

Thanks for the fix.  Worked for me.

---

### Post by www.rzr.online.fr on 2007-11-04
the bug is still present and reported at : 

[https://bugs.launchpad.net/ubuntu/+source/gnome-hearts/+bug/123623](https://bugs.launchpad.net/ubuntu/+source/gnome-hearts/+bug/123623)

--
[http://rzr.online.fr/q/Game](http://rzr.online.fr/q/Game)

---

### Post by markthecarp on 2007-11-05
> **basbeek said:**
> Yeah i had the same problem,
You see, the default cards are in the /usr/share/gnome-common-games directory while gnome-hearts searches in the /usr/share/pixmaps directory.

A simple symbolic link to the gnome-common-games directory does the trick. To make this, do the following:

cd /usr/share/pixmaps/
sudo ln -s ../gnome-games-common/

Hope this works

Bas

This worked for me as well. I went looking for a fix when editing ~/.gnome-hearts.cfg to look in the correct directory did not work.

-mark

---

### Post by mock47 on 2007-12-12
> **basbeek said:**
> Yeah i had the same problem,
You see, the default cards are in the /usr/share/gnome-common-games directory while gnome-hearts searches in the /usr/share/pixmaps directory.

A simple symbolic link to the gnome-common-games directory does the trick. To make this, do the following:

cd /usr/share/pixmaps/
sudo ln -s ../gnome-games-common/

Hope this works

Bas

Thanks Bas, this worked for me as well.
Art

---

### Post by nikolas68 on 2007-12-13
> **basbeek said:**
> Yeah i had the same problem,
You see, the default cards are in the /usr/share/gnome-common-games directory while gnome-hearts searches in the /usr/share/pixmaps directory.

A simple symbolic link to the gnome-common-games directory does the trick. To make this, do the following:

cd /usr/share/pixmaps/
sudo ln -s ../gnome-games-common/

Hope this works

Bas

My wife was booting into Vista just to play Hearts: SOOOOOO glad i found this thread!!! Thanks Bas

---

### Post by treesurf on 2007-12-24
Thanks very much.  This did the trick for me as well.

---

### Post by beamo on 2007-12-29
Worked for me. Thank you very much.

---

### Post by rgraves22 on 2007-12-31
Sorry for the late update... worked great for me as well.. Thanks m8!!

---

### Post by xMist on 2008-03-05
I love this forum.  Hearts didn't start for me - I assumed it was opening and closing faster than I could tell. Went to Ubuntu Forums.  And now I'm losing to the computer.  :guitar:

Thank you.  These forums have helped me solve so many problems just by searching.

---

### Post by broutcha on 2010-09-09
I just installed this game. Great graphics, great UI.
But it's a pity to see its AI engine being so weak :-/

I've stopped my first game when I had -184 and the others scored 15, 22 and 43. I didn't want to wait until someone would reach 100.
The AI really doesn't try to prevent me from Shooting the Moon or even the Sun, which I managed to do even when no cards are swapped!

The AI of Android's most downloaded free Hearts game (not posting links since it would look like advertisement) is fairly cool in comparison.

---

