---
title: "What program controls the top bar and bottom bar?"
date: 2011-09-25
forum: Desktop Environments
---

### Post by CrimpJiggler on 2011-09-25
NOTE: I solved the problem. The program that controls the taskbars + shortcuts is gnome-panel. 

In GNOME, you know the bottom bar where you can switch between open windows and the top bar that has the clock and volume control icon etc. What program controls that? I seem to have lost my top and bottom bar and also ALT + F2 no longer works. CTRL + ALT + DEL doesn't work either. ALT + TAB still works though. Is there a program that controls all these things?

EDIT: I'm googling to try and find info on this specific problem and  noticed someone mentioned gnome-panel. I checked to see if it was  running on my comp but it wasn't even installed. Just installed it and  ran it and now everything is working again!

---

### Post by 3Miro on 2011-09-25
You uninstalled Evolution, didn't you?

Some program tie in with the panel and you cannot remove them without removing the panel itself. Keep an eye on what you remove.

If you resolved your issue, you can also mark the thread as "Solved" (from thread tools), it helps us keep the threads organized.

---

### Post by mcduck on 2011-09-26
> **3Miro said:**
> You uninstalled Evolution, didn't you?

Some program tie in with the panel and you cannot remove them without removing the panel itself. Keep an eye on what you remove.

If you resolved your issue, you can also mark the thread as "Solved" (from thread tools), it helps us keep the threads organized.

just to add a bit detail here, Evolution is most commonly the application people remove and break the panel in the process.

The thing here is that it is safe to remove Evolution, and that won't cause any problems. However removing *every* package with "evolution" in it's name is not safe, as one of the packages handles the integration between Evolution's calendar and gnome-panel's calendar applet, and removing that package will remove gnome-panel as well.

Just be careful when uninstalling packages and remember to always check what's actually going to get uninstalled before clicking the Apply button. If necessary, add packages to remove one at a time and recheck the changes list to see which packages are safe and which would take more stuff with them.

---

