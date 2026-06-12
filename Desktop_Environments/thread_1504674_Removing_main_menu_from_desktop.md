---
title: "Removing main menu from desktop"
date: 2010-06-08
forum: Desktop Environments
---

### Post by panchovilla on 2010-06-08
Hello. I'm trying to set up my system(Ubuntu 10.04) so that the main menu and its contents (application, places, system, etc) do not appear(or are hidden in such a way that the user cannot access it). This sounds counter-intuitive. I know. I tried deleting them by hand, but they reappear after every reboot. Is there a system file with preferences that I can edit or something else that can be done?

---

### Post by Breambutt on 2010-06-08
Quoting myself:

Hit System > Preferences > Advanced Desktop Somethingrather or CompizConfig Settings Manager and find Widget Layer under the Desktop category and add the line **class=Gnome-panel** in the empty field under the Behavior tab.

So, this requires compiz and the Widget Layer comes in compiz-fusion-plugins-extra.

I'm using Cairo Dock on the bottom of the screen on auto-hide. This mostly because of the modular nature of Linux audio eats up a lot of desktop space. Not complaining though, all is fine and dandy.

---

### Post by panchovilla on 2010-06-08
Hey, thanks for the adivce!

I have compiz and the extras installed, but have no icon in the System menu. I tried running it by adding a custom item on the menu, running as compiz, with no luck.

Is there a terminal command to get the UI started up?

---

### Post by Breambutt on 2010-06-08
Huhmh, strange. Guess you'll have to install compizconfig-settings-manager manually. It should appear in the menus but if it doesn't, just start typing *compiz* in terminal and hit tab to see your options.

Edit #546: Lots of typos today.

---

