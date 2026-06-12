---
title: "[SOLVED] Can't change mouse cursor"
date: 2008-12-14
forum: General Help
---

### Post by N00b-un-2 on 2008-12-14
I'm running Ubuntu 8.10, and ever since I installed 8.10 I've had a minor, yet very annoying problem with my mouse.  Whenever I try to change my cursor from the default "DMZ-White" cursor set, my cursor reverts back to a lo resolution black cursor set, and the cursor theme that I choose is only visible while the pointer is located over a Firefox browser window.
I tried overwriting the default index.theme file to "DMZ-Black" but it didn't have any effect.  I've tried installing other themes, deleting themes, etc and nothing will fix the problem.

---

### Post by eternalnewbee on 2008-12-14
Could be a conflict with compiz. Try: **ALT-F2**, and enter ```
metacity --replace
```
And try and see if you still have this problem.
Another thing (assuming you are using compiz) is to set the Window Decorator to GTK.

---

### Post by N00b-un-2 on 2008-12-14
Thanks a lot!  I tried metacity --replace command, and while it fixed the problem with the mouse, it messed up my theme and turned off the Avant dock.  I tried the gtk-window-decorator --replace command and it worked like a charm.  The mouse works properly in all programs and it didn't change my theme.  I guess it was a conflict with Emerald.

---

### Post by Kieran.s on 2008-12-23
Rather than me posting a separate thread, I might as well ask here. Now that I'm running 8.10 I cant seem to find where to change the style of my mouse. I've tried, mouse and appearance in preferences, but I am still unable to find the option to change it.

---

### Post by le singe on 2009-01-22
> **eternalnewbee said:**
> 
Another thing (assuming you are using compiz) is to set the Window Decorator to GTK.

Just curious, how do you go about this?  Must you type something in under "Command" in the  Window Decoration setting of compiz?  Will this disable emerald?

---

### Post by reahjw6 on 2009-01-22
Apperance preferences>theme>customise>pointer.

In synaptic oxygen has some nice pointer themes.

---

### Post by Shpongle on 2009-07-21
im having the same problem as the OP on jaunty and it seems to be compiz thats the problem, except i want a blak cursor instead of a white one, it only works in firefox , and in metacity and xfwm4 but i prefer using compiz coz of things like the ring switcher , any one know of a workaround for compiz?

---

### Post by rolandixor on 2009-08-12
seems from what I read that our ccsm is patched to remove this option (sometimes devs do silly things). I'll try to recompile the original and see if it works, and then try changing my cursor.

---

### Post by munooka on 2009-09-10
You can change the cursor theme using gconf-editor under:
/apps/compiz/general/allscreens/options/cursor_theme

Change the key to  your current theme and Bob's your mother's brother.

---

### Post by Andrew_P on 2009-10-14
In a now-closed thread (313016) elsewhere on this forum there was a reference to using gcursor to change mouse pointer appearance.  In the Add/Remove Applications list for Intrepid Ibex (8.10), it is listed as "Cursors Selection".  It installed without problems and the startup icon resides in System > Preferences, but the program doesn't appear to work in 8.10 anymore.  Clicking the various buttons and icons has no effect; the only button that works is "Close".  See also thread 628988, regarding cursor installation problems in Hardy Heron.

This issue of changing cursors in Gnome is an ongoing comedy of errors, a problem that was solved in Microsoft Windows 95 back in 1994.  Pathetic.:(

---

### Post by jeight on 2010-04-22
[QUOTE=munooka;7926443]You can change the cursor theme using gconf-editor under:
/apps/compiz/general/allscreens/options/cursor_theme


This is the correct fix. After you get to cursor_theme right click and select unset option. Then go the themes and change the mouse pointer to what pleases you. Log out. Log in. Done.

---

