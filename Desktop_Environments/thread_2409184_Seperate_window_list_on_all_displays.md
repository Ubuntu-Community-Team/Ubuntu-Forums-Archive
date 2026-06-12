---
title: "Seperate window list on all displays"
date: 2018-12-29
forum: Desktop Environments
---

### Post by peterterbe on 2018-12-29
I'm trying to set up a multi monitor configuration where I have a panel or taskbar on each displays and each taskbar shows only those apps that are on their screens.
So far I've tried some shell extensions like dash to panel and hide top panel, etc in order to have a fully functional desktop but I can't find anything to solve this.

In addition I would like the windows of each screens to open other windows only on their screen and not the other. 
And last displays should be reminded: if I plug off my display every window should show up on the first screen and if I plug the display back in the windows originally were opened to the second display should move back to the second display.

What are my options for such a config?

I'm using Ubuntu 18.04 with Gnome 3.28.2.

---

### Post by vanadium on 2018-12-29
I am afraid you won't get far with Gnome because of the way how Gnome works by design with multiple monitors and multiple workspaces. By default, the second monitor is just a static second monitor. Workspace switching happens on monitor one. Still, that can be changed by changing the key org.gnome.mutter workspaces-only-on-primary to false. Then, the multiple monitors are each looking at different places on the same workspace, and switching workspaces will switch the view on both monitors. I do no think it is possible at all to have Gnome consider different monitors as different workspaces.

The tiling window manager i3 works more according to your expectations. There, one monitor is a separate workspace. By default, new workspaces are automatically created alternatively on each of the monitors. So add for example a tint2 panel or a dock to that setup, and your first and second requirements will be set. Yet, i3 is "not for the masses".

The last requirement, that windows are grouped on the first screen when you unplug a monitor, and then selectively return to that monitor when you plug the monitor back in, will be very hard to achieve in any desktop environment, I suspect.

---

