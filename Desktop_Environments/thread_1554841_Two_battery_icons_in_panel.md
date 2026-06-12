---
title: "Two battery icons in panel"
date: 2010-08-17
forum: Desktop Environments
---

### Post by gibber1sh on 2010-08-17
I've recently installed 10.04 on my laptop and spent some time configuring it. A while ago I've noticed that there are now two battery icons in the panel in the top-right corner. One seems to be attached to the indicator applet and the other one sits by itself. Changing the settings in the Power Management menu affects both icons in the same way (I can either show or hide them both). Is there any way to remove the extra icon and just keep the one integrated into the indicator?

This is a very minor annoyance really, but it'd still be nice if there was a fix for it.

Update: Now the battery icon in the indicator applet has changed to the chat "evelope" icon, but it still acts as a battery icon (same menu). Something is definitely not right here...

---

### Post by TNT1 on 2010-08-17
when you right click on it, can't you remove it?

---

### Post by gibber1sh on 2010-08-17
Nope, right-click does nothing, and left-click opens a menu showing only the status and a link to the preferences menu (which is also of no help)

---

### Post by Fergin on 2011-10-15
I also have the same problem after upgrading from 11.04 to 11.10
 at 11.04 the battery icon is missing, but 11.10 becomes two
 how to remove it???

---

### Post by jlregeim on 2011-10-19
Yeah, got two icons as well in 11.10 after upgrade from 11.04.  Had 1 icon in 11.04.  Now that I have two, only one 'works'.  Haven't felt like poking around the OS yet, but there must be a simple fix.

---

### Post by practic on 2011-10-23
It's been reported as a bug:

[https://bugs.launchpad.net/ubuntu/oneiric/+source/gnome-settings-daemon/+bug/833397](https://bugs.launchpad.net/ubuntu/oneiric/+source/gnome-settings-daemon/+bug/833397)

But a quick solution is to make sure you haven't whitelisted all tray apps. 

Open DConf-Editor, go to desktop-unity-panel, and look at the "systray-whitelist" item.

If it says ['all'], change it to ['skype','empathy'] and add in any other particular apps you need. Then logout and back in.

---

