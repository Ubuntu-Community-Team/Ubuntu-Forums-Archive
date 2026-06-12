---
title: "compiz updates"
date: 2007-06-24
forum: Desktop Effects &amp; Customization
---

### Post by saldie on 2007-06-24
I followed this guide to get compiz fusion running:

[http://ubuntuforums.org/showthread.php?t=481615](http://ubuntuforums.org/showthread.php?t=481615)

This morning I have about ten update related to compiz, I still have the repositories unabled.
Shouls I go ahead and update?  I don't want to break compiz, which is working great.
By the way the upade manager is saying something about a partial update.

---

### Post by gkiller on 2007-06-24
Since Treviños repository has packages built directly from git, they will be updated often. Normally with every update there will be more plugins, options or bugfixes, but occasionally an update might break compiz or individual plugins.

If you don't want this, disable the repository again and you won't be asked again.

For this newest update, you have to do an "sudo apt-get dist-upgrade" and "sudo apt-get install libcompizconfig-backend-gconf" to get all the new packages, since Treviño changed the names of a few packages. The obsolete ones will get uninstalled automatically this way.

---

### Post by aidanr on 2007-06-24
> **gkiller said:**
> ..do an "sudo apt-get dist-upgrade" and...
You do **_not_** have to dist-upgrade and I wouldn't recommend it, I applied the compiz updates yesterday without any problems

---

### Post by saldie on 2007-06-24
Ok, thanks for the info.

---

### Post by walkerk on 2007-06-24
i ran updates and everything works great still.. if compiz fusion breaks just remove and re-install.. compiz fusion is in beta stages.. don't be scared to help test it. if you were able to install it successfully once why do you think you can't do it again? took my 5 minutes to remove compiz/beryl and upgrade to fusion..

---

### Post by saldie on 2007-06-24
I just did the upgrade and every thing went fine.
:p

---

### Post by gkiller on 2007-06-24
> **aidanr said:**
> You do **_not_** have to dist-upgrade and I wouldn't recommend it, I applied the compiz updates yesterday without any problems
Where is the harm of doing dist-upgrade? It simply automatically removes the now obsolete package compizconfig-plugin and updates libcompizconfig0 to the new version. Of course you can do that manually.

Of course if you have a lot of other repositories enabled, dist-upgrade might trigger some other upgrade processes, but you should be able to read and interpret the output of apt-get anyway if you are doing this.

---

### Post by aidanr on 2007-06-24
Sorry, my bad

I thought it would upgrade to Gutsy, but I looked into it and you'd have to change your sources.lst aswell
But still I don't think it's necessary, compizconfig-plugin was auto-removed  for me anyway without having to do anything extra

---

### Post by gkiller on 2007-06-24
Ok, then it might not be necessary anymore, I don't know. Maybe Treviño changed already something. That advice came directly from him this morning. Maybe it's only needed on some configurations.

---

### Post by saldie on 2007-06-24
One more question gkiller, should I be entering whose two commands you mention in your first post every time I get updates from Trevino's repositories?
TIA.

---

### Post by gkiller on 2007-06-24
> **saldie said:**
> One more question gkiller, should I be entering whose two commands you mention in your first post every time I get updates from Trevino's repositories?
TIA.
No. Normally you can just update using the update manager that pops up when something is available. Just this time some package names were changed which does not happen very often (maybe more often now in the beginning until there is a first official compiz/fusion package).

---

