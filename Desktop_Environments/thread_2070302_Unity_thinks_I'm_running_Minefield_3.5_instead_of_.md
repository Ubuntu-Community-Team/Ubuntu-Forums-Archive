---
title: "Unity thinks I'm running Minefield 3.5 instead of Firefox"
date: 2012-10-12
forum: Desktop Environments
---

### Post by Joe_CoT on 2012-10-12
For some reason this morning Unity decided that instead of running Firefox 16, I'm actually running Minefield 3.5. If I click the Firefox icon, it loads firefox, but the launcher doesn't change to indicate that firefox is open, and instead has a launcher for Minefield 3.5.

Here's a screenshot for an example:
[http://i.imgur.com/DEg7i.png](http://i.imgur.com/DEg7i.png)

I looked and I don't appear to have minefield installed. There was a menu entry for minefield that was disabled, and I deleted it. Still the same, after restarts.

Halp?

---

### Post by tuberculo on 2012-10-16
Same problem here. It started just after an update.

---

### Post by tuberculo on 2012-11-05
Solved. In the folder ~/.local/share/applications there was file named firefox-3.5.desktop. Just deleted it and now the icons are ok.

---

