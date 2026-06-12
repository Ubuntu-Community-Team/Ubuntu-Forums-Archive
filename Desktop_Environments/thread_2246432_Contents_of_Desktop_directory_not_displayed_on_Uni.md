---
title: "Contents of Desktop directory not displayed on Unity desktop"
date: 2014-09-30
forum: Desktop Environments
---

### Post by ufarmer on 2014-09-30
The title says it all.  Is the Unity desktop supposed to display icons for the contents of the Desktop directory?  If so, my installation is not.  Is there a trick?

---

### Post by Frogs Hair on 2014-09-30
If I understand correctly open appearance behavior and enable the launcher icon.

---

### Post by deadflowr on 2014-09-30
See if the settings for show-desktop-icons is true or false.
A quick way through the terminal is
```
gsettings get org.gnome.desktop.background show-desktop-icons
```
if false, then change it using
```
gsettings set org.gnome.desktop.background show-desktop-icons true
```

A longer way is to do this with graphical program, dconf editor.
You would simply follow the same path as laid out above.
org > gnome > desktop > background > check/uncheck show-desktop-icons

But anyway, see if that helps.

---

### Post by Frogs Hair on 2014-09-30
If you are asking about displaying your home directory on the desktop see above. I was thinking of show desktop. If the home folder is in the launcher already right click and there are shortcuts to the default sub directories.

---

### Post by grahammechanical on 2014-09-30
The Unity desktop is supposed to be empty of icons. The File Manager (Nautilus) will show that with a default install of Ubuntu 14.04 the Desktop folder/directory is empty. Therefore there is nothing to show on the desktop. But right click the desktop and click New Folder or New Document and corresponding icons will appear on the desktop and now you will see the Desktop folder/directory being populated.

The Dash is where the Unity user interface holds the links/icons for applications and documents/files that may have been on the Ubuntu desktop of some years ago.

Regards.

---

### Post by Dennis N on 2014-09-30
Show Desktop Icons:
Ubuntu Tweak has a setting to turn these on or off.
**Start Ubuntu Tweak > Tweaks Tab > Show Desktop Icons > On**
'**On**' setting displays icons for files in Desktop folder at a minimum; you can select other icons to display as well: Computer, Trash, Network, ...
'**Off**' setting displays nothing.
Reference System: Ubuntu 12.04

---

### Post by ufarmer on 2014-10-01
Thanks to all.  deadflowr's suggestion was the first thing I tried and it worked.  So strange that has to be enabled.  Ditching Unity is getting higher on my list of things to do.

Is there any way to mark this as solved?  I can't edit the original title and I can't find any such option.

---

### Post by vasa1 on 2014-10-01
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by deadflowr on 2014-10-01
> **ufarmer said:**
> Thanks to all.  deadflowr's suggestion was the first thing I tried and it worked.  So strange that has to be enabled.  Ditching Unity is getting higher on my list of things to do.


Do you have any other desktops installed, maybe a gnome desktop, like gnome-shell.
Unity uses the file manager to handle the desktop, by default(which is what that setting controls)
But gnome-shell does not.
They would share the setting( meaning both are able to set it and unset it), so it could be possible for shell to turn it off, I would think, maybe.
Hope something here makes sense...

---

### Post by ufarmer on 2014-10-01
When I upgraded to 14.04, I tried to install the Gnome classic shell and it was a disaster so I did a fresh installation of 14.04, with cursed Unity, and I have left it alone since.  But Unity has officially soured me on Ubuntu.  On another thread, someone recommended Mate but, at this point, I am just as inclined to try another distro as I am to try to get rid of Unity again.

---

### Post by ufarmer on 2014-10-01
Thanks, vasa1.  I guess I should mark this thread as SOLVED twice. :-)

---

