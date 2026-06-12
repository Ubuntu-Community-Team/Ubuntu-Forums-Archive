---
title: "How to configure what's shown in Places menu?"
date: 2008-12-07
forum: General Help
---

### Post by t4ggs on 2008-12-07
Hi, I'm trying to do two things, first I want to change the order of the shortcuts in the Places menu, for example...when i click the Places menu i see the following:

Home Folder
Desktop
My Library
Computer
CD/DVD Creator
.
.
.
Search for files
Recent Documents

and i want it to be:

My Library
Home Folder
Computer
CD/DVD Creator
.
.
.

and secondly i want to change the specific icon for the "My Library" shortcut, since its not using the same icon as the respective folder...

thanks...

btw check out this...thats why im doing it..
[http://brainstorm.ubuntu.com/idea/16310/](http://brainstorm.ubuntu.com/idea/16310/)

---

### Post by mk1w86 on 2008-12-07
The top part of the Places menu:

Home Folder
Desktop
etc.

are nautilus bookmarks so editing them under the bookmarks menu in nautilus should change how they look in the menu.


Not sure about the rest though.

---

### Post by t4ggs on 2008-12-07
Yeah i know about the bookmarks, but still they don't look as the seem in the bookmarks menu...and I also want to modify the rest of the shortcuts.

---

### Post by DJ_Peng on 2008-12-07
Open a Nautilus window, then select *Bookmarks > Edit Bookmarks*. That will let you drag and drop the various entries to where you want them. You can also use that window to rename some of the bookmarks to something a little easier to remember what they're for is you need to, although I've never used that to rename system-generated bookmarks.

---

### Post by t4ggs on 2008-12-07
yeah well u r all telling me the same thing...but what i want...
i thank u anyway

---

### Post by lswb on 2008-12-09
Part of places menu, the directory list that usually includes Music, Pictures, etc. can be changed by editing the file .gtk-bookmarks. The directories listed in .gtk-bookmarks will appear on the places menu if they exist. I don't know about the rest of the Places items. God forbid gnome should make it too easy to configure something.

---

### Post by t4ggs on 2008-12-09
> **lswb said:**
> Part of places menu, the directory list that usually includes Music, Pictures, etc. can be changed by editing the file .gtk-bookmarks. The directories listed in .gtk-bookmarks will appear on the places menu if they exist. I don't know about the rest of the Places items. God forbid gnome should make it too easy to configure something.


yeah but these r the same I can edit in the bookmarks... and I don't think it's god's fault. lol.

---

### Post by kking on 2008-12-10
I'm trying to modify my places menu as well, but I'm using xubuntu and don't have nautilus or a ~/.gtk-bookmarks file.

Do I just need that file?  If so, could someone post an example of what it should look like so I can make one?

I could install nautilus, but I'd like to find out what file these settings are stored in.

---

### Post by Donalb on 2008-12-16
I can't imagine why Xubuntu woudln't have that file, but them I know nothing about OSes, other than using them
 I'm on Ubuntu. 
Maybe you can't find it? I remember not too long ago when i was starting on 'buntu, someone mentioning a text file I needed to edit & I literally had no idea how to do that. 
Open a terminal and type
sudo gedit .gtk-bookmarks
enter your passwd and the file should pop up.
 The contents of mine are simple;
"
file:///home/donal/Documents
file:///home/donal/Music
file:///home/donal/Pictures
file:///home/donal/Videos
file:///home/donal/Documents/EyeCandy
file:///home/donal/Downloads
"
Adding 2 extra "places" in Nautilus though has caused the 4 original entries in the <Places> menu to go into a sub-menu. This isn't a big deal for me, as I don't used it much that way, I prefer quick access in the Nautilus sidepane. 
Regards

---

### Post by Stuart P. Bentley on 2009-12-12
How do I change an icon on the Places menu?

---

### Post by Leppie on 2009-12-12
> **kking said:**
> I'm trying to modify my places menu as well, but I'm using xubuntu and don't have nautilus or a ~/.gtk-bookmarks file.

xubuntu uses the same file for Places bookmarks. Also an easy way to create a bookmark is to just drag and drop whatever bookmark you would like to create into the navigation pane in thunar/nautilus.
If you right click existing bookmarks in this pane, you can also rename them ;)

---

