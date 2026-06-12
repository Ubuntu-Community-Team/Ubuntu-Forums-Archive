---
title: "This sounds like a bug to me.."
date: 2005-12-21
forum: General Help
---

### Post by three_sixteen on 2005-12-21
Whenever I put a photo CD into my CD drive my computer reads it, I can view the pictures okay.  But when I try to eject the CD from the drive it turns out that I can't.

I either have to reboot my computer or eject the CD manually.  If I eject the CD manually it perpetually tries to read a CD that isn't there anymore until I reboot the computer.

---

### Post by localzuk on 2005-12-21
How are you trying to eject the cd?

---

### Post by frodon on 2005-12-21
It's the linux behaviour. Right click on the cdrom icon on your desktop or in the file browser and click "eject CD".
In a terminal the command "eject cdrom0" do the same thing, if you want to force the eject use the "sudo eject cdrom0" command.

---

### Post by three_sixteen on 2005-12-21
[QUOTE=frodon]It's the linux behaviour. Right click on the cdrom icon on your desktop or in the file browser and click "eject CD".
In a terminal the command "eject cdrom0" do the same thing, if you want to force the eject use the "sudo eject cdrom0" command.[/QUOTE]

Thanks, both right clicking the icon on my desktop and the console command work.  I did try to right click the cdrom icon in file browser, but that didn't do anything.

:D

---

