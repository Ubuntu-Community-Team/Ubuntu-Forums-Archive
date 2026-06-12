---
title: "how to undo updates and installation in the teminal?"
date: 2009-05-18
forum: General Help
---

### Post by mack27 on 2009-05-18
Hi,
i have performed updates and some installation through the Terminal, but i think i installed some contradictory packages (they were all multimedia packages for playing dvds and so on) or too many plug-ins or such, because i get problems with the video (the screen freezes when the cd/dvd player starts and i get weird color effects). how do i undo this now? :-k thanks!!

---

### Post by XCan on 2009-05-18
You can remove packages using 
sudo apt-get remove <pack_name> or sudo apt-get purge <pack_name>.
Of course to use this you would need to know the names of the packages. If you happen to have forgotten which one you've installed, I guess you would have to dig into the log file in System -> Administration -> Log File Viewer. Or if you can't even get X to start, the log file is in /var/log/dpkg.log.

---

