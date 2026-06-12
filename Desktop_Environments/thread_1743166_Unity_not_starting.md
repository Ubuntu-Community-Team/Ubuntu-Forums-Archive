---
title: "Unity not starting"
date: 2011-04-29
forum: Desktop Environments
---

### Post by Kazuki Mishima on 2011-04-29
Since upgrading to Ubuntu 11.04 (amd64), I have been completely unable to start Unity. All I get after entering my login information is the default Ubuntu wallpaper and a cursor. Right clicking, clicking and dragging, etc. accomplish nothing whatsoever. I can switch into console mode, but I can't remember the proper command to logout from my Unity session and return to the login menu. Unlike other users with similar complaints, I have not been changing Compiz settings. I didn't even have the Compiz settings manager installed until a few seconds ago, and the problem started before that. Luckily I can still start into Gnome ("Ubuntu Classic") and do everything from there. But what can I do about Unity?

EDIT: Strangely enough, though, I can hear the Skype startup sound, so something's going on under there.

---

### Post by Kazuki Mishima on 2011-04-29
And now, quite suddenly, Unity works. I'll marked this thread as solved, but I don't know how to delete it.

EDIT: Okay, turns out Unity running properly was just a one-time freak occurrence.

---

### Post by Kazuki Mishima on 2011-04-29
So it turns out this is actually still a problem for me. The most frustrating part is that the result is basically a complete crash -- I can't even go back to the login menu without forcing a restart of my system.

---

### Post by gardy0701 on 2011-05-12
I am having the same issue. I found a way on the forums to get into the virtual terminal, by pressing <Ctrl+Alt+F1> and then from there installing the nautilus terminal, allowing you to right click and open a terminal. 

I do not have the info for this again but I will try to dink around and find it again... 

I am running the Nautilus terminal right now, but it is not a permanent fix, as soon as I close the terminal I lose my desktop again. I think it may be an issue with Compiz since that is the last thing I used before this happened to me.

---

### Post by gardy0701 on 2011-05-12
I do not wan to take the credit here, but I just found another page on the forums that may help you.  

[http://ubuntuforums.org/showthread.php?p=10769680](http://ubuntuforums.org/showthread.php?p=10769680)

If you can open a terminal on your desktop all you need to do is reset Unity. by typing 
unity --reset
I hope this helps. It worked wonders for me!

---

### Post by powerme on 2011-05-12
in terminal : (or before login to desktop,select recovery console)

```
 unity --reset 
``````
 unity --replace
```

---

### Post by jony121 on 2011-08-02
I posted a work around for this: [http://ubuntuforums.org/showthread.php?p=11110777#post11110777](http://ubuntuforums.org/showthread.php?p=11110777#post11110777)

---

