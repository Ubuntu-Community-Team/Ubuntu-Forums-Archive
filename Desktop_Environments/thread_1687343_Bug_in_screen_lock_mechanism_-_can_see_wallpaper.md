---
title: "Bug in screen lock mechanism? - can see wallpaper"
date: 2011-02-13
forum: Desktop Environments
---

### Post by justsomelinuxnoob on 2011-02-13
Step 1: Run Ubuntu 10.10 with all updates installed.
Step 2: Lock the screen
Step 3: Shake the mouse etc to bring up the password entry dialog

---> Before the dialog pops up on the black screen, the wallpaper/background flashes. This allows an unauthorized user to see the user's wallpaper without knowing the unlock password. Depending on the nature of the wallpaper, (i.e. if it contained a network diagram for your enterprise for easy reference), this could become a security risk.

Questions:
1. Where is the best place to report this bug, if it is one?
2. Can anyone else reproduce it? Do you see your wallpaper before you type in the pw at the lock screen?
3. I'm using 2 screens on a dual core laptop with an nvidia card using twinview. Would this have any bearing at all on the wallpaper `bleeding through`?

---

### Post by justsomelinuxnoob on 2011-03-12
Anyone?

---

### Post by Toxicbits on 2011-03-12
You should report the bug in Launchpad: [https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver](https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver)

---

