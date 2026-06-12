---
title: "disable snap-to-top-with-max-windows? (and disable win and alt key w/o modifier)"
date: 2013-04-03
forum: Desktop Environments
---

### Post by iaw4 on 2013-04-03
I am still looking for an easy and safe solution to disable the unity 12.10 feature that maximizes windows when they get close to (want to snap to) the top bar.  this is useful for a <15" screen, but not so useful on a 30" screen.

(I also want to disable use of the windows and alt keys without modifiers.)

possible?

/iaw

---

### Post by JRV on 2013-04-03
install compiz config settings manager with the command:
```

sudo apt-get install compizconfig-settings-manager

```

Run it with the command:
```

ccsm

```

Uncheck Grid near the bottom of the page.

Be careful with other options in ccsm, it is easy to mess things up.

---

### Post by zombifier25 on 2013-04-04
For the Windows and Alt key problem, choose the Unity plugin and disable the "Key to show the HUD" and "Key to show the Launcher" (click them, and uncheck "Enable)

---

### Post by iaw4 on 2013-04-04
I was extremely careful.  I only used ccsm to uncheck "Grid" and "Snapping Windows.  interestingly, this only worked after I clicked on the name, and then unchecked the box on the left.

then I rebooted.  alas, it completely hosed my system.  I no longer see the top bar and the left side bar in my unity 12.04.  when I manage to get a terminal, I can rerun ccsm, but this still has the Grid and Snapping Window both checked, too, despite my having unchecked it before the reboot.  it also has not suppressed the snapping, except I now do not snap to the top bar (because it is gone) but to the top of the screen.

is there any way to get back the sidebar and topbar?

---

### Post by iaw4 on 2013-04-04
more info:

> [   63.411458] unity-panel-ser[2479] trap int3 ip:7f966b011c7f sp:7fff70404340 error:0


and my attempt to restart

> ## /usr/lib/unity/unity-panel-service 

(unity-panel-service:2479): libindicator-WARNING **: IndicatorObject class does not have an accessible description.

(unity-panel-service:2479): LIBDBUSMENU-GLIB-CRITICAL **: dbusmenu_client_get_root: assertion `DBUSMENU_IS_CLIENT(client)' failed

(unity-panel-service:2479): LIBDBUSMENU-GLIB-CRITICAL **: dbusmenu_menuitem_get_children: assertion `DBUSMENU_IS_MENUITEM(mi)' failed

(unity-panel-service:2479): libindicator-WARNING **: IndicatorObject class does not have an accessible description.

** (unity-panel-service:2479): ERROR **: Failed to open connection to bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Trace/breakpoint trap (core dumped)


---

### Post by iaw4 on 2013-04-04
the way to fix it for me was to remove all the .[a-zA-Z] that I did not write.  not sure which one was corrupted.

is there a way to disable the snap-to-top setting and the keyboard HUD keys by editing an XML file?  what exactly did ccsm play with?

/iaw

---

### Post by zombifier25 on 2013-04-05
Hmm, while it's common for Compiz to crash (more like "restarting itself") after a settings change, it's rare to see it completely borked like that after disabling only a simple plugin or two.

For your question, Compiz modifies the dconf settings (gconf in 12.04 and prior). The gconf ones are stored in .xml files in the folder .gconf, while the dconf settings are stored in a binary file. So, no easy way to modify it manually (other than using the dconf editor, but the 2 methods would not be very different from using ccsm itself, which at least organize its settings. In dconf, it's pretty much gibberish for most)

You can try again with ccsm, and if it still crashes, follow this tutorial to reset it: [http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html](http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html)

---

### Post by iaw4 on 2013-04-05
I had tried unity-reset, but it had not made a difference.  the panels still did not launch.  I must have triggered a bug somewhere, perhaps because my bottom menu is on the left side?  or something else that violated some silent assumptions.  or something that is already marginally corrupt but does not present a problem until ccsm tries to read it.  I could see how to recreate and refine the corruption, and then using a dconf dump to explore what specific change triggers the problem.  with dconf dump and dconf-editor, I should be able to pin it down.

is ccsm strictly modifying .gconf, or does it also tinker with something else?

when I do 'dconf dump /', I only get 185 lines of output.  in looking at the keys, I am guessing that I only get to see a subset of possible keys here.  correct?

I don't think 'dconf dump' can read/show the keys in my corrupt older .gconf directory, which I saved.  if it could be examined without being "live", I could then compare what changed, without having to boot in and out of corrupt systems.  this is never much fun.

/iaw

PS: do you happen to know the name of the values which I could change in dconf-editor to eliminate snap-to-top and unmodified keys?

---

