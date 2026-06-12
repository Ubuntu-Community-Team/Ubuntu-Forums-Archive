---
title: "Gnome Places open with gedit"
date: 2011-04-06
forum: Desktop Environments
---

### Post by DhmMelb on 2011-04-06
After doing most of the upgrades I rebooted and found a strange error in Gnome.

Something happened with mime settings.  All but one of the items in the **Places** menu had been set to be opened with **gedit**.  I tried to mount one of my Windows partitions and gedit opened with an error that that was not a text file.  I tried to open my** Documents** folder and got the same error.   So did the **File System**.

Fortunately **Computer** would still open normally and the items shown there (the other partitions and the File System) could still be clicked.

Somewhere deep in Gnome's configuration it has screwed up the items in **Places**.  But where is it?  I have not been able to find anything using **gnome-editor**.

If someone knows where these settings are it would be easy to fix.

---

### Post by ~Plue on 2011-04-06
> **DhmMelb said:**
> 
Somewhere deep in Gnome's configuration it has screwed up the items in Places.  But where is it?
in *~/.local/share/applications/*[I][I]mimeapps.list
[/I][/I]delete,* inode/directory=gedit.desktop........* (the entire line)

-good luck

---

