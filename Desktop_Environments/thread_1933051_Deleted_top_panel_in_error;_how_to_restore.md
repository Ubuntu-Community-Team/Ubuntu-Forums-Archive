---
title: "Deleted top panel in error; how to restore?"
date: 2012-02-28
forum: Desktop Environments
---

### Post by XEtedBear on 2012-02-28
I'm running Gnome 3 desktop on 11.10. Today the automatic update changed LibreOffice to Version 3.5 and changed 2 launch icons (for Writer and Calc) in my top panel to 'No Entry' signs. In trying to delete these I Alt-RightClicked the panel and chose the delete option, because the icon exactly matched what I was seeing.

No surprisingly, I now no longer have a top panel. I've got some ammo. left over; should I shoot myself in the other foot too? Or can I recover the top panel?

AAARrrgghh! I just realised that if I logoff, I will not be able to do anything on this desktop again, as I have no way of starting any applications now - I was just lucky to have a browser running at the time.

---

### Post by Andrew_P on 2012-02-28
> **XEtedBear said:**
> I'm running Gnome 3 desktop on 11.10. Today the automatic update changed LibreOffice to Version 3.5 and changed 2 launch icons (for Writer and Calc) in my top panel to 'No Entry' signs. In trying to delete these I Alt-RightClicked the panel and chose the delete option, because the icon exactly matched what I was seeing.

No surprisingly, I now no longer have a top panel. I've got some ammo. left over; should I shoot myself in the other foot too? Or can I recover the top panel?

AAARrrgghh! I just realised that if I logoff, I will not be able to do anything on this desktop again, as I have no way of starting any applications now - I was just lucky to have a browser running at the time.

Try right-clicking on the bottom panel (if you still have one), then select "New panel" to create a new top panel.  You'll have to repopulate it yourself, by right-clicking on it and adding applets.  The panel may actually be created on the left or right side of the screen, but that's OK, because you can drag it to the top later.  That's my best guess, since I'm using an older version of Ubuntu with GNOME 2.  Any chance that the top panel ended up in Trash?

The Power Button on Lucid Lynx 10.04 is handled by "Indicator Applet Session".  That gives basic power down/restart capability.  Next, add the "Main Menu" applet.  That will give access to your programs again.  Once you have that capability restored on your machine, you should be able to safely power down as needed while you research a complete solution.

---

### Post by XEtedBear on 2012-02-29
Thanks; got it. 

I've got myself a new top panel now, with a few things on it but can't find how to get the launchers for 'Applications' or 'Places'. I've found the one called 'Main Menu' for the main Gnome menu bar - which includes 'Applications' and 'Places', but that means I have to click more icons now. Can I get to these two items more directly?

---

### Post by Andrew_P on 2012-03-01
> **XEtedBear said:**
> Thanks; got it. 

I've got myself a new top panel now, with a few things on it but can't find how to get the launchers for 'Applications' or 'Places'. I've found the one called 'Main Menu' for the main Gnome menu bar - which includes 'Applications' and 'Places', but that means I have to click more icons now. Can I get to these two items more directly?

By right-clicking on the various items I find on my top panel and selecting "About" from the context menu that pops up, I see the following applets on my GNOME 2 panel, from left to right:

[LIST]
[*]Main Menu (the GNOME Main Menu; includes "Applications", "Places" and "System")
[*]The Help launcher (name=Help / command=yelp / comment=Get help with Ubuntu)
[*]My customized SeaMonkey browser launchers (Ubuntu uses Firefox by default, i.e, name=Firefox Web Browser / command=firefox %u / comment=Browse the World Wide Web)
[*]A Drawer containing miscellaneous personalized launchers
[*]A Divider to separate things and keep it tidy
[*]A variety of more personalized launchers copied from the Applications menu.
[*]Indicator Applet 0.3.7
[*]NetworkManager Applet 0.8
[*]Clock 2.30.2 (applet)
[*]Indicator Applet Session 0.3.7 (includes shutdown button)
[/LIST]
With the exception of the application launchers, most of these items can be added by right-clicking on the panel, selecting "Add to Panel..." from the context menu, and then selecting the applets you want to add.  Since you're running a slightly later system, you may not have all the same panel applets available, but you should be able to find everything needed to get a similar level of functionality to what I've described.  The application launchers are added by opening the Applications menu from the GNOME Main Menu, right-clicking on a specific application icon that you want to add, then selecting "Add this launcher to panel" from the context menu.  After you've moved things where you want them, you should right-click on the individual icons and check the "Lock to panel" box.  Easy, huh?

It would have been easier if you had saved a screenshot of your desktop before this accident happened, as that could have guided you in recreating the panel layout the way it was before.  See the attached cropped screenshot of my GNOME 2 top panel.

---

### Post by Krytarik on 2012-03-01
> **Andrew_P said:**
> 
[LIST]
[*]Main Menu (the GNOME Main Menu; includes "Applications", "Places" and "System")
[/LIST]

Yeah, only that this is called "Menu Bar" in the "Add to Panel" dialog, with a 'slightly' confusing description; tricky, huh?! :P

Regards.

---

