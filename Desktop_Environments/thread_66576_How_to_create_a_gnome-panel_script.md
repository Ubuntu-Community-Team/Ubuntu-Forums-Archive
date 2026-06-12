---
title: "How to create a gnome-panel script?"
date: 2005-09-17
forum: Desktop Environments
---

### Post by Bluefire on 2005-09-17
I searched the forum and guide to no avail.  I'm a windows user learning ubuntu and love it so far.

That being said, I'm trying to figure out if there is a way to create a script file that I can access from the gnome panel.  Basically, I want to have it open a terminal, run a command, then launch a program.

I'm running WoW fine on it, but noticed that the change that you can make permanently to fix your mouse is slowing down my FPS.  The terminal command before launching WoW works great, but I don't know how to create a script to do this everytime without me inputting it.

Thanks!

---

### Post by elitegoodguy on 2005-09-17
Try this...

Make a text file using gedit or vi with the command that you type into the terminal. and save 

open up the terminal, type **chmod +x *filename*** Then just add to panel with the Application launcher and the filename is the application you want to launch

hope I am making sense

---

### Post by Bluefire on 2005-09-17
[QUOTE=elitegoodguy]Try this...

Make a text file using gedit or vi with the command that you type into the terminal. and save 

open up the terminal, type **chmod +x *filename*** Then just add to panel with the Application launcher and the filename is the application you want to launch

hope I am making sense[/QUOTE]
 Worked great, thanks!

---

