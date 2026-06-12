---
title: "[SOLVED] Desktop gone"
date: 2006-03-13
forum: Desktop Environments
---

### Post by Anonimoes on 2006-03-13
Tonight I played some with my startup scripts (.bashrc, .bash_profile and .xinitrc) while trying to get some programs launched automatically at GNOME startup. During this process I suddenly kind a 'lost' my desktop. Both the upper and lower panels are fine and I can still launch applications and stuff from the menus on de left of the upper panel bar. The thing is that there is no desktop background (only standard ubuntu brown) and no launchers. Clicking my right or left mousebutton on the desktop doesn't have any effect either. Also, when I connect a usb storage device I can just access it using a file browser but no icon appears on the desktop but it did do so before.

Of course I immediately changed all the startup scripts back to how the were before I changed them. I even compared them to the startup scripts of a friend of mine and the are exactly the same as his. Then I tried to start while the startup scripts were moved and that diddn't help as well. I also logged into the GNOME failsafe system instead of ordinary GNOME and in the failsafe the desktop was perfectly fine!

I just can't think of wat the problem may be now, do you guys have any ideas?

---

### Post by Sutekh on 2006-03-13
Try opening up the GNOME Configuration Editor (Applications -> System Tools Menu) and using the tabs on the left, open up **apps -> nautilus -> preferences** and look for the options **show_desktop**.  Is that box checked (ticked)?

---

### Post by Anonimoes on 2006-03-13
[QUOTE=Sutekh]Try opening up the GNOME Configuration Editor (Applications -> System Tools Menu) and using the tabs on the left, open up **apps -> nautilus -> preferences** and look for the options **show_desktop**.  Is that box checked (ticked)?[/QUOTE]

Yes, it is.

---

### Post by Sutekh on 2006-03-13
Well I'd say that somehow nautilus was removed from the startup.

Open a terminal and type
```
nautilus
```
with the terminal still open, fire up System -> Preferences -> Session.  

Select the Current Session tab, select nautilus and set the Order to 40.  

Set the Style to Restart and click Apply.

Close the terminal. Nautilus should exit and a new instance should start.

Close the Sessions window and log out, making sure to check the option to 'Save current setup'.

Log back in and you should have a fully functional desktop again.

---

### Post by Anonimoes on 2006-03-13
Okay, that worked out fine! Thanks a lot!

Do you maybe have any idea how/why this happened? (Can it have something to do with me changing the startup scripts?)

---

### Post by Sutekh on 2006-03-13
Excellent!  

Yes it must have been due to changing the startup scripts.  I think this is the location of them (which you probably already know) ~/.gnome2/session.

---

### Post by Anonimoes on 2006-03-13
[QUOTE=Sutekh]Excellent!  

Yes it must have been due to changing the startup scripts.  I think this is the location of them (which you probably already know) ~/.gnome2/session.[/QUOTE]

I think my interpretation of a startup script is different from yours (my interpretation being the wrong one probably). The scripts I meant are all in my homedir and are the files .xinitrc, .bashrc and .bash_profile. I didnt know about the script you are referring to. (now I think of it, .bashrc isn't a startup script at all, is it?)

---

### Post by Sutekh on 2006-03-13
AFAIK **~/.bashrc** is used when a bash shell is started.   **~/.xinitrc **is used when X is started.


**~/.gnome2/session** is [B]/home/<username>/.gnome2/session 
[/B]
(the **~/** is a shortcut for** /home/<username>**)

I'm pretty sure that's the startup script for GNOME.  I could be wrong though.


If you're interested in this sort of thing, you might find this link useful

[Ubuntu Wiki - Custom X Session]("https://wiki.ubuntu.com/CustomXSession")

---

### Post by Anonimoes on 2006-03-14
Thanks for elaborating things! I'm surely going to read that wiki page.

---

### Post by Sutekh on 2006-03-14
No problem.  I'm delving into that link too.

---

