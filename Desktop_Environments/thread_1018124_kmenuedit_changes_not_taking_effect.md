---
title: "kmenuedit changes not taking effect"
date: 2008-12-21
forum: Desktop Environments
---

### Post by duane-tech on 2008-12-21
I had KDE 4 and removed it for KDE 3 which I like better. Unfortunately, now kmenuedit changes do not take effect.

/etc/xdg/menus/kde-applications.menu contains the line:
        <MergeFile>applications-kmenuedit.menu</MergeFile>

kmenuedit alters the file:  ~/.config/menus/applications-kmenuedit.menu

Does anyone know what is wrong?

PS
KDE 3.5 in Kubuntu 8.0.4 (Hardy)

---

### Post by Zorael on 2008-12-23
Like this, right?
```
        <MergeDir>applications-merged</MergeDir>
        <MergeFile>applications-kmenuedit.menu</MergeFile>
```
Not sure, never happened to me. I'd try creating a new user and see if it happens to him as well, just to rule out there being something wrong with *your* applications-kmenuedit.menu file.

Perhaps reinstalling kmenuedit would help, too, though now I'm just guessing. Granted that one even exists in the Hardy repos; it obviously doesn't in Intrepid's.
```
$ sudo aptitude reinstall kmenuedit
```

As a side-note, KDE 4.2 is shaping up nicely, worlds better than 4.0.x and 4.1.x. There's still the matter of the video garbage upon drawing new objects [SIZE="1"][[1]](http://bugs.kde.org/show_bug.cgi?id=170462) [[2]](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/254468)[/SIZE], for which there's now a workaround at the expense of performance, as a temporary compromise. Unless you have a recent Nvidia card as ther 180+ drivers circumvent the issue.

---

