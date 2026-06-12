---
title: "Move a file to a nautilus window with folders in list view"
date: 2010-11-23
forum: Desktop Environments
---

### Post by Sylchat on 2010-11-23
Hi,

I don't know if this is a known issue, but when I want to copy/move a file to a folder containing lots of sub-folder displayed as list, I can't do a simple drag&drop, because there is no empty space to move this file. It will always go into one of the sub-folders...
So obviously I have to go up one folder or to change view from list to Icon or Compact...
Is it a known issue? Is there a solution?
(Using GNOME nautilus 2.30.1)

[[img]http://d.imagehost.org/t/0455/nautilus-move2.jpg[/img]](http://d.imagehost.org/view/0455/nautilus-move2)

---

### Post by ajgreeny on 2010-11-23
Use **Edit-Copy** and **Edit-Paste** from the menus, or temporarily change view to Icon or Compact.

It's not a problem I have ever even thought about, but that seems to be the way round it.

---

### Post by a-user on 2010-11-23
yes it is a known problem. it frustrated me me too. it is the only directory browser i ever met that does not have some kind of empty space to drop into the actuall directory.

and no, using "edit-copy" etc. is by far not a solution. it is a very very slow workaround.

the only reason i don't feel too anoyed is that i mostly use the terminal anyway.

edit: a simple solution for the devs would be to use the first column (the one with the folder name) only as dropplace that goes into the sobfolder. anywhere else (other columns) go into the actual folder.

---

### Post by Sylchat on 2010-11-23
Thanks for confirming! Hopefully we'll get a fix in the near future!

---

### Post by a-user on 2010-11-23
well, when i said "known" problem i ment you are not the only one that has observed this.

but i doubt it is a problem that the devs are aware of. so if you want to have a fix for this you have to write this to the devs. probably the suggestion forum would be a good idea. or look for the nautilus homepage.

---

### Post by Sylchat on 2010-11-23
Ah, I actually misunderstood :p

---

### Post by VanillaMozilla on 2010-11-23
I have seen a bug report on it.  Better just learn to live with it, though.  Sometimes it takes years to get around to problems like that.

---

### Post by CowzRule on 2010-11-23
If you have a middle mouse button, try dragging your file with it to the folder you want to drag it to. When you release you should get a choice to Move, Copy or Link.

---

### Post by Sylchat on 2010-11-23
> **CowzRule said:**
> If you have a middle mouse button, try dragging your file with it to the folder you want to drag it to. When you release you should get a choice to Move, Copy or Link.

Sorry but doesn't work on a window full of folders with no empty space to move to parent.

I have posted this however => [http://brainstorm.ubuntu.com/idea/26531/](http://brainstorm.ubuntu.com/idea/26531/)

Let's see where it goes...

---

### Post by a-user on 2010-11-24
> **CowzRule said:**
> If you have a middle mouse button, try dragging your file with it to the folder you want to drag it to. When you release you should get a choice to Move, Copy or Link.
what exactly has this to do with the issue of this thread?
it is not about the choice of what to do (copy/move) it is about WHERE to copy it. currently it is not possible to chose the ACTUAL folder for this, cause any drop point hits a subfolder. there is no space left as a drop point for the actually seen folder.

---

### Post by Sylchat on 2010-11-24
Hi,

My idea has been marked as duplicate of this one:
[http://brainstorm.ubuntu.com/idea/3286/](http://brainstorm.ubuntu.com/idea/3286/)

"User can paste files only then he clicks RMB on empty space in nautilus. But when there are much more files in folder than could fit on screen, user only can click RMB on file or folder. Then if he wants to paste any item, no "paste" menu item is displayed. User can only find "Paste" in "Edit" menu, so there also must be "Paste" item in RMB menu."

This is also a problem I have experienced, so feel free to click on the green arrow to promote this idea !

cheers

---

### Post by oOarthurOo on 2010-11-25
If your location bar was buttons instead of path, you can drag it onto the name of the folder in the location bar. 

Perhaps dragging the file to the location bar in path mode would also, but i'm not sure about that.

---

### Post by Sylchat on 2010-11-26
> **oOarthurOo said:**
> If your location bar was buttons instead of path, you can drag it onto the name of the folder in the location bar. 

Perhaps dragging the file to the location bar in path mode would also, but i'm not sure about that.

Yes that works thanks! 

I hadn't tried it because it seems the 'toggle location bar' disappeared... and in text mode, the path of the moved file gets copied to the location bar!

Hopefully I found a nautilus script to change the gconf setting (and the scripts menu is available even if there is no empty space in the list folder):

```
#!/bin/bash
# Nautilus script to toggle Location Entry / Pathbar
# (i.e. text entry of paths or button navigaton)
# Owner : Seán Ó Séaghdha
#         sean.anseo@gmail.com
# Based on Toggle-Desktop.sh by Peeyoosh Sangolekar (piyush_sangolekar@hotmail.com)
# http://enli.co.cc/customization/nautilus-script-to-toggle-hideshow-desktop-easily-for-ubuntugnome/
# Install in ~/.gnome2/nautilus-scripts/ and make executable.
# Use: Right click on empty space in Nautilus and choose Toggle Pathbar from the Scripts menu
# Licence : GNU GPL 
# Ver. 0.1 Date: 10-11-2010
# Dependencies : Nautilus

pathbar="gconftool -s --type bool /apps/nautilus/preferences/always_use_location_entry false"
text="gconftool -s --type bool /apps/nautilus/preferences/always_use_location_entry true"
test=$( gconftool-2 --get /apps/nautilus/preferences/always_use_location_entry )

if [ $test = "true" ]; then
	eval $pathbar
else
	eval $text
fi
```

---

### Post by VanillaMozilla on 2010-12-03
EDIT:  disregard this post.


Have you guys tried it recently?  It's fixed.

It just works in Lucid.  Just drag it right to the folder.  Some things do get fixed.

There's no need for any funny workarounds.  I suggest you just close the brainstorm topic(s) if that's possible.

---

### Post by Sylchat on 2010-12-04
> **VanillaMozilla said:**
> Have you guys tried it recently?  It's fixed.

It just works in Lucid.  Just drag it right to the folder.  Some things do get fixed.

There's no need for any funny workarounds.  I suggest you just close the brainstorm topic(s) if that's possible.

Just tried it, but there is no space available at top or bottom of folder list to be able to drag&drop a file to the parent folder. I am not sure you understood what the problem is: it's about doing a drag & drop to a nautilus window in list view that is full of folders. There is no empty space around the list to do the drag&drop. But the solution to move to the last path-button works ! (it's not a workaround).

But at least, I saw the new Ubuntu font in 10.10 that I love and just installed on my 10.04 machine (apt-get install ttf-ubuntu-font-family) :)

---

### Post by VanillaMozilla on 2010-12-05
Yeah, you're right.  My mistake.

I'm pretty sure it's fixed in the appropriate Gnome package, though, and the patch will *eventually* make its way to our desktops.

---

