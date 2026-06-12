---
title: "Tomboy Notes inconsistent at startup"
date: 2009-06-12
forum: General Help
---

### Post by dansmith on 2009-06-12
I've added Tomboy Notes to my list of Startup Applications.  What I want is to display the note icon in the Notification Area for easy access.  For some reason, however, what frequently happens is the "Search All Notes" window opens as well.  Also, when I close this window, the notification icon *sometimes* goes away, and sometimes continues to run.  As a result, I usually have to manually restart the app, defeating the purpose of Startup Applications.

The default behavior of the "tomboy" command is, I believe, to display the notification icon only.  This is what happens whenever I manually run it.  The launcher in the Applications->Tomboy Notes uses an (undocumented) "--search" option to force the search window to open.  My launcher in the Startup Applications list simply invokes "tomboy", so I do not expect the search window to appear at startup.  Yet it occurs intermittently: sometimes I just get the icon at startup, and sometimes I get the search window.

Compounding the problem is the strange behavior of closing the window: sometimes when I close the search window that appears at startup (via the window's X button), the notification icon goes away too; sometimes it does not.  In this case, I can reproduce the problem manually, but still can't figure out the pattern: by running "tomboy --search" from the command line and closing the window (sometimes clicking other things first), sometimes the notification icon goes away and sometimes it does not.

---

### Post by dansmith on 2009-06-12
Guess this is a known issue:

<https://bugs.launchpad.net/ubuntu/+source/tomboy/+bug/112703>

Two workarounds seem possible: first, use "sleep" to delay launching Tomboy until panels have been properly initialized; second, add the "Notes" item directly to a panel rather than using the Notification Area.  (Tomboy instances living on a panel apparently do not create a duplicate icon in the Notification Area.)

---

