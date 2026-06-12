---
title: "[SOLVED] Intalling KDE in a clean manner"
date: 2008-03-29
forum: Desktop Environments
---

### Post by dstein on 2008-03-29
I am currently using Ubuntu wuth Gnome. I think that I would like to check out KDE. I found installation instructions at [https://help.ubuntu.com/community/InstallingKDE](https://help.ubuntu.com/community/InstallingKDE). However, I have reasons to believe that this will cause a mess. A few months ago, I installed Koctave on my machine, which installed some KDE libraries and programs, which were added to my 'Applications' menu. At the time, I just wanted Koctave, and all the additional programs seemed to just cause a mess in my Gnome environment.

Is there any way to install KDE, such that it is completely separate from my Gnome environment? I am probably not wording this correctly, but I would like my KDE programs to only appear accessible from KDE and my Gnome programs to only appear accessible from Gnome.

Does anyone have any suggestions for installing a second desktop environment? Any reasons why I should refrain from doing this? Thanks!

---

### Post by kellemes on 2008-03-29
> **dstein said:**
> 
Is there any way to install KDE, such that it is completely separate from my Gnome environment? I am probably not wording this correctly, but I would like my KDE programs to only appear accessible from KDE and my Gnome programs to only appear accessible from Gnome.

No.
Don't see the issue by the way.. Gnome or KDE application don't exist. The simple fact one application makes use of some specific toolkit doesn't mean it may only be run in one specific dm.
They aren't and shouldn't be locked in to any environment.. that's the beauty of GNU/Linux.. you can have it all, any time, any place..

---

### Post by dstein on 2008-03-29
Oh, I didn't realize that packages that use one environment's toolkit would run smoothly in the other environment. I guess my question is irrelevant. For some reason, I kinda thought that all the KDE packages that were installed when I installed Koctave didn't work, but I'm probably mistaken. Thanks.

---

### Post by ajgreeny on 2008-03-29
And don't forget you can always edit out of the main menu the items you either don't want or need to show.  Just right click in the menu on the panel and chose Edit to do it by simply unchecking the unwanted items.  You can even delete them from the menu if you want, but you never know, you might want them back sometime in the future, so just uncheck them and you can always add them back in to the menu if you need to.

The best way to add KDE, I think is to use ```
sudo aptitude install kubuntu-desktop
```

---

