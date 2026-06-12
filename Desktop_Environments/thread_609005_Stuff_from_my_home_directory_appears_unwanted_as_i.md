---
title: "Stuff from my home directory appears unwanted as icons on my desktop"
date: 2007-11-10
forum: Desktop Environments
---

### Post by pinkunicorn on 2007-11-10
It seems that everything I create on the top level of my home directory appears as unwanted icons on my desktop. This behavior is highly undesired.

When first installing, I removed the slew of empty directories that were created. I have now recreated "Desktop" in the hope that this would fix the problem and leave me with a clean desktop and only one unwanted directory instead of lots of them, but the only thing that happened was that I got yet another icon on my desktop. 

How do I get rid of these icons? (No, "rm -rf ~/" isn't the correct answer.)

---

### Post by Happy_Man on 2007-11-10
You may have accidentally set an option in gconf-editor. Press alt-f2, type in gconf-editor, and browse to apps/nautilus/preferences. Make sure that the entry "desktop_is_home_dir" is unchecked.

---

### Post by pinkunicorn on 2007-11-10
desktop_is_home_dir is already unchecked.

---

### Post by pinkunicorn on 2007-11-15
This problem still persists after a reboot...

---

### Post by pinkunicorn on 2007-11-26
I still have this problem, and desktop_is_home_dir is unchecked. Help, please! :confused:

---

### Post by palletjackracer on 2007-11-26
Has anyone solved this issue?  I am also having the same problem.  I deleted all of the folders in my home directory after I installed Gutsy including Desktop.  Now everything in my home directory appears on my Desktop.  I followed the above instructions but that did not work.

Does anyone have ideas as to how to fix this issue?

Was the Desktop directory a symlink or some other 'special' type of feature?

---

### Post by Happy_Man on 2007-11-26
Try to recreate the Desktop directory. Make a folder in your home directory, call it Desktop (remember the capital D) and reboot, see if that fixes it.

---

### Post by palletjackracer on 2007-11-26
I have already tried that.  It did not work.  I seem to remember the icon for the Desktop folder when first installed was different that the standard directory folder.  This, I am assuming, means that it was some sort of specialized directory.  Can you check to see if/how yours is different?

---

### Post by huffy318 on 2007-11-26
I noticed this when I booted up today.  I *think* it happened because I accidentally un-capitalized ~/Desktop to be ~/desktop.  

But now, I can't get it to go back.  The desktop_is_home_dir switch doesn't do anything for me, though one of them (in schemas) is not settable.  I don't know what that is for.

I am using Gnome on Gutsy.

---

### Post by pinkunicorn on 2007-11-26
> **Happy_Man said:**
> Try to recreate the Desktop directory. Make a folder in your home directory, call it Desktop (remember the capital D) and reboot, see if that fixes it.

Been there, done that, got no effect. :(

```

drwxr-xr-x   2 hans hans  4096 2007-11-18 17:03 Desktop

```

---

### Post by huffy318 on 2007-11-26
This worked for me:

My   ~/.config/user-dirs.dirs  had:
XDG_DESKTOP_DIR="$HOME"
XDG_DOWNLOAD_DIR="$HOME"
< and other lines >

Delete the XDG_DESKTOP_DIR line and then run     xdg-user-dirs-update

In my case, I had to delete XDG_DOWNLOAD_DIR, also, since I had removed my Desktop directory which reset all Desktop references back to $HOME/.

For some reason, just editing the line to say 
XDG_DESKTOP_DIR="$HOME/Desktop"
didn't work.  Nautilus spit out error messages constantly and the CPU was 100%.

---

### Post by erfahren on 2007-11-26
you could try checking the desktop_is_home_dir then restart X and then create the ~/Desktop directory, then uncheck it again 

OR -

(maybe this would be better to try first)

try checking the desktop_is_home_dir then restart X - then uncheck it and see if the directory is automatically created.

---

### Post by palletjackracer on 2007-11-26
The first suggestion worked for me with the exception of needing to restart.  After the restart everything was as it should be.  Thanks!

---

### Post by McLogic on 2008-02-14
I tried to find the problem calling it "the computer forgot   that I had a home directory" 
and "Gnome lost Desktop folder"
and "Desktop is now Home"
but it took some work to find this thread, so I'm adding keywords and a bump!

The below worked for me:

> **huffy318 said:**
> This worked for me:

My   ~/.config/user-dirs.dirs  had:
XDG_DESKTOP_DIR="$HOME"
XDG_DOWNLOAD_DIR="$HOME"
< and other lines >

Delete the XDG_DESKTOP_DIR line and then run     xdg-user-dirs-update

In my case, I had to delete XDG_DOWNLOAD_DIR, also, since I had removed my Desktop directory which reset all Desktop references back to $HOME/.

For some reason, just editing the line to say 
XDG_DESKTOP_DIR="$HOME/Desktop"
didn't work.  Nautilus spit out error messages constantly and the CPU was 100%.

---

### Post by amartins on 2008-05-14
Hi, everyone!

Removing the line:
XDG_DESKTOP_DIR="$HOME"

was enough for me.

Thanks!

---

