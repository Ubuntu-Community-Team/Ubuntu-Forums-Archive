---
title: "Can not change resulation of display"
date: 2006-06-11
forum: Desktop Environments
---

### Post by sadeqn on 2006-06-11
Hi,
When I use LiveCD on my PC (with NVidia card) I can change resulatio to any thing I want. but after I install it on HDD, after click on apply to set my favorate resluation insted of default I see that X restart but no thing change. :confused: 
I want to set the resulation to 1024x768 @ 85hz refresh rate.
Is ther any one help me?

---

### Post by Zelut on 2006-06-11
You could try running the xserver auto-detect again & see if that makes any changes for you.  You can also make manual changes in that setup, IF you know what you're doing.

at the terminal run 'sudo dpkg-reconfigure xserver-xorg' and it'll run thru some questions for you.  You can always safely use defaults if you are unsure.

---

