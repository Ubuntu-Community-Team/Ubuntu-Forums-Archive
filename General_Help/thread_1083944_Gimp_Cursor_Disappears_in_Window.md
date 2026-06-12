---
title: "Gimp Cursor Disappears in Window"
date: 2009-03-01
forum: General Help
---

### Post by Barry Kirk on 2009-03-01
I'm having a really wierd problem with Gimp.

Whenever I move my cursor inside the drawing window, as soon as it clears the guides, it disappears.  I'm unable to to draw or make any changes to the image that is displayed.

My setup is as follows.

I'm using Ibex build
Processor is an older intel x32 laptop at 2.0 GhZ

I tried completely uninstalling Gimp and reinstalling it but that doesn't seem to work.

I'm using Gimp 2.6

---

### Post by Barry Kirk on 2009-03-06
I fixed part of the problem.

I used Edit/Preferences/Theme Reset to factory defaults.

Now my cursor doesn't dissapear over the window, but I still can't draw anything.

Also, the mouse cursor appears to have a shape that indicates that it isn't able to do anything.

I've just got one layer  ( background ) and it's visible and unlocked.

I've got All selected.

---

### Post by Barry Kirk on 2009-03-06
One more thing.  At a point in the past I had installed gimpshop.  I think I've got it completely uninstalled, but how do I know for sure.

When I re-install gimpshop, I can select things and draw, but a lot of my filters are missing like red-eye removal.

---

### Post by unutbu on 2009-03-06
The fact that you can somewhat fix the problem by selecting Edit>Pref>Theme>Default suggests that maybe the problem is limited to your personal configuration. 

All personal gimp configuration settings are stored in a directory called .gimp-X.Y  where X and Y are version numbers. For example, Ubuntu 8.10 ships with gimp 2.6, and the configuration directory is called .gimp-2.6. 

So perhaps try this:
[list]
[*]Quit gimp
[*]Open up your file browser and rename the .gimp-2.6 directory to something like .gimp-2.6_old.
[*]Restart gimp. Gimp will notice there is no .gimp-2.6 directory and will create a new one. This will reset all your personal preferences to factory defaults.
[/list]

If you use nautilus (the default Ubuntu file browser), then you may have to press Ctrl-h to see the .gimp-2.6 directory. (Files and directories that begin with a dot are hidden by default).

---

### Post by Barry Kirk on 2009-03-06
OK,

Newbie question here.

Where is the gimp-2.6 directory?

---

### Post by unutbu on 2009-03-06
The .gimp-2.6 directory is in your home directory. (Go to Places>Home Folder). Then press Ctrl-h so you can see files and directories that begin with a dot. Note that the directory is called   

.gimp-2.6

(with a dot in front) not 

gimp-2.6

---

### Post by Barry Kirk on 2009-05-17
unutbu,

Thank you for the information... That seemed to work.



Sorry it took so long to get around to checking this one, but got distracted by other issues.

---

