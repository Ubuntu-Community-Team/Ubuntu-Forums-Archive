---
title: "Gnome 3.2 background loading out of place, shifted down"
date: 2012-02-13
forum: Desktop Environments
---

### Post by kohoutek1 on 2012-02-13
Here's a bug that has just started happening in my Gnome 3.2 shell:

All backgrounds are loading out of place, shifted down. This leaves a white strip across the top the screen.

It's probably something I wouldn't notice except that I have a theme with a translucent panel. 

When the desktop loads, the background begins in the proper position, but then it shifts down when all components have loaded.

This was not happening until today, but now it occurs with every login. I have been using this desktop configuration for about a week now, with no other problems.

I've attached a screenshot so you can see what I'm talking about. Notice the white band across the top half of the panel.

Could this be a Mutter problem?

Extension conflicts?

What logs would I need to check to see the error?

---

### Post by kohoutek1 on 2012-02-13
I tried turning off all extensions and rebooting. No luck with that, but it probably does rule out extension conflicts.

---

### Post by kohoutek1 on 2012-02-14
It seems now to be an issue with Nautilus, or "Having the file manager handle the desktop."

When I turn off the file manager-->desktop setting in Advanced Settings, the space at the top goes away.

But with that setting off, I have no folders on the desktop.

Any ideas on how to correct the problem?

---

### Post by kohoutek1 on 2012-02-16
The desktop picture is being pushed down by a menu bar that is present when file manager handles the desktop, under the shell panel. If I install the Auto-hide Top Panel extension, I can see the menubar, with its menus.

I have ruled out Unity causing the problem. I am running Ubuntu 11.10 with pure Gnome 3.2.1, no Unity installed. At log-in, I get the options of Gnome, Classic Gnome, or Classic Gnome no effects.

As my x-window-manager, I'm running mutter, not metacity. Changing between them has no effect on the unwanted menubar.

Does anyone know how to turn off that menubar?

---

### Post by kohoutek1 on 2012-02-16
OK, I found the solution to the problem in another thread here on ubuntu forums, though that thread wasn't specifically related to this issue. The same issue had come up in the discussion though.

Here's a command to remove the menu bar: 
```
sudo apt-get autoremove appmenu-gtk appmenu-gtk3 appmenu-qt
```

This removal seems to have no adverse affects. The menu bar is gone, the desktop background is in the right place, and I can now have the file manager handle the desktop with my working folders.

I still don't know when or how I installed the components that made that menu bar suddenly appear, though...

---

