---
title: "Enabling only security updates"
date: 2006-06-23
forum: Desktop Environments
---

### Post by dengar on 2006-06-23
How do you go about only enabling security updates for ubuntu? Particularly now that I have compiz working nicely I'd rather not screw it up based on bad upgrades. Would I need to disable the repositories under than the security one? Is there a way to do that only for the update manager and not for synaptic in general?

---

### Post by Ramses de Norre on 2006-06-23
If it's only compiz you could lock only that package to his version, to do so select the package in synaptic, open the package menu and choose lock version.

Otherwise you could indeed comment out all other repos but you wont be able to install packages without uncommenting them everytime..

---

