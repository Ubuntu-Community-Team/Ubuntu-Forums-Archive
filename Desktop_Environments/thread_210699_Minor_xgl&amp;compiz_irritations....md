---
title: "Minor xgl&amp;compiz irritations..."
date: 2006-07-07
forum: Desktop Environments
---

### Post by Lunar_Lamp on 2006-07-07
I am just wondering if anyone knows how to fix teh following minor irritations:

 - XGL & Compiz installed, and now I don't know how to set up a shortcut so that ctrl+shift+t opens a new gnome-terminal

 - Kopete IM windows keep flashing in the task-bar, even after I have read the new messages recieved

 - Now using XGL&Compiz, keyboard has changed to US as opposed to UK

 - Another XGL/Compiz one: "Arrange and view all windows = Moving the pointer to the top right screen corner turns on or off; clicking a window will zoom it to the front".  Well, moving my pointer to the top right of te screen doesn't do anything, so I am clearly missing something, or this quote is a lie.

 - When I right click on a window and send it to a new viewport it doesn't go there, I think this is because gnome detects the window as all one desktop.  How do I sort this out, as I used workspaces heavily to keep organised?

 - In thunderbird, when I go to click on the drop-down menu next to 'get-mail' to select which accounts to get mail from, the option has vanished, and it works just as if I was clicking 'get-mail'.

---

### Post by Lunar_Lamp on 2006-07-07
It appears that the thunderbird one is now fixed after restarting x.

---

### Post by Rashid584 on 2006-09-23
[quote=lunar_lamp]- Kopete IM windows keep flashing in the task-bar, even after I have read the new messages recieved[/quote]

Argh. I've got this problem...its annoying me a lot :(

Anyone know a fix?

-Rashid

---

### Post by gumbald on 2006-09-23
> **Lunar_Lamp said:**
> 
 - Now using XGL&Compiz, keyboard has changed to US as opposed to UK

You can just change this in Keyboard preferences. Also make sure you've selected 104- or 105-key layout to ensure that all the shortcuts work.

If your keyboard keeps defaulting to US when you reboot, you can add a line to your "thefuture" script to change the layout. Unfortunately I'm not on my Ubuntu machine at the moment and can't find the site I used, but if someone else can point out the right command to change the keyboard layout from the command line, that's all that's needed I believe...

---

### Post by SimonJW on 2006-09-24
I can help with the US/UK keyboard issue. Most sites advise you to run **xmodmap** but I don't think this works very well. I use:
```
setxkbmap -model pc105 -layout gb -variant basic
```
where the **gb** is for Great Britain, and so should be correct for you as well.

Also to set a keyboard shortcut to run a program, Compiz can do this itself. You need to run **csm** (for Quinn's compiz) or **gconf-editor** then apps->compiz (for vanilla Ubuntu Compiz) and then using the "command" and "run command" entry's you can set "gnome-terminal" and "ctrl-shift-t".

I would also appreciate a solution to the Kopete issue :)

The Top-Right situation can also be fixed in csm/gconf-editor by changing the screen corners setting under the Scale plugin.

---

