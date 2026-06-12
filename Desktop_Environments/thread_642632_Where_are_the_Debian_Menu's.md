---
title: "Where are the Debian Menu's?"
date: 2007-12-16
forum: Desktop Environments
---

### Post by felixdzerzhinsky on 2007-12-16
There are no entries in the Debian Menu in Gutsy in Fluxbox and in Gnome.

Programs like Grass (GIS Program) are not showing up.

What do I need to install to enable the Debian Menu's?

---

### Post by jewellz on 2007-12-16
These are the commands I got from [glanz at Newbies Linux.com]("http://newbieslinux.com/forum/index.php?webtag=DEFAULT&msg=2692.1") long long ago.

> Now in a terminal do 
[HTML]sudo apt-get update[/HTML]

Then do 

[HTML]sudo apt-get install xfe[/HTML]

May as well get "menu" and menu-xdg too

[HTML]sudo apt-get install menu menu-xdg
[/HTML]
This will make an "other" entry in the menu system that lists all your applications and utilities debian style in one big menu...

Open a term after that and do
[HTML]update-menus[/HTML]

They should still work but... there's [this thread at this Ubuntu forum]("http://ubuntuforums.org/archive/index.php/t-288588.html") that covers reinstalling

---

