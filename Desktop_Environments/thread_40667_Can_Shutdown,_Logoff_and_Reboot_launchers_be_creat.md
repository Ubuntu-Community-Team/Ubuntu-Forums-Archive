---
title: "Can Shutdown, Logoff and Reboot launchers be created?"
date: 2005-06-09
forum: Desktop Environments
---

### Post by MetalMusicAddict on 2005-06-09
Like the title says. :)

I like to have shortcuts on the desktop for these but I cant seem to do it in Ubuntu. I think Im missing a command.

---

### Post by codejunkie on 2005-06-09
make a launcher with gksudo telinit 6 this will reboot and gksudo telinit 0 will shutdown the computer. as for log off i haven't found that one yet hope this helps.

---

### Post by MetalMusicAddict on 2005-06-16
Does anyone know the command for "Logoff"?

---

### Post by fastluck on 2005-06-16
I tried 'killall kdesktop'. Got an interesting result, but it didn't log me off.  Interesting, though.  My terminal stuck around and when I typed kdesktop even this web site was still active in my browser.  Cool.

---

### Post by intangible on 2005-06-18
[QUOTE=MetalMusicAddict]Does anyone know the command for "Logoff"?[/QUOTE]
 gnome-session-save --kill

---

