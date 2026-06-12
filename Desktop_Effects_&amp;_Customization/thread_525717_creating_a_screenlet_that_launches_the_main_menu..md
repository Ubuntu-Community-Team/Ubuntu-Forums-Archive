---
title: "creating a screenlet that launches the main menu."
date: 2007-08-14
forum: Desktop Effects &amp; Customization
---

### Post by xl_cheese on 2007-08-14
I've been trying to figure out how to do this.  I've got a method that works now, but it has shortcomings.

I'd like to be able to place the screenlet on top of the panel, but I cannot figure out how.  For now you have to create a launcher on the gnome panel that has the top and bottom clipped.  You then place a screenlet with the same icon behind the one on the panel to make it complete.

You also have to have a menu launcher on the panel or the menu will freeze in the open position.

Here's how I was able to make the screenlet launch the main menu.

1. install openbox

```
sudo apt-get install openbox
```

This command opens the menu
```
gnome-panel-control --main-menu
```


I then created an executable file with this inside.
```
#!/bin/bash
gnome-panel-control --main-menu &
gnome-panel-control --main-menu &
gnome-panel-control --main-menu &
gnome-panel-control --main-menu &
gnome-panel-control --main-menu &
gnome-panel-control --main-menu &
gnome-panel-control --main-menu &
gnome-panel-control --main-menu &
gnome-panel-control --main-menu && gnome-panel-control --main-menu &
gnome-panel-control --main-menu &
gnome-panel-control --main-menu &
gnome-panel-control --main-menu &
gnome-panel-control --main-menu && gnome-panel-control --main-menu &

```


The reason for the repetition is because the screenlet would only launch the menu with that command after clicking several times in a row.  It was hokey. 

Using the generic launcher screenlet set the command to this file and you are done.

You can then hack the launcher screenlet icon to what ever you want.

You'll also need to set the main menu launcher on the panel to the same icon using gconf-edit


Maybe some others here can come up with better methods?

---

### Post by Hugolp on 2007-08-14
Hi

I know its a bit offtopic but Id like to know if you know how to make all the bars go away? both top and low bars and just have the Wallpaper?

Thanks

Hugo

---

### Post by urukrama on 2007-08-15
Right click on the panel > Delete panel.

Alternatively, you can set them to autohide (Right Click > Preferences > Autohide).

If you don't want the gnome-panel to load on startup, you'll have to remove it from your session (System > Preferences > Sessions)

---

### Post by urukrama on 2007-08-15
> **xl_cheese said:**
> I've been trying to figure out how to do this.  I've got a method that works now, but it has shortcomings.

I'm sorry, but I don't quite get what you want to achieve. Why don't you just use the Main Menu button (Right Click > Add to panel, and click main menu)? Doesn't that achieve the same? Or am I missing something?

---

### Post by xl_cheese on 2007-08-15
> **urukrama said:**
> I'm sorry, but I don't quite get what you want to achieve. Why don't you just use the Main Menu button (Right Click > Add to panel, and click main menu)? Doesn't that achieve the same? Or am I missing something?

eye candy.  Something larger than the normal main menu launcher.

If the screenlet can be made to work without relying on the gnome panel it would be possible to completely do away with the panel.  ie use kiba-dock or awn to hold the open apps in the center and then have  a few screenlets for other things.

---

### Post by Hugolp on 2007-08-17
> **urukrama said:**
> Right click on the panel > Delete panel.

Alternatively, you can set them to autohide (Right Click > Preferences > Autohide).

If you don't want the gnome-panel to load on startup, you'll have to remove it from your session (System > Preferences > Sessions)


Try to do that when theres only one panel left. You wont be able to delete it. And yes I know about autohide, but I want to remove it.

And I do want gnome-panel to load so I can have the menus. I just want the bars gone.

Hugo

---

### Post by H_out on 2007-08-17
> **Hugolp said:**
> Try to do that when theres only one panel left. You wont be able to delete it. And yes I know about autohide, but I want to remove it.

And I do want gnome-panel to load so I can have the menus. I just want the bars gone.

Hugo

I've been trying to do the same thing, but the closest I can get is to get it down to one panel on the bottom, going into the panel properties and disabling "Expand", then dragging it all the way to a corner.

I've attached a screen shot of what I mean.

To make it as minimalistic as possible, you could remove all the features of the panel and make the background color transparent...ugly hack.

---

### Post by Rupertronco on 2007-08-18
I've done the same exact thing, i wish i could ditch this method.

---

### Post by H_out on 2007-08-18
Sorry to the thread starter for the off-topic posts, hopefully this will be the last one.

I've found a nicer solution to hiding the panels here:
[http://ubuntuforums.org/showthread.php?t=230300](http://ubuntuforums.org/showthread.php?t=230300)


**Back to topic:**
Have you tried something other than a screenlet?  From what I can tell, they're still pretty new.

Perhaps xfce4-panels might be able to execute the main menu launch, they're pretty customizable.  It should be available in the Ubuntu repository.

If I understand what you're trying to do, it seems like you could try this workaround:
-create a transparent panel with the main menu button
-lay it over a screenlet that doesn't have any functionality
-when you click the screenlet, you're actually clicking the panel, which opens the menu

---

### Post by urukrama on 2007-08-19
What about pressing ALT+F1 to show the main menu? OR xfce4's desktop right-click menu?

---

