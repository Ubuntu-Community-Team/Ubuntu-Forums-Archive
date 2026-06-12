---
title: "Restore Ubuntu?"
date: 2009-03-22
forum: General Help
---

### Post by edta on 2009-03-22
Hey guys,

I'm not quite sure what happened but I get errors running awn in Ubuntu 8.10 don't work because of an "/home/user/.gtkrc-2.0:26: error: unexpected identifier 'panel', expected keyword - e.g. 'style'" and a "Error: Screen isn't composited. Please run compiz (-fusion) or another compositing manager." I also have a ton of random little add on errors so I thought it would be easier if I simply wiped Ubuntu clean and start fresh again. Is there any way to wipe Ubuntu (8.10) clean without uninstalling and reinstalling? I don't really care about the files so no need to save them.

---

### Post by Woody1987 on 2009-03-22
you could try deleting all your configuration files in your home directory. Then when you reboot, ubuntu should create fresh new ones with the default settings.

---

### Post by Tobi-fp on 2009-03-22
Try adding 
"compis --replace" to your session manager..

Or you could run "compiz --replace" and then afterwards run "avant-window-navigator"..

If you do the second thing first, you can see if that is the problem

---

### Post by edta on 2009-03-22
Thanks guys.

Tobi's 2nd solution got rid of my error messages but I'm still going to try Woody's solution to rid of my other problems.

---

