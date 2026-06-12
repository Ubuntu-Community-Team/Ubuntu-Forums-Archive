---
title: "issues with workspace switching"
date: 2005-12-17
forum: Desktop Environments
---

### Post by timczer on 2005-12-17
I searched for something similar but didn't find it.  I cannot get the workspace switching applet to work on the gnome panel.  I can use ctrl+alt+arrow to move between workspaces but not the switcher.  I tried using brightside, but it will not go past the edge of the screen to the next workspace. Can anyone tell me why this will not work?

---

### Post by Sutekh on 2005-12-21
What's happening with the switcher?  What happens when you click another workspace, or roll the scroll wheel (if you have one) over the switcher?

---

### Post by timczer on 2005-12-21
It will only show one workspace at a time.  If I hover over it, nothing happens.  The scroll wheel actually will change the workspace, so that is good to know.  If a right click on the switcher, and choose preferences, the top part is shadowed out and not accessable to me.  This is where I should be able to ask the switcher to show all my workspaces, but the "show current workspace" choice is marked and I can't change it because for some reason it is disabled for me.

---

### Post by Sutekh on 2005-12-21
[QUOTE=timczer]It will only show one workspace at a time.  If I hover over it, nothing happens.  The scroll wheel actually will change the workspace, so that is good to know.  If a right click on the switcher, and choose preferences, the top part is shadowed out and not accessable to me.  This is where I should be able to ask the switcher to show all my workspaces, but the "show current workspace" choice is marked and I can't change it because for some reason it is disabled for me.[/QUOTE]

Ok I get it.  Does the situation change if you remove and replace the switcher?

Open the Configuration Editor, and look for apps -> panel -> applets -> workspace_switcher_screen0 -> prefs

Then check the key; display_all_workspaces

---

### Post by Sutekh on 2005-12-21
Don't bother replacing the switcher, just enable that key in the Configuration Editor, I just checked what it will do.

---

### Post by timczer on 2005-12-22
Removing and reinstalling has not worked, done that a couple of times.  When I go to configuration editor, apps->panel->applets->, and from there they are just numbered applets, no names.  There are a couple of them that did not say to display all workspaces, I enable those.  Now the workplace switcher shows the 4 desktops I have enabled, the "show all workspaces" box is now checked, but is still shadowed and can't be switched from the preferences that come up from right clicking the applet.  Oh, well, it is working like I need it to, so I will take that.  Thanks for your help.

---

