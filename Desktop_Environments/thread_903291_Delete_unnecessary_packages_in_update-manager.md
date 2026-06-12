---
title: "Delete unnecessary packages in update-manager?"
date: 2008-08-28
forum: Desktop Environments
---

### Post by aviceda on 2008-08-28
I've just installed Hardy on an Asus eeePC 701 and would like to remove notification of package upgrades like Compiz which are far too large, Is there an easy way of doing this? Get fed up of having to un-check boxes to prevent downloading them.

---

### Post by mocoloco on 2008-08-28
If they're package you don't actually use you can uninstall those apps in synaptic, just be careful of course that nothing important depends on them.

If it's stuff you use you can force the current version, in synaptic find and select the package, then go to Package -> Force Version, and select your current version.  Then it shouldn't ask you about updating it.

---

### Post by aviceda on 2008-08-28
Thanks Moco, hadn't thought of using Synaptic, I was under the impression that the 'notified' applications were not already installed, but when I check,  they are and can be uninstalled.....thanks a lot!
Hope that made sense...
Tom

---

### Post by mocoloco on 2008-08-28
Those notifications are for *updates* to already installed packages. You won't be offered anything new through the update manager. And maybe I should clarify that Update Manager just uses Synaptic on the back end, thus changes in Synaptic affect it.  Never though about how that might seem strange since I've been using it for so long :)

---

