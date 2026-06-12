---
title: "screwed up terminal"
date: 2005-12-15
forum: Desktop Environments
---

### Post by Doomed_Tupperware on 2005-12-15
I checked the "run custom command instead of shell" box and entered ". /etc/.bash_aliases" thinking it would run that on startup everytime and let me continue as normal, but it didn't and now everytime I open it, it closes automatically. How can I change it back to the way it was?

---

### Post by schilcha on 2005-12-15
I don't really want to try, what you did... Here are some suggestions...

Try starting gnome-terminal with the "-x bash" option (read "gnome-terminal -x bash"). Since your term is not working, you can use "Applications > SystemTools > Run as different user" to enter your command line. 

If that doesn't do the job, you can try to remove the offending setting from the configuration-file manually. Open an xterm (again via "run as different user"), open the file ~/.gconf/apps/gnome-terminal/global/%gconf.xml, look for the line containing bash_aliases and substitute the command with something harmless (eg "bash" or just "", which is nothing)

---

### Post by Doomed_Tupperware on 2005-12-15
Thank you so much, I owe you my soul and firstborn.

---

