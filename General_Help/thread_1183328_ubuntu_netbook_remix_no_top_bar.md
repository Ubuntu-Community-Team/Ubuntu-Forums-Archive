---
title: "ubuntu netbook remix no top bar"
date: 2009-06-09
forum: General Help
---

### Post by goosemontana on 2009-06-09
i just installed ubuntu netbook remix today and i really like it but i have a problem. i was deleting things from my favorites and somehow the top bar went away. ive tried opening the terminal and typing gconftool-2 --shutdown then rm -rf ~/.gconf/apps/panel then pkill gnome-panel but that didnt work. can someone help me?

---

### Post by goosemontana on 2009-06-10
should i reinstall ubuntu? would that fix it?

---

### Post by fooman on 2009-06-10
open a termianl and try this:

```
gnome-panel &
```

see if that helps.

---

### Post by Brandon Williams on 2009-06-10
[This post](http://ubuntuforums.org/showpost.php?p=7323838&postcount=40) may explain what has happened if deleting items from the menu is the problem. Alternatively, if you used desktop-switcher at some point (to go from UNR to classic mode or vice versa), then [this info](http://www.ubuntu.com/getubuntu/releasenotes/904#Missing%20GNOME%20panels%20in%20Ubuntu%20Netbook%20Remix%20after%20using%20the%20desktop-switcher%20application) from the release notes might help.

---

