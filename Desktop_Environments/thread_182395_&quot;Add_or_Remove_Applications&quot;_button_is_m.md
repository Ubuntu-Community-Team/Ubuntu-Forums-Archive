---
title: "&quot;Add or Remove Applications&quot; button is missing"
date: 2006-05-26
forum: Desktop Environments
---

### Post by thecgmguy on 2006-05-26
Greetings and salutations.

This is probably a real easy fix but as I'm new to Ubuntu (and Linux in general) I need some help. 

After a fresh install, I went into the Add/Remove Applications window, advanced mode and removed totem.  I also ran/installed the ubuntu updates.  Afterwards, the Add or Remove Applications button no longer appears.  How can I add this again? The properties for the menu bar didn't seem to have the option. 

Thanks in advance. 

CGM

---

### Post by Blairboy on 2006-05-26
I'm not really familiar with the tool you're talking about, but you can open up a terminal (applications->accessories->terminal) and type "sudo apt-get install totem" it'll get totem back for you if that's what you want.  Hope this helped.

---

### Post by aysiu on 2006-05-26
Right-click on the menu and select **edit menu**. Then add a new launcher with the command: ```
gksudo gnome-app-install
```

---

### Post by amohanty on 2006-05-26
Ok try this (its a work around, I am not quite sure how you can restore the menu item):

Applications->Accessories->Terminal
In there type:
**sudo gnome-app-install**
Enter your password
and the add/remove applications window will pop up.

HTH
AM

---

### Post by dmizer on 2006-05-26
you should be able to simply select it from the list as with a radio button 

right click on applications and select "edit menus" ... the menu editor will appear.  then click on "applications" (top of the list in the left hand pane) and scroll down to the bottom of the list on the right pane.  you should find "add applications" there.

---

### Post by thecgmguy on 2006-05-26
Hi!

Thanks everyone for the prompt feedback! It's greatly appreciated...

Unfortunately, didn't work. 

I added the button according had it run the following command: 
```
gksudo gnome-app-install
```

But when I try to run it, I get the following error in a popup dialog box:
[B]Failed to run gnome-app-install as user root:
 Child terminated with 1 status[/B]

I also get nothing when I open up the terminal and perform the following procedure:
--------------
Applications->Accessories->Terminal
In there type:
sudo gnome-app-install
Enter your password
and the add/remove applications window will pop up.
-------------

It will prompt me for my password and shortly afterwards it will return me to the prompt... no errors. 

Is there a way to confirm if the gnome installer app even exists on the system?

Thanks, 

CGM

---

### Post by aysiu on 2006-05-26
[QUOTE=thecgmguy]
Is there a way to confirm if the gnome installer app even exists on the system?[/QUOTE] Sure. ```
sudo aptitude update
sudo aptitude install gnome-app-install
``` If it's installed, you'll be told it's already the newest version.

---

### Post by thecgmguy on 2006-05-26
Thanks everyone (especially Aysiu).  It's working great after a reinstall of the gnome installer. 

Your patience and prompt feedback was greatly appreciated. 

The community support here is simply outstanding. 

-CGM

---

