---
title: "Changing Places Menu"
date: 2010-06-27
forum: Desktop Environments
---

### Post by andy_t on 2010-06-27
At the moment my places menu has the entries Computer and 54GB Filesystem but that filesystem is the WinXP partition and not the one linux is installed on, is there any way to change these entries?

Thanks!

---

### Post by teilnehmer on 2010-06-27
As far as I know, the places menu will use the favorites from your file manager (Nautilus in Ubuntu or Dolphin in Kubuntu or Thunar in Xubuntu). So, if you add directories to your favorites in your file manager, they will show up in the Places menu. 

Unfortunately, I do not know how to permanently NOT show certain entries, like your WinXP partition. 
If you don't need the WinXP partition for your work under linux, I assume you could stop it from being mounted in /etc/fstab. Please refrain from changing anything in /etc/fstab before someone else confirms this, I'm a pretty new user myself.

---

### Post by andy_t on 2010-07-03
The partition is not mounted at boot, it mounts when you click on it. I'd rather have Computer and File System than the current two as they would be more useful... I know I could just create a bookmark to / but that's an extra entry and makes the menu longer than it needs to be.

Does anyone know what decides what appears in that menu, is it Computer and the first partition that is usually there?

---

