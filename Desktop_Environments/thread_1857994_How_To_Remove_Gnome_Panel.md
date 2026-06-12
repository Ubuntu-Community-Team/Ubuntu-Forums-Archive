---
title: "How To Remove Gnome Panel"
date: 2011-10-11
forum: Desktop Environments
---

### Post by cwhittier on 2011-10-11
I know this has been asked a million times, but I have 2 special requirements that I have not seen a solution for anywhere.

I need to hide or remove all gnome panels completely.
I need gnome-panel to remain running.

I know I can delete one panel, but not both.
I know I can set the autohide property, with a large delay, but with this the bar is still accessible, which I can't have.

Any thoughts?

---

### Post by Frogs Hair on 2011-10-12
The command below will work , but you may want to have  a replacement for the panel such as Awn installed first .```
sudo chmod -x /usr/bin/gnome-panel
```

---

### Post by cwhittier on 2011-10-12
That command will remove gnome-panel's executable permissions, which means it will not launch.

I need gnome-panel to be running, just hidden. If I wanted to stop it from running, I could just remove it from the required components list of gnome desktop.

---

### Post by Copper Bezel on 2011-10-12
What exactly do you need it to do while it's hidden? You can use compizconfig-settings-manager to make it a "widget" in the "Widget Layer" plugin, matching class=Gnome-panel, which will keep it out of sight, but any dialogs it produces (like Alt+F2) will be stuck on the widget layer as well.

---

### Post by cwhittier on 2011-10-13
I was trying to leave this information out, because I didn't want people reading the post to try and solve this problem instead. Basically, this question was asked to see if there was a possible workaround to another problem.

I have a GTK application that I wrote myself, which is meant to be used in a kiosk type environment. This means I need to remove all user access to the OS. The trouble is, when I remove gnome-panel from startup.. anytime a popup window is created (dialogs, combo boxes), the widget below it (which is pretty much the entire screen) flashes gray for about a second, like it's redrawing incredibly slow. Turn gnome-panel on, and it's fine. off it's not. I know gnome-panel should have nothing to do with how my application is drawn, but one way or another, it's directly affecting it. I have another post about that issue, however a workaround for me, would be to find a way to keep gnome-panel running, but hidden, so whatever accidental effect it's having on my app, will continue to happen.

The compiz thing sounds like it's worth trying. I'll look into that.

---

### Post by Larkspur on 2011-10-13
Copper Bezel's method is probably best since it gets rid of the Alt+F2 dialog, which would make your kiosk easy to escape for experienced users. Also, be sure to disable to keyboard shortcut for the widget layer, or make a custom one.

---

### Post by cwhittier on 2011-10-13
Thanks for the suggestion. I've disabled all shortcut keys, so that wouldn't be an issue. The device this is used for is running 9.04, which doesn't have ccsm readily available.. So I haven't had a chance to try this yet, as I'll have to download the packages and integrate them into a firmware upgrade package.

I will post back with my results.

---

### Post by Larkspur on 2011-10-13
Before you go to the trouble of downloading ccsm (unless you already have), you could try this: 

1) Open gconf-editor and Keyboard Shortcuts
2) Remove all the applets from the panel 
3) In gconf-editor, go to /apps/panel/global/ and tick the box next to "locked_down"
4) In Keyboard Shortcuts, delete the values for "Run Application" and "Main Menu"

If it works, the panel is still visible, but you can't add applets or launch anything.

---

### Post by cwhittier on 2011-10-13
I know I'm making this really difficult, but I can't do that either. Well.. that's not entirely true.

The software runs on a dedicated system, and I need to retain the ability to revert the OS back to it's previous state in the event that the user downgrades to a previous version of firmware. 

Currently, I can accomplish this by just turning gnome-panel back on.. We had the top panel customized to be in a semi-locked state previously, with custom launchers.. If I were to make changes to the top bar in my "lockout" script, I would have to have a way to put it back.. Which is doable, but difficult, since it involves generating desktop files from a script, and making many modifications via gconf-tool, etc. This is an option, but not an easy one. I wish I knew why the lack of gnome-panel is causing an issue in the first place.

---

### Post by cwhittier on 2011-10-20
Sorry for the delayed response, some other stuff came up that took priority. This method did not work. I don't really know what to do at this point. I still don't understand the correlation between gtk redrawing and gnome-panel running. It makes no sense, and nobody else seems to have heard of this issue.

---

