---
title: "How to add an entry to the Places menu?"
date: 2006-11-07
forum: Desktop Environments
---

### Post by mesh2005 on 2006-11-07
Is it possible to add a location to the places menu? if so, how?

---

### Post by pandu.rs on 2006-11-07
drag and drop

---

### Post by pandu.rs on 2006-11-07
> **pandu.rs said:**
> drag and drop
in nautilus

---

### Post by bluenova on 2006-11-07
When you are in the folder that you want in your places menu, goto Bookmarks > Add Bookmark. It will then appear in your places menu.

---

### Post by CarpKing on 2006-11-07
Is there a way to remove the entries that are there by default?  In Dapper, I created a folder called "Documents" in my Home folder, and it automatically showed up on the Places menu.  Since upgrading to Edgy, that entry has disappeared from the side panel in the file chooser, but stayed in the menu and in Nautilus.  If I add it as a bookmark in the file chooser, it shows up twice in the places it was before.

---

### Post by CatKiller on 2006-11-07
Does Bookmarks -> Edit Bookmarks -> Remove not work then?

---

### Post by CarpKing on 2006-11-07
> **CatKiller said:**
> Does Bookmarks -> Edit Bookmarks -> Remove not work then?

It works for the bookmark that was added by me (the one that shows up everywhere), but not the one that was automatically added under Dapper (the one that doesn't show up in the file chooser).  The latter does not show up in Bookmarks-->Edit, and falls above the line between bookmarks and default places in the Nautilus side pane.

---

### Post by mesh2005 on 2006-11-08
Thank you :)

---

### Post by CatKiller on 2006-11-08
> **CarpKing said:**
> It works for the bookmark that was added by me (the one that shows up everywhere), but not the one that was automatically added under Dapper (the one that doesn't show up in the file chooser).  The latter does not show up in Bookmarks-->Edit, and falls above the line between bookmarks and default places in the Nautilus side pane.

I find it weird that this is there at all. You say it appeared automatically when you made the directory - you don't remember doing anything else with it? I've made many directories in my Home folder, and never had any appear in the Places menu. I'm quite interested to know how this happened.

---

### Post by klato on 2006-11-08
My "Documents" directory also showed up automatically in Nautilus, which I thought was kinda cool. That's the only directory it's ever done that for, though (aside from automounted USB devices and such).

---

### Post by CatKiller on 2006-11-08
> **klato said:**
> My "Documents" directory also showed up automatically in Nautilus, which I thought was kinda cool. That's the only directory it's ever done that for, though (aside from automounted USB devices and such).

OMG, that's **insane**. I just tried it, and you're right - then I needed to know the how to get rid of it, since it didn't go away when I deleted the folder. I was quite panicked till I did a **killall gnome-panel**. It seems that it's the super-special nature of the word "Documents" that does it - I wonder if there are any more super-special words? Anyway, if you change the name of that folder and refresh the panel, it should disappear.

EDIT: [https://launchpad.net/distros/ubuntu/+source/nautilus/+bug/22628](https://launchpad.net/distros/ubuntu/+source/nautilus/+bug/22628)

---

### Post by almalaci on 2006-11-12
Now is there a way to put a location into the first part of the "Places" where the "system" places (devices, home, Desktop) are? Add Bookmark puts it in the bottom part, but I want one in the upper part. Can you do that?

---

### Post by CarpKing on 2006-11-13
> **almalaci said:**
> Now is there a way to put a location into the first part of the "Places" where the "system" places (devices, home, Desktop) are? Add Bookmark puts it in the bottom part, but I want one in the upper part. Can you do that?

Naming it "Documents" and placing it in your Home folder is the only way I've ever found.  I wonder if it would work with a symlink?

---

### Post by almalaci on 2006-11-13
Yes, the Documents folder works, also if I mount create a folder under the media folder, and mount an iso file into it, the iso folder appears there as a device. It must be a special symlink

---

