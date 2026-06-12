---
title: "Why do installed programs go all over the place?"
date: 2009-04-18
forum: General Help
---

### Post by linuxtorvalds on 2009-04-18
This is both a general complaint and a specific request:

How can you tell what menu if any synaptic will install to:  
I've seen them show up in
Applications --> submenus
System -->  Preferences
System -->  Administration
no menu, have to open up a terminal to run it, often even if it has a GUI
Is there a solution?  I'm tired of checking every item in all menus to see if a new item (which may have a name that doesn't match it's name in Synaptic).

Specific:
I used synaptic to install "bootchart" and it isn't anywhere.  No man bootchart, and 
Places --> Search for files --> search for file bootchart --> look in filesystem doesn't find it.

Synaptic shows it installed, and it is a canonical supported app.

I don't actually need bootchart, but this has been bugging me a long time.

---

### Post by lovinglinux on 2009-04-18
Some menus only appear after reboot. I don't know why. The location of the menu depends on the application category, they are organized by function.

I don't think bootchart has a GUI, but I could be wrong. All you have to do is install it. Next time you boot, a report image will be automatically saved into* /var/log/bootchart* folder.

EDIT: you can also copy, move and create menus at "Applications >>> Preferences >> Main Menu"

---

### Post by joeyknuccione on 2009-04-18
> **linuxtorvalds said:**
> This is both a general complaint and a specific request:

How can you tell what menu if any synaptic will install to:  
I've seen them show up in
Applications --> submenus
System -->  Preferences
System -->  Administration
no menu, have to open up a terminal to run it, often even if it has a GUI
Is there a solution?  I'm tired of checking every item in all menus to see if a new item (which may have a name that doesn't match it's name in Synaptic).

Specific:
I used synaptic to install "bootchart" and it isn't anywhere.  No man bootchart, and 
Places --> Search for files --> search for file bootchart --> look in filesystem doesn't find it.

Synaptic shows it installed, and it is a canonical supported app.

I don't actually need bootchart, but this has been bugging me a long time.

In synaptic, right click the file, then properties, then under that look for installed files. Use this listing to find the files used. Not perfect maybe, but it works when you cant figure out what starts an app.

---

### Post by oldos2er on 2009-04-18
Bootchart is a daemon that runs on startup. See [http://www.bootchart.org/docs.html](http://www.bootchart.org/docs.html)

---

### Post by linuxtorvalds on 2009-04-18
Lovinglinux:  I did look, there was a /var/log/bootstrap with nothing in it.  Rebooted and got a very nice .png of the boot process.  It tripped me up because there was no executable and no man page (*everything* should have a man page).

joeyk:  Thanks, that's a tip that should be shouted from the rooftops.  I never tried it before.  I've been having this problem since I started with dapper.

0lddo2er:  Thanks, I'll take a look.

---

