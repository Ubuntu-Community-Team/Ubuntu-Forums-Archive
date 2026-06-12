---
title: "edit the locations in the places menu"
date: 2007-08-31
forum: Desktop Effects &amp; Customization
---

### Post by Chymera on 2007-08-31
I want to add my root (filesystem) folder to the places panel.... how do i do that?
(no, i dont want to switch to kde)

also... if this doesn't work how could i assign a shortcut key to opening that folder?

---

### Post by imjustabill on 2007-09-03
You can add any folder you want to the places menu, just open up nautilus and make sure that the side pane is open (hit f9 or go to the view menu to open), make sure places is selected from the dropdown box in the side pane, then just drag any folder you like over to it. Since you cant just drag the / folder, you'll have to grab the "location" box at the top and drag that in.

---

### Post by Inxsible on 2007-09-04
> **Chymera said:**
> I want to add my root (filesystem) folder to the places panel.... how do i do that?
(no, i dont want to switch to kde)

also... if this doesn't work how could i assign a shortcut key to opening that folder?
The Places --> Computer should take you to one level above the Filesystem.

But if you insist on going to the filesystem and having it in your Places menu, you can do this
1) In nautilus browse to the directory first (In your case the filesystem)
2) Press Ctrl + D
[COLOR=Red]OR[/COLOR]
2a) Click on Bookmarks -- > Add Bookmark.

Of course you can do this for n number of folder locations :)

This will create an entry in the Places menu

---

### Post by Inxsible on 2007-09-04
If you want to create a shortcut to opening the folder you can do that too.

I used one of my media buttons to go to my home folder. System --> Preferences --> Keyboard Shortcuts

In that I chose Home folder and gave it a new key binding by pressing the key I wanted as shortcut.


On further inspection, I found that they have an entry for Home folder, but there is no way you can specify a folder there :( so I am not sure if this would work.

But you can always create a launcher on the desktop for it

Right click on desktop --> Create Launcher --> Give it a name and comment.

Command would be ```
nautilus /path/to/folder
``` Assign a nice icon you like and you should be good to go :)

---

