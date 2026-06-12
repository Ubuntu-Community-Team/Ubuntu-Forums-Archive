---
title: "xfce4-panel freezing in karmic"
date: 2009-12-14
forum: Desktop Environments
---

### Post by arsenix on 2009-12-14
I upgraded to Karmic a few weeks ago and haven't had many issues other than this obnoxious xfce4-panel freeze issue.  Essentially it just randomly freezes.  It usually happens when I click it (ie switching windows or desktops etc).  Top shows it eating almost a whole CPU.  Kill -9'ing it gets rid of it and it restarts itself, although it often freezes again soon after.  It happens every few days, but once it starts to occur it happens frequently.  Is this happening to anyone else?


James

---

### Post by RedSingularity on 2009-12-14
Have you tried reinstalling it?  Maybe a fresh version will work better.

---

### Post by arsenix on 2009-12-15
Haven't really had time to do a full reinstall.  Other than this everything is working fine.  I suppose I could try reinstalling just XFCE.  It appears to be related to the "Task List" panel.  If the task list is removed from the panel it stops freezing.  Seems to be related to the number or type of applications in the task list.

  Searching around I haven't been able to find any other reports of this issue.  Xfce doesn't seem to have any debug output I can find either.



James

---

### Post by RedSingularity on 2009-12-15
Oh no, i meant did you reinstall the task list monitor?  Not the whole OS.  If just the panel is giving you a problem, you can always try doing a fresh install of that.

---

### Post by denis_dupont on 2009-12-15
Hi,
I had freezing problem with karmic I thought, but when I changed the NVidia driver taking 173 instead of the latest (180) everything became fine. Try this if you have a video card with NVidia driver !

---

### Post by arsenix on 2009-12-15
Yeah I did try reinstalling xfce and the panel... no dice.  I guess I'll try installing a debug build of the panel later and try to track it down.  It definitely seems to be tied to either the number of apps open or the type of apps since it only freezes when I am on the workspace which holds my browser and a bunch of other apps.


James

---

