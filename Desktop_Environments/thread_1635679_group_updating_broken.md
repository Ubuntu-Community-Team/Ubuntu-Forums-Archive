---
title: "group updating broken"
date: 2010-12-02
forum: Desktop Environments
---

### Post by cromestant on 2010-12-02
Hello, 
I ve been trying to see why this is happening, but can't seem to put my finger on it.

I recently had to add my user to a group, I did so in a few ways; like editing the /etc/group file directly, and with the usermod command.

Opening the user/group admin utility in gnome showed that the user was in fact in the group, however the terminal emulator on gnome did not show the group (even after close and reopen).

In gentoo I used to do env-update (or open and close the terminal emulator) and it would reflect the changes.

Switching to the F1 terminal and logging into the user did show the changes, but in the terminal emulator in gnome still nothing; I had to log out and relog into gnome in order to get this to work

Is it broken or am I doing something wrong?

btw this is 10.10

---

