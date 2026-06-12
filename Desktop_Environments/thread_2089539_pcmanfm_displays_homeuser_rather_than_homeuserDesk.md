---
title: "pcmanfm displays /home/user rather than /home/user/Desktop"
date: 2012-11-29
forum: Desktop Environments
---

### Post by spadewarrior on 2012-11-29
I've installed Lubuntu 12.04 over the top of a slightly borked Crunch Bang installation and now it appears that pcmanfm is managing my /home/user folder rather than my Desktop folder. It seems to have got confused about the path to display and I'm wondering if this is somehow due to a conflict with pre-existing LXDE config files.

If I load up a pcmanfm window and click on 'Desktop' in 'Places' I get taken to my home folder too. Any idea how I can change this, and how it might have occurred?

Thanks :)

---

### Post by Isamu715 on 2012-11-30
Check the contents of *~/.config/user-dirs.dirs* . XDG_DESKTOP_DIR may be set incorrectly.

---

### Post by spadewarrior on 2012-12-06
Excellent. That solved it. Thanks very much!

---

