---
title: "Uninstall updates installed from Ubuntu repository"
date: 2009-03-22
forum: General Help
---

### Post by abcuser on 2009-03-22
Hi,
I have installed Lokalize that is program for translation .po files into several languages. Program was working without any serious problem.

Now I have after some weeks updated Ubuntu from System | Administration | Update Manager. I saw there was also an update of Lokalize and I installed update in hope it will fix some security problems.

But know I see this program update made Lokalize very unstable. So I uninstalled it from Applications | Add/Remove and installed it again. Problems persists. I tried Synaptic and the same problem persists.

Now I am wondering if there is any way that I can install previous version of Lokalize, that was working without any problem or to uninstall updates. Is this possible?

Please don't say that I should report bug to Launchpad. I have had working version of product and I would like it back, I don't need update which makes product unstable.

Any idea how to install previous version of Lokalize from Ubuntu repository?
Regards

---

### Post by MaindotC on 2009-03-22
If you got o Synaptic -> File -> History it should show you what packages were installed, upgraded, and when.  You can use that list to uninstall anything regarding Lokalize.  Be sure to mark them for complete removal.

---

### Post by zvacet on 2009-03-22
Removing package from synaptic will be partial job.Anytime he want to install package again it will install unstable version( one OP don´t want).Go to /var/cache/apt/archives and see if you have two versions of Lokalize there.If you do delete latest so that previous one can be installed.When you install old version again then in synaptic **lock version.** You can do same thing from terminal 

```
sudo aptitude hold package_name
```

---

### Post by CatKiller on 2009-03-22
You don't need to mess around deleting anything, or uninstalling anything. Open up Synaptic Package Manager, find lokalize in the list, and then select Package -> Force Version... This will give you a dropdown list of the versions that are available. Pick the older one that worked better for you and then hit the Force Version button. If you don't want any updates to this package, you can select Package -> Lock Version to prevent new versions being installed. When this package has been fixed, you can de-select Lock Version to start getting updates to it again.

---

### Post by MaindotC on 2009-03-22
CatKiller - I didn't know about this.  Thank you for sharing - I learn something new everyday.  Hope it helps OP.

---

