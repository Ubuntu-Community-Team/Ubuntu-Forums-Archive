---
title: "Borked XFCE menu/app list by running PekWM"
date: 2011-08-27
forum: Desktop Environments
---

### Post by jamiethehutt on 2011-08-27
So I fired up PekWM and tried adding the XFCE panel by running xfce4-panel, this worked OK in PekWM but the Application Menu was blank.

Restarted my session into XFCE and the menu is still blank, and now my panel is crashing. Tried deleting the menu files so they'd be regenerated. Still blank. Deleted all XFCE config files and I get my menu back. 

I open the menu preferences and click default menu (which was already selected) now my menu is blank again. So I select 
/etc/xdg/menus/xfce-applications.menu as the menu file. Ta-da! I have a menu.

I now go to make a launcher for my task bar and I've to search for the application from a list XFCE generates, however this list is now blank. So I can't make new launchers.

Do you guys have any idea of what might be wrong here? I'm pretty sure I'm just needing to delete a broken config file but I'm at a loss to which one it'd be...

Thanks for any help you may be able to provide!

EDIT: Actually I loose the menu every time I restart XFCE and the panel crashes now, regardless of what file I choose...

EDIT EDIT: Well I just deleted my entire .config directory and that seemed to solve it. I had tried deleting just the XFCE related settings but that didn't seem to work...

---

