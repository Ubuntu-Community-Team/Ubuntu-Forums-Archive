---
title: "not displaying... bar... thingies..."
date: 2008-12-02
forum: Desktop Environments
---

### Post by stupu on 2008-12-02
ill just start by saying sorry for any incoherence, im really tired and in a rush. sorry! :)

on booting this morning i skipped a "routine hard drive check" or something (like i said, in a rush), and when i logged in all was fine, had some of the instability i had put down to old hardware (im a lazy troubleshooter, i must admit), like firefox crashing. normally, this leads to a freeze up, reboot and then flawless running for the rest of the day, so really, the earlier the better.

but this time it didnt freeze up... it just kept going, crashing firefox every few minutes, so i decided to preempt the problem, restarting the session. ive had smarter moves.

when i logged back in i saw this: [http://i79.photobucket.com/albums/j125/Stupu/Screenshot.png](http://i79.photobucket.com/albums/j125/Stupu/Screenshot.png) 

im not really sure how to describe it, so hope you can see that. if not, then ill try; the bars along the tops of the windows (i am killing myself over what to call them) have vanished, i cant alt-tab or drag windows either... i would normally just go nuts at a problem like this and reinstall so much crap so badly the computer dies, and id like to try something new and ASK for help.

appreciate anything anyone can offer as to how to fix this, though i wont be able to get back to this til after school.

---

### Post by the yawner on 2008-12-02
> **stupu said:**
> 
when i logged back in i saw this: [http://i79.photobucket.com/albums/j125/Stupu/Screenshot.png](http://i79.photobucket.com/albums/j125/Stupu/Screenshot.png) 

im not really sure how to describe it, so hope you can see that. if not, then ill try; the bars along the tops of the windows (_i am killing myself over what to call them_) have vanished, i cant alt-tab or drag windows either... i would normally just go nuts at a problem like this and reinstall so much crap so badly the computer dies, and id like to try something new and ASK for help.

appreciate anything anyone can offer as to how to fix this, though i wont be able to get back to this til after school.

Those are called window decorations. There is usually one program that handles that called a window manager. In Xfce (and Xubuntu) the default is usually xfwm4. But in case you're using Compiz it might be changed to gtk-window-decorator or perhaps emerald.

Is this problem persistent after a reboot?

---

### Post by stupu on 2008-12-02
yeah, ive tried rebooting, didnt help im afraid. :/

EDIT: knowing what to look for, i found this thread [http://ubuntuforums.org/showthread.php?t=778423&highlight=window+decorations](http://ubuntuforums.org/showthread.php?t=778423&highlight=window+decorations) which seems to have solved the problem (simply run xfwm4 *slaps head*)

thanks muchly :D

---

