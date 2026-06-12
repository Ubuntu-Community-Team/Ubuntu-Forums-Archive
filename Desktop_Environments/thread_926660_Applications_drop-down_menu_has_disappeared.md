---
title: "Applications drop-down menu has disappeared"
date: 2008-09-22
forum: Desktop Environments
---

### Post by frncz on 2008-09-22
Hello

Although the 'Applications' tab is still at there at the top left of my screen, there is no drop down menu under it anymore. Drop down lists for 'Places' and 'System' are fine.

How do I restore the drop down list, please

Thanks

Mike, 8.04

---

### Post by chongzivalve0809 on 2008-09-22
a professional [gate valve](http://www.valvesupplier.net/forged-steel-gate-valves.htm) China manufactuer and supplier,established in 1983The main product is:cast steel [gate valve](http://www.valvesupplier.net/forged-steel-gate-valves.htm),forged steel gate valve ,pressure seal gate valve,plate [gate valve](http://www.valvesupplier.net/forged-steel-gate-valves.htm).  BFV Valve also possess the test lab with various of examination equipment for material chemical composition analysis, physical property and non-destructive examinat-ions such as RT,UT,MT,PT .[gate valve](http://www.valvesupplier.net/forged-steel-gate-valves.htm) manufacturer website:[www.valvesupplier.net/forged-steel-gate-valves.htm](http://www.valvesupplier.net/forged-steel-gate-valves.htm)

---

### Post by blesbok on 2008-09-22
here's a possible short-term remedy

i'm using kde and am not at an ubuntu desktop right now, but do ALT-F1 and you should get the same result as clicking that menu

---

### Post by frncz on 2008-09-22
> **blesbok said:**
> here's a possible short-term remedy

i'm using kde and am not at an ubuntu desktop right now, but do ALT-F1 and you should get the same result as clicking that menu


Thanks

Alt-F1 just highlights the Applications' tab, but does not bring down the menu.

also, the 'Edit Menus' option I get with a right click does not do anything. It is not grayed out, but there is no response. And this is the case for the other tabs too! I can't edit menus

Cheers

Mike

---

### Post by frncz on 2008-09-22
> **frncz said:**
> Hello

Although the 'Applications' tab is still at there at the top left of my screen, there is no drop down menu under it anymore. Drop down lists for 'Places' and 'System' are fine.

How do I restore the drop down list, please

Thanks

Mike, 8.04

Problem solved: Clicking on 'Menu Editor' in 'file system' allowed me to click on all applications I wanted to see. I don't know how it all got unclicked!

---

### Post by Timpotten on 2008-12-31
Right click panel where the drop-down used to be
Ignore the top two options, and scroll down to Menu Bar and select it!

---

### Post by colbobs on 2009-01-01
Problems here too and these options unfortunately do not help.
Thanks for the advice though.

I've found some other potential solutions on the forum with no success again I'm afraid.
Search for applications menu and a couple of threads with a similar title to this one are there.

---

### Post by Timpotten on 2009-01-02
I am having some problems too. Took a look at the hidden file /home/username/.config/panel/applications.menu  (in the file browser, you need to click view and tick 'show hidden files)

There were several files called something like applications.menu-undo.22 These can be renamed by deleting the undo.XX part. This seemed to work, but the Places and System menus were incomplete

I then created a new user and gave permission for the new user to write to one of my folders. 

When you log-on as the new user, there is no such file as .config/panel/applications.menu until you edit the menu bar (by adding an application) I checked to make sure all the drop-downs were still there. 

I saved a copy of this new file somewhere easy to find and accessible to both users (e.g. Desktop). and even remembered to right click the file name and set the permission so that when I logged-on as myself, I could read it.

I tried both copy/ replace the old file and used gedit to compare and 'hand craft' the contents. Now the Places and Applications are complete, but the system preferences and settings is still absent. 

If you give permission to others to use your home directory, the system does not load .dmrc as a security measure. so I reset permissions to user only and re-booted, but The right click 'edit menus' is still not working - any ideas?

---

### Post by Timpotten on 2009-01-02
from: [http://linux.about.com/od/ubuntu_doc/a/ubudg10t2.htm](http://linux.about.com/od/ubuntu_doc/a/ubudg10t2.htm)

Ubuntu comes with the Alacarte Menu Editor, so you can customize your menus and add entries for applications that don't automatically appear after they are installed.

To add a new menu entry (it says) Open Alacarte with Applications->Accessories->Alacarte Menu Editor (which is not present on mine) or by right-clicking on any top-level menu and choosing Edit Menus (this used to work, but now does not). so I tried to run it in Konsole but it reported "inconsistent use of tabs and spaces in indentation"

---

### Post by francoise_peace on 2009-12-06
Same problem: Edit Menus doesn't respond and Alacarte doesn't launch from launcher alacarte's icon.
[http://forum.ubuntu-fr.org/viewtopic.php?pid=3119773](http://forum.ubuntu-fr.org/viewtopic.php?pid=3119773)

A Karmic bug ?

---

### Post by tiggsy on 2010-01-30
Not a karmic bug. This computer is running Hardy and has similar problems. Selecting Edit menus from the right click menu has no effect, and clicking on Applications produces a very tiny cream block to the far left and underneath the ubuntu logo in the top panel.

I can't find the file /home/username/.config/panel/applications.menu but there is /home/username/.config/menus/applications.menu - which on my machine is empty.

---

### Post by tiggsy on 2010-01-31
Found the fix here from hangar_18 : [http://ubuntuforums.org/showthread.php?t=258832]("http://ubuntuforums.org/showthread.php?t=258832")

---

### Post by Alex Fuchs on 2011-02-08
> **Timpotten said:**
> I am having some problems too. Took a look at the hidden file /home/username/.config/panel/applications.menu  (in the file browser, you need to click view and tick 'show hidden files)

There were several files called something like applications.menu-undo.22 These can be renamed by deleting the undo.XX part. This seemed to work, but the Places and System menus were incomplete

I then created a new user and gave permission for the new user to write to one of my folders. 

When you log-on as the new user, there is no such file as .config/panel/applications.menu until you edit the menu bar (by adding an application) I checked to make sure all the drop-downs were still there. 

I saved a copy of this new file somewhere easy to find and accessible to both users (e.g. Desktop). and even remembered to right click the file name and set the permission so that when I logged-on as myself, I could read it.

I tried both copy/ replace the old file and used gedit to compare and 'hand craft' the contents. Now the Places and Applications are complete, but the system preferences and settings is still absent. 

If you give permission to others to use your home directory, the system does not load .dmrc as a security measure. so I reset permissions to user only and re-booted, but The right click 'edit menus' is still not working - any ideas?
I edited the applications.menu to remove some deleted wine programs and the whole applications menu disappeared!
So I had a look in the last applications.menu.undo- and there where those deleted entries.
I opened Nautilus in  ~/.config/menus (as user) dragged the *.undo file to the Desktop, renamed it and put it back to replace the file applications.menu and all the entries where restored.

---

