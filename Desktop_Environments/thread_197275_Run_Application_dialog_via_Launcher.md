---
title: "Run Application dialog via Launcher?"
date: 2006-06-15
forum: Desktop Environments
---

### Post by dolson on 2006-06-15
How can I create a launcher for my desktop or Applications menu to start the Run Application dialog box?

I ask because I'm trying to help my friend who appears to hate keyboard combos, and he's mostly a Windows user, and would like it to be more similar to Windows.

Thanks in advance.

---

### Post by rai4shu2 on 2006-06-15
I think you can add a Run Application launcher to the panel, but I don't think you can create it anywhere else on the desktop.

---

### Post by Sutekh on 2006-06-15
Ai... keyboard combos are so superior to the mouse.  Even in Windows I favour the keyboard.

You should be able to add a launcher to your desktop using this 
```
gnome-panel-control --run-dialog
```
in the command section.

---

### Post by dolson on 2006-06-15
I understand and totally agree about the keyboard. And he does in some ways, but I also think he has a very valid point when he complains that there are only keyboard shortcuts for everything EXCEPT for copy and pasting.

Anyhow, so, gnome-panel-control. That is part of the openbox package? I am going to have a hard time explaining why he has to install a different window manager entirely to get functionality that should be a part of GNOME by default. Oh well.

Thanks for pointing that out, but I am not trying it on my system, I don't want to install another WM myself. I'll let him know though.

---

### Post by Sutekh on 2006-06-15
[quote=dolson]
Anyhow, so, gnome-panel-control. That is part of the openbox package? I am going to have a hard time explaining why he has to install a different window manager entirely to get functionality that should be a part of GNOME by default. Oh well.[/quote]Oh.  I forgot it was part of the Openbox package, scrap that idea.  
The command should be something easy, but I can't figure it out at the moment.  

There is also the [gmrun](http://packages.ubuntu.com/dapper/x11/gmrun) package from the universe repository, which doesn't require much in the way of dependancies.

I still want to know what the command is though...

---

