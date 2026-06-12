---
title: "how to make drive icons appear on right side?"
date: 2008-10-03
forum: Desktop Environments
---

### Post by Entheogen on 2008-10-03
i have a stupid question about gnome.. for example, i want all my cd/dvd icons appear on the right side of desktop and i want them stretched. can i do that and how? :) i can do that for one icon, but gnome doesn't remember that, so when i insert another cd it is small icon on left side..

---

### Post by mandrill on 2008-10-03
> **Entheogen said:**
> i have a stupid question about gnome.. for example, i want all my cd/dvd icons appear on the right side of desktop and i want them stretched. can i do that and how? :) i can do that for one icon, but gnome doesn't remember that, so when i insert another cd it is small icon on left side..

I believe you can accomplish that with the configuration editor. if you do not have it installed, do so - it will appear under System Tools.So your path will be system tools > configuration editor > apps > nautilus > icon view, or > preferences.

---

### Post by Entheogen on 2008-10-03
you are talking about gconf-editor? if so, i cannot find any configuration line that could help me.. :|

---

### Post by mandrill on 2008-10-03
> **Entheogen said:**
> you are talking about gconf-editor? if so, i cannot find any configuration line that could help me.. :|

I just tried this, and it worked. Whether it will in your particular instance or not, I don't know.

Right-click desktop, uncheck "keep aligned" - move icons to where you want them, re-check "keep aligned". I restarted and and everything came back up on the right side, just where I left it.

---

### Post by Entheogen on 2008-10-03
it works for one cd.. i set one dvd "Movies" to right corner and stretched it, and whenever i insert that disk it is on right side & stretched. but when i insert another disk, for example some data disk, it is on left corner & small icon. :|

---

### Post by mandrill on 2008-10-03
> **Entheogen said:**
> it works for one cd.. i set one dvd "Movies" to right corner and stretched it, and whenever i insert that disk it is on right side & stretched. but when i insert another disk, for example some data disk, it is on left corner & small icon. :|

I bet a symlink would do it.

---

### Post by Entheogen on 2008-10-04
i think symlink wouldnt appear when cd inserted and disappear when ejected.. :|

---

### Post by mandrill on 2008-10-04
> **Entheogen said:**
> i think symlink wouldnt appear when cd inserted and disappear when ejected.. :|

I think you're right. This may be one of those deals where you spend a disproportionate amount of time looking for what turns out to be a completely simple 10-second solution.

Good Luck!

---

