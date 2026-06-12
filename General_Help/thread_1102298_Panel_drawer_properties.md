---
title: "Panel drawer properties"
date: 2009-03-21
forum: General Help
---

### Post by BightningLug on 2009-03-21
I've added a drawer to one of my panels to act like a QuickLaunch button. I was wondering if there is a way to alter the speed for opening and closing the drawer? There doesn't appear to be any way of changing it in the drawer properties window.

---

### Post by tmetzcc325 on 2009-04-28
Unfortunately, I am looking for something similar.  I don't like the delay before the drawer opens, and I am looking for a way to use a folder/directory as a toolbar on the panel, like how Windows allows you to pin toolbars to the taskbar.

If I find anything, I will follow up here.

---

### Post by drs305 on 2009-04-28
I looked into the gconf-editor settings and couldn't find a setting to set the drawer speeds. I even tried creating some new keys without success. 

I can offer some assistance to tmetzcc325, and maybe to the OP. Before drawers became available, I created my own drop-downs that I still use. Best of all, when I click on the panel icon it opens immediately. It may be more work than drawers, but it does open quickly.

1. Open the Main Menu for editing (Right click on the Main Menu icon, Edit Menu; or run "alacarte")

2. Create a new menu: Applications, New Menu. The new menu folder will now appear in the left pane.

3. Add at least one shortcut into the folder. Highlight the New Menu in the left pane, select "New Item" in the right pane and add the required info. Close when you are done.

4. Right click the upper panel, Add to Panel, Application Launcher, drag your New Menu to the panel and release.

5. When you click on this panel shortcut, it will instantaneously drop down.

6. To add additional apps, right click on the icon, Edit Menu, highlight the Menu in the left pane, "Add Item" in the right pane. I don't remember a way to drag new items into the folder so each item has to be added individually although it may be possible.

---

### Post by tmetzcc325 on 2009-04-28
That's not a bad idea, thank you.

After a bit of Googling, I found this package called file-browser-applet, which does almost exactly what you can do in Windows.  To use it, I created a folder in my home directly called shortcuts, then I put links to all the apps that I currently have in the drawer in that folder.

Then, after installing file-browser-applet (which can be found in the universe repo I believe), I added the applet to the panel, and added an entry in the applet preferences to point to this shortcut folder.  Then it pops up a list of that folder contents.

Here is the project page, but this can be installed via apt-get or synaptic:

[http://code.google.com/p/gnome-menu-file-browser-applet/](http://code.google.com/p/gnome-menu-file-browser-applet/)

Hope this helps everyone...seems like a good project - hopefully it gets rolled into main at some point and becomes standard.

---

