---
title: "update-menus problem"
date: 2007-03-10
forum: Desktop Environments
---

### Post by Feck on 2007-03-10
Hey folks!
     :confused: Major issue here. I am currently in the midst of "customizing" fluxbox, but there seems to be a major issue. The sudo update-menus command doesn't seem to exist! Every time I run update-menus, it tells me that the command could not be found. I think this might be a major problem as the lack of that command seems to have left my menus in fluxbox completely blank.

Can anyone shed some insight into this for me? Thanks!

Cheers,
Feck

---

### Post by Raavea on 2007-03-10
Have you tried this: [http://ubuntuforums.org/showpost.php?p=2151986&postcount=109](http://ubuntuforums.org/showpost.php?p=2151986&postcount=109)
My menu was fine, so I've never had to do update-menus, and I am pretty new myself, but this person helped me with a lot of my issues, so I thought the link might be worth trying for you.

Good luck!

---

### Post by RedSquirrel on 2007-03-11
> **Feck said:**
> Hey folks!
     :confused: Major issue here. I am currently in the midst of "customizing" fluxbox, but there seems to be a major issue. The sudo update-menus command doesn't seem to exist! Every time I run update-menus, it tells me that the command could not be found. I think this might be a major problem as the lack of that command seems to have left my menus in fluxbox completely blank.

Can anyone shed some insight into this for me? Thanks!

Cheers,
Feck


It looks like you don't have the **menu** package installed.

How did you install Fluxbox? If you installed it from the repositories, the menu package should have been installed automatically.

You can install the menu package like this:

```
sudo aptitude update
sudo aptitude install menu

```If you compiled Fluxbox yourself, you are probably also missing some of the files that 'update-menus' uses to build the Fluxbox menu.

Instead of all that, you can use **fluxbox-generate_menu**, as suggested by the link Raavea gave. Actually, fluxbox-generate_menu makes a nice menu and you don't need the menu package to create it. It's up to you. ;)

---

