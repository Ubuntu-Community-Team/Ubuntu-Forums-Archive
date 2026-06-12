---
title: "Edit applications menu in Xubuntu?"
date: 2007-04-22
forum: Desktop Environments
---

### Post by duelle on 2007-04-22
Just wondering how to add/remove things from it. I'm sure there's a file somewhere, just don't know what it's called.

---

### Post by RedSquirrel on 2007-04-22
I think it's safer to use the GUI. Destop Preferences -> Behavior tab. Click on "Edit menu".

The files seem to be in ~/.config/xfce4/desktop/.

---

### Post by duelle on 2007-04-24
Actually, I was wondering how to remove an entry from the "system" menu in there, but using edit on it won't do anything. I just want to get rid of an entry made by a windows program I installed with WINE that made a new tree called "Other", if that's any help.

---

### Post by Toshibi on 2007-04-29
I'm wondering the same thing. I have no idea where to find this file.

---

### Post by mrazster on 2007-04-29
This might be of a little help...if you play around with it a little.

[http://forum.xfce.org/index.php?topic=2658.0](http://forum.xfce.org/index.php?topic=2658.0)

---

### Post by Jerinaw on 2007-09-26
> **duelle said:**
> Actually, I was wondering how to remove an entry from the "system" menu in there, but using edit on it won't do anything. I just want to get rid of an entry made by a windows program I installed with WINE that made a new tree called "Other", if that's any help.

I'm having the same problem. I installed wine and it edited my Applications menu. I want to move somethings that wine added to another submenu. Anyway 'Menu editor' wont edit the system menu that gets included. I think i found the menu file that gets included 

**/usr/share/app-install/desktop/applications.menu**

and if you look in you ~/ dir for .desktop i think they are the links that you click to run something (it's like 1am here and i don't feel like reading up on how the menus are created so bear with me :-P )

Lol i dont know where i'm going with this...anyway i just want to edit the applications menu. Is there a way to use the 'Edit Menu' application to edit that systems menu?

btw i tried opening the applicatoins.menu with the Edit Menu program and i just got a blank window.

---

### Post by Shinoda on 2007-11-03
> **mrazster said:**
> This might be of a little help...if you play around with it a little.

[http://forum.xfce.org/index.php?topic=2658.0](http://forum.xfce.org/index.php?topic=2658.0)
[FONT=Courier New]NoDisplay=true[/FONT] doesn't seem to work for me, whereas [FONT=Courier New]Hidden=true[/FONT] does. Thanks for the link anyway.

Edit: Turns out both options work. I only had to make a change to the folder like creating or (re)moving a file so the menu would update (not even a reboot did it).

---

### Post by mistervinnie on 2008-03-03
If you're having trouble with wine, check out this dir 

/home/vincent/.local/...

I removed some files someware in this folder (lets say all of them, but i don't think that was really necessary :) )

Anyway, my "Others" menu is completely gone now.

(ps: it could be just me, but i spend 3 hours to get this job done)

---

### Post by thornomad on 2008-05-21
> **Shinoda said:**
> Edit: Turns out both options work. I only had to make a change to the folder like creating or (re)moving a file so the menu would update (not even a reboot did it).

Wow!  You are right - I struggled with this for a long time and it wasn't till I read this little gem that I changed the name of the .desktop file in question and then: it worked!

Prior to that it was just a frustrating sequence of restarts.  Now I only have to logout to get it to work (and change the name of the file).

D

---

