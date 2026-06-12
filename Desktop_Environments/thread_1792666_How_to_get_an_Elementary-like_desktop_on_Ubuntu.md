---
title: "How to get an Elementary-like desktop on Ubuntu?"
date: 2011-06-28
forum: Desktop Environments
---

### Post by pimentel28 on 2011-06-28
I certainly do not want to install Elementary OS, and just want a similar interface. I already installed docky, but Unity gets in the way. Is there a way I can disable that?

Also, can I hide the docky application icon on Docky? 

Or is there a better way to do this? 


Thanks in advance!

And just in case...I'm going to go back up my music...

---

### Post by FormatSeize on 2011-06-28
> **pimentel28 said:**
> I certainly do not want to install Elementary OS, and just want a similar interface. I already installed docky, but Unity gets in the way. Is there a way I can disable that?
 
Also, can I hide the docky application icon on Docky? 
 
Or is there a better way to do this? 
 
 
Thanks in advance!

Elementary OS is based on Ubuntu 10.10, which has Gnome 2.32. So that's the desktop environment that it has. It doesn't seem to me that it would be an easy task to go from a Unity set up and stripping it down to an Elementary OS. You can, though, use Gnome-classic, and go from there. It seems that it would be easier that way, and you don't have the thing that is getting in the way of Docky. And then from there, you can go about stripping out things that you don't use (apparently, the common things that things that people don't use are command line text editors like nano, media players, and a few other things).
 
I'm not completely sure if you can hide the application icon on Docky, but I'm sure it's possible. Try:
```
gconf-editor
``` and look through the options for docky there.

---

### Post by pimentel28 on 2011-06-28
> **FormatSeize said:**
> Elementary OS is based on Ubuntu 10.10, which has Gnome 2.32. So that's the desktop environment that it has. It doesn't seem to me that it would be an easy task to go from a Unity set up and stripping it down to an Elementary OS. You can, though, use Gnome-classic, and go from there. It seems that it would be easier that way, and you don't have the thing that is getting in the way of Docky. And then from there, you can go about stripping out things that you don't use (apparently, the common things that things that people don't use are command line text editors like nano, media players, and a few other things).
 
I'm not completely sure if you can hide the application icon on Docky, but I'm sure it's possible. Try:
```
gconf-editor
``` and look through the options for docky there.

Thanks, what do you recommend? Trying to strip down Ubuntu, or just going with a fresh installation of Elementary? Honestly, I only have 2GB's of data to backup...and I use Amazon CloudDrive to backup my data..

---

### Post by FormatSeize on 2011-06-28
> **pimentel28 said:**
> Thanks, what do you recommend? Trying to strip down Ubuntu, or just going with a fresh installation of Elementary? Honestly, I only have 2GB's of data to backup...and I use Amazon CloudDrive to backup my data..
The easiest thing to do is to a fresh installation of Elementary, and then add things from there through the Software Center, like a media player and other toys that you would like to have. 
The very first thing you have to do, though, is to go into gconf-editor and enable right-click, unlock your top panel, and enable the desktop if you want to put stuff there. All of those things are disabled by default.

---

### Post by pimentel28 on 2011-06-28
> **FormatSeize said:**
> The easiest thing to do is to a fresh installation of Elementary, and then add things from there through the Software Center, like a media player and other toys that you would like to have. 
The very first thing you have to do, though, is to go into gconf-editor and enable right-click, unlock your top panel, and enable the desktop if you want to put stuff there. All of those things are disabled by default.

Thanks Format :D Much appreciated! I'll be backing up my data now, since this seems the easiest way. I already downloaded Elementary OS in two minutes, and have it burned on a disc. I'll give a whirl on the LiveCD.

---

### Post by pimentel28 on 2011-06-30
This thread's resolved, thanks a lot :) Already went into gconf-editor and enabled right click/desktop and unlocked the top panel, love my new desktop!

---

### Post by Frogs Hair on 2011-06-30
> **pimentel28 said:**
> This thread's resolved, thanks a lot :) Already went into gconf-editor and enabled right click/desktop and unlocked the top panel, love my new desktop!

Use the thread tools to mark the thread  as solved .:D

---

