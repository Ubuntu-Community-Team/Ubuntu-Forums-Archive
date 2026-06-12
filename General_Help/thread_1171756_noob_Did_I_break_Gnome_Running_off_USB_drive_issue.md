---
title: "noob: Did I break Gnome? Running off USB drive issue."
date: 2009-05-27
forum: General Help
---

### Post by jorx on 2009-05-27
Hi everybody,

I'm getting the feel for U.E. (Ultimate Ubuntu) and fooling around with it in my spare time.  
It boots off of a 16GB USB flash jump drive which is fantastic.

I was experimenting with it on my laptop- and one thing I tried (unwisely) experimenting with was putting the laptop into "sleep" mode, and then removing the USB drive. That- predictably- caused the computer to cease working upon power up. I thought "No big deal, nothing on the USB drive is harmed". So I powered off my laptop.

Upon reboot, which automatically boots into Gnome, I find that that the taskbars are missing! So all I have is the wallpaper and the desktop icons.  It's kind of difficult to do anything. 

I'm not sure how to tell Gnome to shut down or reboot- haven't had much luck with "init 3" 

Any advice would be appreciated!

---

### Post by unutbu on 2009-05-27
There is probably an elegant way to solve this problem, but I don't know the elegant way, so I will share with you my sledge-hammer approach to solving GNOME problems:

Open a terminal and type
```

mv ~/.config{,-old}
mv ~/.gnome2{,-old}
mv ~/.gconf{,-old} 
```

This will rename the .config, .gnome2, and .gconf directories to directories of the same name with "-old" appended.

All your GNOME configuration settings are held in one of these three directories (as far as I know). 

Log out and log back in.

GNOME will detect that these directories are missing, and will create new ones for you which have the default settings. Your GNOME environment should behave like it did when you first installed.

WARNING: If this works, you will have to redo all your GNOME settings (background, font size, etc.).

Once you get your GNOME settings back as you like them, you are free to delete the three *-old directories.

---

### Post by jorx on 2009-05-29
Fortunately upon a third reboot- it appeared Gnome no longer had that problem.
But thank you for your advice- I'm taking notes and will remember this!

---

