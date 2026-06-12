---
title: "can only see firewire disk when logged into gnome"
date: 2007-07-13
forum: Desktop Environments
---

### Post by finite9 on 2007-07-13
I log into gnome and can see my firewire external drive ok, but if I do not log into gnome, and press ctrl-alt-F1 to get to a terminal, I log in but cannot see /media/disk/ where the firewire disk is usually mounted.

I need this to work as a server, and I do not log in.  How do I make my external disk mount at boot?

---

### Post by finite9 on 2007-07-17
never mind, somoeone else pointed out that runing fdisk -l will show all my discs, and I could then identify the device name of the firewire disc and mount it from the CLI.

---

