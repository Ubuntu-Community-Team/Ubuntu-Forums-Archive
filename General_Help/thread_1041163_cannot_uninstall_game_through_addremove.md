---
title: "cannot uninstall game through add/remove"
date: 2009-01-16
forum: General Help
---

### Post by Universal344 on 2009-01-16
I recently installed the game Lbreakout2 from add/remove programs and now I want to remove it.  However, when I try to remove it add/remove tells me to use synaptic because some applications depend on it.  When I search for LBreakout2 in synaptic I see two packages, Lbreakout2 and LBreakout2-data.  Are these the only two packages that need to be removed?  If so should I tell synaptic to mark for removal or mark for complete removal?  Thank you for any help you can provide.  

Oh, and is there a general rule for how to get rid of applications when add/remove won't uninstall them (like: search the application name in synaptic and completely remove all packages with the name.  Or something of the sort.)

---

### Post by redilyn on 2009-01-16
If you select to remove LBreakout2 it will mark any other apps which depend on it as well. It should tell you what apps those are.

You are correct, the standard way to remove apps that wont remove from add/remove is to search them in synaptic and remove the offending app while paying close attention to any other apps it lists which are going to be removed as well.

BTW, The difference between remove and completely remove is:

Remove = removes the files but keeps the settings in case you want to reinstall later
Completely remove = removes the files and settings

---

### Post by Universal344 on 2009-01-16
> **redilyn said:**
> If you select to remove LBreakout2 it will mark any other apps which depend on it as well. It should tell you what apps those are.

When I deselect it in add/remove to uninstall it tells me to use synaptic and nothing about automatically marking other apps which depend on it fro removal as well.  

> **redilyn said:**
>  You are correct, the standard way to remove apps that wont remove from add/remove is to search them in synaptic and remove the offending app while paying close attention to any other apps it lists which are going to be removed as well.

And when I mark the packages for removal how will I see which other packages it will remove due to the dependencies?

---

### Post by redilyn on 2009-01-16
Opps sorry, You need to mark it for removal in synaptic.

When you do so it should open another window which will tell you the apps it will remove.

Just check that list over carefully to make sure you don't remove something you want.

---

### Post by Universal344 on 2009-01-16
Alright just to be sure, to uninstall Lbreakout2 I should right click lbreakout2 and lbreakout2-data in synaptic and mark of complete removal (I won't be reinstalling it) then look over what else will be removed and proceed if it is nothing I care about. Oh and if it tells me that something else will be removed but I don't know what is, can I proceed or am I at risk of loosing something important.  Thanks!

---

### Post by redilyn on 2009-01-16
> 
Alright just to be sure, to uninstall Lbreakout2 I should right click lbreakout2 and lbreakout2-data in synaptic and mark of complete removal (I won't be reinstalling it) then look over what else will be removed and proceed if it is nothing I care about.


Yep you got it.

> 
Oh and if it tells me that something else will be removed but I don't know what is, can I proceed or am I at risk of loosing something important. Thanks!


If it is something you do not recognize you should search on google or post here before proceeding. Every case is different so I can not say for certain that it would be safe to continue.

---

### Post by Universal344 on 2009-01-16
I marked lbreakout2 for removal and the only other package that needed to be removed as well was lbreakout2-data.  I clicked proceed and the packages were removed successfully, thank you for your help.

---

