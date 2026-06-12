---
title: "Enlightenment under Ubuntu"
date: 2006-12-30
forum: Desktop Environments
---

### Post by CapitalT on 2006-12-30
Hi all,

I installed E on my Ubuntu edgy laptop, everything went fine.

But some menus (I'm looking at you Enlightenment Epplets menu :evil: ) are longer than the screen, and when I open them the parent menu flies off the screen (vertically) and it you have a microsecond to highlight the child menu or it will disappear.

I'm pretty sure anyone who has tried E faced the same thing, but did any one find the antidote?

---

### Post by finferflu on 2007-01-08
You could give a look to E17, it's a lot prettier than E16 and easier to customize. An easy how to: [http://ubuntuforums.org/showthread.php?t=319336](http://ubuntuforums.org/showthread.php?t=319336)

Have fun!

---

### Post by dbbolton on 2007-01-14
> **CapitalT said:**
> Hi all,

I installed E on my Ubuntu edgy laptop, everything went fine.

But some menus (I'm looking at you Enlightenment Epplets menu :evil: ) are longer than the screen, and when I open them the parent menu flies off the screen (vertically) and it you have a microsecond to highlight the child menu or it will disappear.

I'm pretty sure anyone who has tried E faced the same thing, but did any one find the antidote?
if there were a way to disable icons in the menu...

---

### Post by jcankrom on 2007-07-05
you can disable icons in the menu...
edit the *.menu files in your .enlightenment directory (its hidden by default, as are all .---- directories)
the *.menu files are text files with entries following this format:
name [TAB] icon [TAB] type [TAB] command
where name is what appears in your menu and type is either exec (for programs) or menu (for submenus)

change all the icon paths to NULL and poof! no more icons. now the epplets menu should be small enough to fit on your screen.

---

