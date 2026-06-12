---
title: "Applications"
date: 2004-11-27
forum: Desktop Environments
---

### Post by peter_barb on 2004-11-27
How do I delete menu options from the "Applications" tab.

Yes I am a newbie.. first time <b>EVER</b> using Linux so don't laugh :p

---

### Post by jdong on 2004-11-27
hahahahaha (just kidding)!

This is actually not an obvious-answer question.


Open up a file browser, then go to File->Open Location..., then type in **applications:///**.

Manipulate the menu entries like any other files and folders.

---

### Post by peter_barb on 2004-11-28
Another few dumb questions..

1) Where is a file browser that comes with ubuntu?

2) How do I remove programs I do not use on ubuntu?

---

### Post by jdong on 2004-11-28
Nautilus is the built-in filebrowser. Right-click a folder, choose **Browse**.


Or, use ALT+F2 (Run Application), type in **nautilus**



Use **synaptic** (Computer->System Configuration) to add/remove programs.

---

### Post by peter_barb on 2004-11-28
Okay so once I checked the "Remove" button by right clicking is it fully removed from linux

---

### Post by Rancoras on 2004-11-28
[QUOTE=peter_barb]Okay so once I checked the "Remove" button by right clicking is it fully removed from linux[/QUOTE]

After you press the "Apply" button, the package will be removed.

---

### Post by clasqm on 2004-11-28
[QUOTE=jdong]

Open up a file browser, then go to File->Open Location..., then type in **applications:///**.

Manipulate the menu entries like any other files and folders.[/QUOTE]

Since all the original poster asked was to delete entries, why not just rightclick on the menu entry and select "Remove this Item"?

---

### Post by jdong on 2004-11-28
[QUOTE=clasqm]Since all the original poster asked was to delete entries, why not just rightclick on the menu entry and select "Remove this Item"?[/QUOTE]
 That works for this specific purpose, but in the future if he'd like to reorganize the menus even more, the right-click method becomes very inefficient.

---

### Post by peter_barb on 2004-11-28
w00t! Thanks guy. I noticed ubuntu is so much more different then windows. Do you guys know a good place to find linux drivers?

---

### Post by calvinpriest on 2004-11-28
Generally speaking, you don't need to install drivers in GNU/Linux.  Support for most hardware will be automatically added during installation. 

What device are you looking for drivers for?

---

### Post by peter_barb on 2004-11-28
I am looking for drivers for a Lexmark printer. The model is z615. Linux has some lexmark drivers already, just it doesn't have that particular one.

---

### Post by adbak on 2004-11-28
In that case, you need to do a few things.

First, open up Synaptic.  Click Settings on the menu bar, then click Repositories.  After that, a window should pop up with a bunch of website addresses and a cdrom entry.  These are the places that Synaptic culls programs from.

There should be some entries that don't have checkboxes next to them.  Click each box and a window should pop up asking if you want to add the Universe repository.  Click Okay, and make sure that all boxes are checked.  Click Okay and then click Reload.

Click on Search, type "cupsys-driver-gimpprint", and then click Okay.  Some results should pop up.  Right click on cupsys-driver-gimpprint and click Mark for Insallation.  It will ask if you want to install cupsys-driver-gimpprint-data as well.  Yes, you do.  Then you need to click Apply, wait for it to download and install.

After it's done downloading and installing you need to click Settings, then Repositories and now you need to uncheck the Universe repository sources.  Click Reload and then exit Synaptic.

We're almost done.

Next, click on Computer in the upper panel, click System Configuration, and then click on Printing.  Get rid of any previous printer configuration, if you have any, then click Add Printer.  Go through the steps to set up your Lexmark and your specific model should be there.

I believe that's all you need to do.  Good luck!

---

