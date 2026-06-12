---
title: "[SOLVED] Gnome panel Menu screenshots?"
date: 2008-04-19
forum: Desktop Environments
---

### Post by Confuzius on 2008-04-19
I'm trying to take a screenshot of the gnome panel system menu to show someone where something is, but it seems that print screen doesn't work when the menu is open.

Any suggestions, or is this "expected behaviour"?

Thanks kindly.

---

### Post by n0kS on 2008-04-19
Here's something that can help you:
sudo apt-get install scrot
scrot -cd 10

And you will have 10 secs to open your gnome menu and wait until it countsdown to get the screenshot :)
ps: (the image is saved in the current terminal's directory)

---

### Post by Confuzius on 2008-04-19
That did it, thanks!

---

