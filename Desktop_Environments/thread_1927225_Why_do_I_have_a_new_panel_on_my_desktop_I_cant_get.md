---
title: "Why do I have a new panel on my desktop I cant get rid of?"
date: 2012-02-17
forum: Desktop Environments
---

### Post by gardengxc on 2012-02-17
I'm running Ubuntu 11.10 with gnome classic and after a restart I find I have a new panel at the top of my desktop. I hate panels at the top I find they do nothing but get in the way for me but to my surprise I can't do anything to it not even move the bloody thing. Is there a new update to gnome clasic that would do this? If so what is it so I can undo this.

I really love Gnome but I like Gnome the way I set it up.

---

### Post by cortman on 2012-02-17
Alt+right click on panel, "remove panel".

---

### Post by gardengxc on 2012-02-17
First thing I tried. Didn't work.
[IMG]http://oi44.tinypic.com/6qjkvt.jpg

---

### Post by cortman on 2012-02-17
Yes, your problem is different than I envisioned- I thought you were referring to a panel on the top of the screen. I seem to remember from my gnome-fallback days that if I made a panel extra wide, it would act like that. Maybe try Alt+right click on the bottom panel and see what the width is set to?

---

### Post by gardengxc on 2012-02-17
The new bar us independent of any panel. Removing them does nothing same with messing with their properties. Further the content of the new panel isn't anything I put in.

---

### Post by Copper Bezel on 2012-02-17
It's not a panel - it's a Nautilus bug unique to Ubuntu's Gnome 3 that happens in Shell and, apparently, Fallback. I thought this problem had been fixed in the current version of 11.10, though. Weird. 

If you open Advanced Settings (Gnome Tweak Tool) and disable "Have file manager handle the desktop," what happens?

---

### Post by gardengxc on 2012-02-17
My desktop is reduced back to just my wallpaper. The bar disappears along with my with my icons.

---

### Post by Copper Bezel on 2012-02-17
Okay, try this then. Remove the appmenu packages: 

```
sudo apt-get remove appmenu-gtk appmenu-gtk3 appmenu-qt
```

Log out, log back in, and see what you get. (This will break Unity, but I'm assuming that's not a problem.)

Edit: Oh, and turn the Nautilus desktop back on, of course.

---

### Post by gardengxc on 2012-02-17
That seems to have fixed it.

Yup everything seems to be working now, Thanks.

---

### Post by Copper Bezel on 2012-02-17
Sweet. = ) Be sure to mark the thread as Solved (Thread Tools at the upper right.)

---

### Post by gardengxc on 2012-02-17
Again thanks for the help that was bugging the hell out of me.

---

