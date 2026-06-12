---
title: "Theme switches when changing between ubuntu and other OS"
date: 2012-06-01
forum: Desktop Environments
---

### Post by kiro23 on 2012-06-01
Hi guys, 

I am multibooting between Ubuntu 12.04 (Unity), Opensuse 12.1 (GnomeShell) and Win7 and have a problem with the GTK theme, cursor theme, icons and window decorations getting messed up after I change it in the other Linux OS. 

For example, if I start in Opensuse, everything looks fine, then the next time I startup Ubuntu the GTK theme, cursor theme, icons and window decorations will revert to a Gnome 2-ish theme and when I check the appearance settings they are blank. 

I can change the theme back to ambiance fine, but then Suse will look like it doesn't know what theme it's supposed to have. 


Any thoughts on how to fix this? 

As a side note, i should add they are both on separate partitions with a shared home partition.

---

### Post by Cheesemill on 2012-06-01
You have this problem because you are sharing a /home directory between different distros.
This is never a good idea because the configuration files of different distros aren't necessarily compatible with each other and will conflict, causing your issue.
The only fix I can think of is to use separate home directories.

---

### Post by kiro23 on 2012-06-02
I see... That's the thing I was trying to avoid. I guess it'll just be switching themes whenever I boot into the other one...

---

### Post by vasa1 on 2012-06-02
> **kiro23 said:**
> I see... That's the thing I was trying to avoid. I guess it'll just be switching themes whenever I boot into the other one...
But you should really consider the advice given by Cheesemill.

---

