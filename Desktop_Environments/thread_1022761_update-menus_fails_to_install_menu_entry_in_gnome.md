---
title: "update-menus fails to install menu entry in gnome"
date: 2008-12-27
forum: Desktop Environments
---

### Post by ub40d on 2008-12-27
I want to add a menu entry (several actually) to my gnome desktop
through some scriptable procedure, not gui-clickety-click because I'll
have to redo the same on several other computers.

I have read [http://www.debian.org/doc/packaging-manuals/menu.html/](http://www.debian.org/doc/packaging-manuals/menu.html/) and
figured I should use update-menus. I've installed

  sudo apt-get install menu

and read the man pages of update-menus and menufile.

I add my entry to /usr/share/menu, I run update-menus without errors,
but then no menu entry appears. Why?

To make this easy to reproduce for those willing to help, here's a
step by step example; please point out what I should fix.

 cd /usr/share/menu
 sudo cp evolution mytest

Now let's edit the file mytest (gksudo emacs mytest). Originally it was

?package(evolution):needs="X11" section="Applications/Network/Communication" \
  title="Evolution" command="/usr/bin/evolution" \
  hints="Gnome,Mail,Calendar" icon="/usr/share/pixmaps/evolution.xpm"

and we now turn it into

?package(mytest):needs="X11" section="Applications/Network/Communication" \
  title="Mytest" command="/usr/bin/evolution" \
  hints="Gnome,Mail,Calendar" \
  icon="/usr/share/icons/gnome/scalable/apps/gnome-terminal.svg"

So what I've done is simply to change the name of the menu entry (and
package) from evolution to mytest and the icon to that of the
terminal. The executable stays the same. What I'd expect is that this
would generate another menu entry near the one for evolution, except
with the name "mytest" and the icon of terminal. Selecting that entry
would launch evolution. Let's go...

 sudo update-menus --nodpkgcheck

This runs without errors but the menu entry does not appear. Even if I
log out and back in. Why?

Note I can also run

 sudo update-menus --nodpkgcheck -v --stdout | fgrep mytest

and I get 

!F /usr/share/menu/mytest
command="/usr/bin/evolution" hints="Gnome,Mail,Calendar" icon="/usr/share/icons/gnome/scalable/apps/gnome-terminal.svg" needs="X11" package="mytest" section="Applications/Network/Communication" title="Mytest"

...which proves that update-menus is "seeing" my entry. So why
does it not get installed?

---

### Post by irishbreakfast on 2009-03-21
I don't have an answer - I have the same problems.

If you found an answer please post.

Thank you

---

