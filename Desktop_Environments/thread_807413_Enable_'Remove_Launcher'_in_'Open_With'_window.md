---
title: "Enable 'Remove Launcher' in 'Open With' window?"
date: 2008-05-25
forum: Desktop Environments
---

### Post by x1a4 on 2008-05-25
Hi,

How do I enable the 'Remove Launcher' menu in the 'Open With' dialog?  

Thank you.

---

### Post by x1a4 on 2008-05-30
Or, if not possible, how do I modify the 'Open With' list.

---

### Post by morgengenuss on 2008-06-01
tbh i don't really see the point of adding the "remove launcher" to the "open with" dialog...
(or are you just referring to the context-menu?)

anyway, if you can rightclick, your either in thunar or on the desktop and for both i have to ask: why would you need a "remove launcher" entry, when you can simply delete the file (i don't even understand the difference between "removing" a launcher and deleting the corresponding .desktop-file).

---

### Post by x1a4 on 2008-06-01
> **morgengenuss said:**
> tbh i don't really see the point of adding the "remove launcher" to the "open with" dialog...
(or are you just referring to the context-menu?)

In Xfce, when you r-click a file and there are several applications the file can be opened with, the context menu has a submenu called 'Open With' which lists those other applications.  There is also a menu item called 'Open With Other Application' which, when clicked, opens a window, entitled 'Open With', containing a list of installed apps to choose from.  The list in this window is divided into two sections: applications in the 'Open With' list and all others.  When I r-click an entry in that list the context menu has one item: 'Remove Launcher', which exists but is disabled in Xubuntu.  According to Xfce documentation this is used to remove launchers from the 'Open With' List.  I want to remove items from that list.  For example, when I r-click a png image the 'Open With' list contains Sunbird, Thunderbird, Firefox and GIMP.  I only want GIMP there.

> when you can simply delete the file

Unless it will remove an application from the 'Open With' list (and nowhere else), I don't want to delete any files.  I want to customize the list of applications displayed in the 'Open With' list.  The Xfce way of doing this is to r-click on the application in the 'Open With' window and clicking 'Remove Launcher', but in Xubuntu this is disabled.

> (i don't even understand the difference between "removing" a launcher and deleting the corresponding .desktop-file).

I suppose there is no difference.  So, where are the .desktop files used for the 'Open With' list of the context menu and the 'Open With' dialog window?  Oh wait, there are none.  I already did a search for .desktop files that might be used in the 'Open With' list but there are none--only menu entries which I most certainly want to keep.

---

### Post by morgengenuss on 2008-06-03
ok, sorry. now i understand your problem. to be honest i'm having my own trouble with this open-with dialog. sometimes when i pick a new default programme to open a file-type thunar doesn't remember it.

i would assume that there must be a file somewhere, containing the correspondences of mime-types and applications (and open-with-dialog options). i'll have a look and report back if i find anything (you can of course do the same if you like).

---

### Post by x1a4 on 2008-08-09
bump it up

---

### Post by archieb0ld on 2008-08-29
Any luck with this one?

---

### Post by x1a4 on 2008-11-14
Nope.

---

### Post by anonymous_user on 2009-02-03
Does anyone know how to customize the Open With list?

---

### Post by Redsandro on 2009-02-26
Bump

I am trying to figure this out myself.

It remembers all typo's as well. :( For text files I now have [I]open with:
mousepad
mousepad\
npp
npp\[/I]

Yeah on certain keyboards, '\' under 'backspace' is my favorite typo key..

---

### Post by Ahunt on 2009-03-26
After a couple of years running Ubuntu we now have one PC running Xubuntu and it is impressive for simplicity and speed!

The only problem we have not been able to solve is the one described in this post originally, which has not been solved here. When you install Sunbird it associates itself with image files, including .jpg and .png under the "open with" menu. If you click on it by mistake it opens Sunbird, creates a new calendar and then an error message, because, of course, you can't open an image file in a calender!

In Gnome it is easy to remove Sunbird from the list of "open with" applications, but in Xubuntu the "remove launcher" is grayed out, disabled. I tried it as "root" and there is no change.

Does anyone have a solution for this yet?

---

### Post by Ahunt on 2009-03-26
Incidentally I had a search through Launchpad looking to see if this has been reported as a bug and can't see that it has been yet.

---

### Post by gaborok on 2009-10-08
To remove unwanted items (added manually in the past) from the "Open With" dialogue:

-Right click on the file you are trying to open with only a certain set of applications
-Then choose the "Open with Other Application..."
-Then click once on the application you wish to remove from the list. If this application was  added/typed in manually in the past, now you can remove it by clicking the "Remove" button.

Log out, then log in or restart to see the change.

Best Regards

---

### Post by Smeagol07 on 2010-08-04
> **x1a4 said:**
> In Xfce, when you r-click a file and there are several applications the file can be opened with, the context menu has a submenu called 'Open With' which lists those other applications.  There is also a menu item called 'Open With Other Application' which, when clicked, opens a window, entitled 'Open With', containing a list of installed apps to choose from.  The list in this window is divided into two sections: applications in the 'Open With' list and all others.  When I r-click an entry in that list the context menu has one item: 'Remove Launcher', which exists but is disabled in Xubuntu.  According to Xfce documentation this is used to remove launchers from the 'Open With' List.  I want to remove items from that list.  For example, when I r-click a png image the 'Open With' list contains Sunbird, Thunderbird, Firefox and GIMP.  I only want GIMP there.

If you want to delete applications from this list you have to edit 
```
/usr/share/applications/mimeinfo.cache
```
If you added item by yourself, or you want to add new item you need to edit ```
~/.local/share/applications/mimeinfo.cache
```
deafault actions are in
```
~/.local/share/applications/defaults.list
```

---

### Post by kmiernik on 2011-05-04
I'm using Xfce 4.8 under Arch Linux, and I had the same problem with open with menu. The last post is close to good answer but not quite solves the problem of custom entries. To remove them from "open with" menu I had to:

1) remove associations from .local/share/applications/mimeapps.list
2) remove from the same directory userapp-XXX-XXX.desktop files listed in mimeapps.list file (this step to clear everything)

---

