---
title: "Display jumbled - appears woven"
date: 2012-02-10
forum: Desktop Environments
---

### Post by SteveKier on 2012-02-10
I'm running Ubuntu 11.10 (oneiric), Gnome version 2.32.1.

What happens to me is, after the machine has been up a while (maybe minutes, maybe hours), the display becomes jumbled.  The "jumbling" presents the appearance of weaving.  That is, it looks like two small adjacent squares of the overall screen image have been swapped - painted in each other's places.  But it repeats over the whole screen, eventually making the whole thing unusable and I have to reboot.

The corruption sometime starts just on the desktop background, and windows and icons float on top of the corrupted image, getting painted correctly.  But eventually it always creeps inside of the windows.  Characters in text get corrupted and unreadable.  That's when I have to reboot.

Anybody have thoughts on what's going wrong?

Thanks,

Steve

---

### Post by jerrrys on 2012-02-10
Open a terminal and enter:

top

This will let you monitor your top 10 processes and see if any process is eating up memory.

Look for xorg

Also what kind of computer is this and video do you have?

---

