---
title: "Panel Launch Problems"
date: 2009-01-08
forum: Desktop Environments
---

### Post by wallyspratz on 2009-01-08
Former Windows user here, who moved over to Mac 
and now I'm simply lovingggggggg Ubuntu!!

I'm having a problem with the panel- I can't add anything to it. That option is greyed out (along with add panel and delete panel)

When I right click top panel and select the option: "Allow panel to be moved" I get the following error: 

The application "gnome-panel" attempted to change an aspect of your configuration that your system administrator or operating system vendor does not allow you to change. Some of the settings you have selected may not take effect, or may not be restored next time you use the application.

Details:
Can't overwrite existing read-only value: Can't overwrite existing read-only value: Value for `/apps/panel/toplevels/top_panel_screen0/disable_movement' set in a read-only source at the front of your configuration path.

I've had that message many times, including once on startup after
reinstalling the following three packages:

gnome-panel
gnome-panel-data
gmome-panel-dbg

And the problem persists

Any idea how to fix this? Is this a permissions prob? If so, what is the path to the app?

Your help would be greatly appreciated.

Thanks

---

### Post by gettinoriginal on 2009-01-10
Yes, it is a permission problem.  Select F2 and in the box type ```
gksudo nautilus
``` and navigate to: /apps/panel to check permissions and change if necessary.

---

