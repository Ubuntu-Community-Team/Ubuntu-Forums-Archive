---
title: "How do i downgrade KDE?"
date: 2005-11-09
forum: Desktop Environments
---

### Post by z-vet on 2005-11-09
Hi all. 
I would like to install a stable KDE 3.4.3 instead of 3.5 Beta 2 i have installed now. Is there an easy way to do it?

---

### Post by Lambert on 2005-11-09
I'm not a hundred percent on this. Somebody correct me if needed.

1st make sure you've changed your repos back to the original.

Open up synaptic and click on reload.

Search for and highlight [COLOR=Sienna]kdm.[/COLOR]
Click on package in the toolbar and choose force version from the list. choose the version you want. (If you don't have the force version or the correct choice then check your repos). Then click on apply.

There may be some individual program you installed you need to go through the same process. If you get any errors search for that package and see which version you have, then see if you can force it to a downgrade.

---

