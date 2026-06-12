---
title: "Gnome Workspace switcher"
date: 2006-01-08
forum: Desktop Environments
---

### Post by jrei on 2006-01-08
Hi there,

switching the desktop with keycodes, shows a Workspace Switcher in the middle of the screen. Nevertheless you can't click on the workspaces to change it, its just an overview of the workspaces. I'd like to have something simmilar but for workspace switching so I can jump directly to the workspace I want to go to.

I don't want to integrate the workspace switcher into my normal panel, since I use 10 desktops using 5 columns and 2 rows. 
I currently have a panel at the bottom of the screen, which unhides on mouse over, which contains the switcher. 

I think it would be very helpfull to open a quite large Workspace Switcher in the middle of the screen, or better at a customizable place, using a keyboard shortcut, mouseclick on a system tray symbol and/or mouseover the normal workspace switcher.

If there allready is such a thing let me know, and if not someone with time and knowledge about the gnome workspace switcher might think about including the functionality. :)

Greetings, Jörn

---

### Post by jimbz on 2006-01-08
Have you tried Ctrl-Alt-Left/Right/Up/Down Arrows?

Hope it can help

Jim

---

### Post by jrei on 2006-01-08
Thanks, but that was what I was talking about in the beginning. ;) 

But I would prefer to to get an overview of all worspaces on a keystroke, and then choose the workspace I want to go to. Acutally I could use the "jump to workspace" shortcuts but I would like to have some more visual overview, because I am not allways sure on which workspace I started my application and I don't want to accidentally go to a workspace where Openoffice or some IDE is running. Shure it's not killing me, I just thought that it would be nice to get some visual feedback befor choosing a workspace. You might think of it like the apple expose, but more structured, since you have more workspaces on which you applikations run. 

A problem with the worspace switcher which is integrated to a gnome-panel is that the panel has a maximum hight of 120 pixel. To get a good overview of your desktops you can't use more than two rows. I realy like worspaces to organise my work and I would like to try a 4x4 matrix of workspaces but for such an amount of workspaces I need some kind of overview where I can see which applications are running on the different workspaces.

Greetings, J&#246;rn

---

### Post by 23meg on 2006-01-08
Try skippy, which is in the repositories.

---

### Post by jrei on 2006-01-08
[QUOTE=23meg]Try skippy, which is in the repositories.[/QUOTE]

Thanks, very fancy thing. But It will only help organize the windows on a single workspace but I'd like to organize my workspaces. :) 

Actualy I am not a big fan of expose style organization, since it shuffles my windows and having plenty of gnome-terminals running it doesn't help very much showing them in small. :) 

What I am thinking of is like taking a step back from your workspace to see them all and then choosing which one I want.

I think an unhiding gnome-workspace-switcher in the middle of the screen with maybe a customizable size would do a realy good job to get an overview.

For a more funky solution something like 3DDesktop could be imagined, zooming out of the current workspace to see the complete matrix of all worspaces. 

But I realy think the gnome-workspace-switcher would do the job. :) Especialy because I don't want to wait on that overview since I want to improve the worspace handling and not wait for the helper application. ^^

Greetings, Jörn

---

### Post by ranf on 2006-01-09
If your mouse has a scroll wheel, you can use it when the mouse pointer is over the workspace switcher on the lower panel (in Gnome).

---

### Post by jrei on 2006-01-10
[QUOTE=ranf]If your mouse has a scroll wheel, you can use it when the mouse pointer is over the workspace switcher on the lower panel (in Gnome).[/QUOTE]

Thanks for the info but that wouldn't help me to get an overview. A problem crossing all worspaces is that it leads to a lot of memory swapping. I would like to avoid that. Using gnome, firefox, evolution, gimp, emacs, multiple gnome-terminals, openoffice, anjuta and netbeans eats up allot of memory and it realy helps if you don't switch to the workspace where netbeans is running. ;) Allthough I will get a nice coffee break. :)

---

### Post by brohan on 2006-01-10
In System > Preferences > Keyboard Shortcuts there are options to 'move window to workspace x'. Just setup the keyboard shortcut there.

Edit: Doh, Didn't throughly read the first question, though this could be of some help nevertheless.

---

### Post by jrei on 2006-01-14
Hi again,

I just found out, that the size of the gnome panel can be ajusted above 120 within the configuration manager. I set the panel size to 500. The panel just contains the workspaceswitcher and automaticly hides. I placed it in the upper left corner with orientation "left". I also set the animation speed to "fast" since the panel is quite large ^^.

I think the position is quite good, since i get an overview of the workspaces, I can choose a workspace and then use the application menu form the normal top panel to start an application.

It currently solves my problem. I have a 4x3 matrix of workspaces and still can see the application icons in the workspace switcher. ^^ *cheers*

Greetings, Jörn

PS: On my search I found the application "brightside" which enables action for workspace corners. Very nice tool. Just "apt-get install brightside". If you like working with the mouse you should take a look at it.

---

### Post by pt123 on 2007-03-24
Thanks this thread is very useful when Beryl  crashes

---

