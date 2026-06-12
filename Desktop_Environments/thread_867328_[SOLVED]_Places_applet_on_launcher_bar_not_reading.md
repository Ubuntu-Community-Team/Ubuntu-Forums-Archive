---
title: "[SOLVED] Places applet on launcher bar not reading from ~/.gtk-bookmarks"
date: 2008-07-22
forum: Desktop Environments
---

### Post by firstguythere on 2008-07-22
I'm trying xubuntu for the first time (I've used Ubuntu for 6 months or so now) and am trying to add some custom bookmarks to the Places applet/menu (xfce4-places-plugin) that comes default with xubuntu hardy.  I log in as "bob" and have added "/home/bob/Pictures" minus the " to ~/.gtk-bookmarks

When I click on the places menu/applet it does not show the added location, however if I open a file browser window the new location DOES show up in the bookmark frame.  

What am I missing to make the location appear in the Places menu/applet as well?

---

### Post by firstguythere on 2008-07-23
Solved it!  As suspected it was a user error.  As per this link [http://ubuntuforums.org/archive/index.php/t-40603.html]("http://ubuntuforums.org/archive/index.php/t-40603.html")
local file locations need to be formatted as file:///YOURLOCATION NameofLocation not just ///YOURLOCATION (though this does work when browsing with thunar

So after two days work all I had to do was add "file:////home/bob/Pictures Pictures" to "~/.gtk-bookmarks" less the quotes and the shortcut now works.

---

### Post by VitaLiNux on 2008-07-23
Good, Mate! Would you please mark this thread as Solved?:popcorn:

---

### Post by firstguythere on 2008-07-23
> **VitaLiNux said:**
> Good, Mate! Would you please mark this thread as Solved?:popcorn:
I'm new to this forum too, how do I mark this post as solved properly?

---

### Post by firstguythere on 2008-07-23
> **firstguythere said:**
> I'm new to this forum too, how do I mark this post as solved properly?
Figured that out too.

---

