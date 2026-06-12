---
title: "solving keyboard layout issue"
date: 2008-04-09
forum: Desktop Environments
---

### Post by fela on 2008-04-09
Does anyone have the problem where their keyboard layout goes funny, as in, keys don't work and such? I got it, and what i did, is reconfigure X by issuing this command in terminal: ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` then I went to System > Preferences > Keyboard, to the layout section. I deleted the layout, added another one, and made sure it wasn't selected as 'default'. Seemed to work fine after that!

This is just my solution if anyone else is having this problem.

---

