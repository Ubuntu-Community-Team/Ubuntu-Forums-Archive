---
title: "gnome panel gone no fkeys"
date: 2009-04-05
forum: Desktop Environments
---

### Post by reahjw6 on 2009-04-05
Hey all
my gnome panel has gone and i can not use the fkeys so cant run altf2.
I believe if i put this into the terminal it will bring back my panel   gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel.

How do i get into the terminal to run the code.
Thanks reah.

---

### Post by gettinoriginal on 2009-04-05
Are you sure it is gone, or just hidden.  And may I ask why you cannot use the F2 key ??

---

### Post by reahjw6 on 2009-04-05
I have no ideas why i can not use the fkeys they have always worked before.
How can i get the panel back if it is hidden.
I still have icons on my desktop just no panel.
Thanks Reah

---

### Post by reahjw6 on 2009-04-05
Ok i am an idiot.
Before going out this morning i removed Evolution.
So i ctrl>alt>dlt and went into failsafe gnome terminal installed Evolution then installed gnome-panel and all is now ok.
I thought the best way was to retrace my steps.Fkeys all ok now as well.
Can anyone explain why uninstalling Evolution affected the gnome panel.
Thanks Reah

---

### Post by gettinoriginal on 2009-04-05
Uninstalling Evolution uninstalls Gnome Desktop.  For whatever reason, they are tied together within the dependencies.

---

### Post by reahjw6 on 2009-04-05
Thanks for explaing that will mark as solved.

---

