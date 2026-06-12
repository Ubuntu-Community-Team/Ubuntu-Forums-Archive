---
title: "Treviño's repos now have official Fusion release, but..."
date: 2007-08-19
forum: Desktop Effects &amp; Customization
---

### Post by GFree678 on 2007-08-19
for some reason the CCSM has malfunctioned and is showing checkboxes where there used to be none, as if the Actions tab entries have become mangled somehow in certain areas.

For example:

[[IMG]http://img154.imageshack.us/img154/3780/screenshotcompizconfigsqe1.th.png[/IMG]](http://img154.imageshack.us/my.php?image=screenshotcompizconfigsqe1.png)

Most of those checkboxes used to be key shortcut settings but now you can't customize the key shortcuts because they've morphed into checkboxes!

The checkboxes don't seem to do much when clicked, and I'm fairly certain they're not suppose to appear like this. There are a few areas in the CCSM where the Actions tab remains as normal, but most areas have this mangled appearance, which kinda makes key modifications impossible.

---

### Post by yellowband on 2007-08-19
thats unfortunate.  i'm looking forward to install compiz-fusion but think i'll wait until that is fixed.  can somebody post when the repo has the corrected version available.?

---

### Post by hyperair on 2007-08-19
Dammit I'm getting that too. ><

EDIT: I've switched to Vorian's repository temporarily until all is fixed.

---

### Post by GFree678 on 2007-08-19
> **hyperair said:**
> Dammit I'm getting that too. ><
Heh, that makes me glad if only to know it's not just me then. We can share the pain. :lolflag:

---

### Post by thebigham on 2007-08-19
Yeah, i have the same problems too. 3D Windows, Cube Atlantis, Watter Effect and Group and Tab Windows don't seen work either. And also i can't enable the desktop cube by middle click on the desktop with Viewport Switcher now. :(

---

### Post by hyperair on 2007-08-19
You could switch to Vorian's repositories, or wait a while until it's working again. Switching back to Beryl temporarily works too =p

By the way: [http://forum.compiz-fusion.org/showthread.php?t=1012&page=6](http://forum.compiz-fusion.org/showthread.php?t=1012&page=6)

---

### Post by GFree678 on 2007-08-19
Thanks for that.

I think I also know the reason why the configs were "lost" from previous versions - it seems as though the older version stored settings in ~/.conpizconfig, but the upgraded version uses ~/.config/compiz/compizconfig, and so didn't import the old config.

---

### Post by tkboy85 on 2007-08-19
Oh crap...I thought it was my problem. I purged everything, including settings (I just checked, my .compizconfig directory was purged as well), then did a reinstall. Didn't help at all. Guess I'll just wait for an update :)

---

### Post by FuturePilot on 2007-08-19
Gah, same here. That last update seems to have recked havoc on everything. The 3D window plugin no longer works either.

---

### Post by blueeyesmike on 2007-08-19
count me in as well, I update to this supposedly more stable and wonderful compiz and it all of a sudden reverts back to the stone age, key bindings for many options are missing. I had some luck using amarath's backports but am really looking forward to seeing a proper fix for this

---

### Post by writingsama on 2007-08-19
so how do I use that respository?

---

### Post by blueeyesmike on 2007-08-19
For Vorian's go to [http://vorian.org/?p=82](http://vorian.org/?p=82) (Although I had similar problems with this, maybe didn't clear previous pachages properly though)
And amaranth's repo's are detailed at [http://forum.compiz-fusion.org/showthread.php?t=3153](http://forum.compiz-fusion.org/showthread.php?t=3153) her's fixed the problem for me but removed a lot of the plugins I was used to.

Hope that helps

---

### Post by Analord on 2007-08-20
All you need to do is..

Comment out Trevino's for now.

Put vorian repos.

Uninstall as described on vorian's page.
do sudo apt-get autoclean (removes all old version of packages from /var/cache/apt/archives/, all of them not just compiz)
then install as described on vorian's page.

U will have then 0.5.1.

And when trevino does his stuff, ull need to repeat the process by adding Trevino's repos and commenting out Vorian in /etc/apt/sources.list

---

### Post by hyperair on 2007-08-20
You call keep track of what's going on here: [http://smspillaz.wordpress.com/](http://smspillaz.wordpress.com/). It even has an RSS Feed. =p I'll update when I hear anything.

---

### Post by sc00ter on 2007-08-20
Mine's knackered too ... :(

Still usable(ish) but key-bindings and hot-spots are at default. Scale plugin is next to useless at the mo and 3D cube has been crippled too.

Should have read the forum first before letting update-manager do it's worse !! bugger ...

Hope an update comes out of Treviño soon to fix this.

---

