---
title: "Rhythmbox, Segmentation Fault"
date: 2005-12-11
forum: Desktop Environments
---

### Post by Doomed_Tupperware on 2005-12-11
I've been trying to open Rhythmbox and it just won't start up, so I tried the terminal command rhythmbox and it gave me a segmentation fault. I've already tried reinstalling it and rebooting, what else can I do?

---

### Post by PsychoTrauma on 2005-12-11
Try uninstalling rhythmbox and purging the settings. This can be done with aptitude by selecting the package and pushing "-"(without the quotation marks). You can also use synaptic by right clicking a selected package and choosing "mark for complete removal". Then reinstall rhythmbox. The reason I suggest this is because it might be one of your files that you're loading in your library that's crashing rhythmbox. Purging the settings should reset the folders you have added to your library and you'll be able to see if that is the problem.

---

### Post by Doomed_Tupperware on 2005-12-11
Nope, no go.

---

### Post by PsychoTrauma on 2005-12-12
What version of rhythmbox are you using? If you're using 0.9.0 try uncommenting the backports repos and getting 0.9.1 from there. If you're using 0.9.1 try opening synaptic, finding rhythmbox and forcing the version back to 0.9.0.

---

