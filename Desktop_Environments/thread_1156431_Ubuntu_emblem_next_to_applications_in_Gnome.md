---
title: "Ubuntu emblem next to applications in Gnome"
date: 2009-05-11
forum: Desktop Environments
---

### Post by NeT_DeMoN on 2009-05-11
I was wondering if I could change the Ubuntu emblem by the "Applications" menu in Gnome, I've tried changing the 48x48 images and another group from other threads but none of them changed that emblem, I'm using a Ubuntu Studio GTK theme that was downloaded from synaptic, is there a possibility that I have to change the themes image too?

---

### Post by Sarai the Geek on 2009-05-11
Go into the folder that contains your icon theme (if it's one you installed yourself, it'll likely be in ~/.icons, otherwise check /usr/share/icons) and then go to scalable>filesystems/places. Replace the icon called "start-here.svg" (it is in either the filesystems or places folder, depending on your theme)  with the icon of your choice. 
You may want to create a backup of the original start here vector image in case you want to go back. :)

---

### Post by NeT_DeMoN on 2009-05-11
That is the thing though... I replaced all those emblems with the one I want then ran 'killall gnome-panel' and when I saw it didn't work I logged out and logged back in and it still didn't work.

---

### Post by Jfedak on 2009-05-11
Hmm, I'm having some trouble with this as well. It's not allowin me to delete the start-here.svg file or to replace it with a new one.

---

### Post by NeT_DeMoN on 2009-05-11
> **Jfedak said:**
> Hmm, I'm having some trouble with this as well. It's not allowin me to delete the start-here.svg file or to replace it with a new one.
Use the terminal and type 'sudo mv start-here.svg "other place"' mv and cp works.

---

### Post by Jfedak on 2009-05-11
ok, got it to move, however, the image is still the same, but now when i go to add it to the panel, it shows the image I want... but it doesn't show it on the actual panel once it's added.

---

### Post by Sarai the Geek on 2009-05-12
> **Jfedak said:**
> ok, got it to move, however, the image is still the same, but now when i go to add it to the panel, it shows the image I want... but it doesn't show it on the actual panel once it's added.

Try replacing the "distributor-logo" icon as well. 

Also, after making changes to icon sets you'll want to to go into appearances, change the icon theme to a different one, then change it back. Dunno why this is necessary, but it is (logging out or restarting X would work as well).

---

### Post by Sarai the Geek on 2009-05-12
> **NeT_DeMoN said:**
> Use the terminal and type 'sudo mv start-here.svg "other place"' mv and cp works.

If you feel like living life on the edge, you could also do this in the gui by typing "gksudo nautilus" then performing the action like you tried to do before. But remember, you have the ability to seriously mess up your computer when running nautilus as root. Proceed with caution.

---

