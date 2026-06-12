---
title: "Other Partitions Show Up on Desktop"
date: 2007-06-22
forum: Desktop Environments
---

### Post by M249-M4A1 on 2007-06-22
Hi, when I installed Ubuntu 7.04, there were a couple icons placed on my desktop that corresponded to my Windows XP paritions.  I can't unmount them or anything by means of right-clicking them and clicking Unmount. I have also checked the help topics that related to mounting and unmounting stuff (Sorry, it's late and I can't think of the word).

So my question is, how can I get rid of those icons from my desktop? I don't want to be able to access my other partitions, at least from the desktop itself.

- Thanks!

---

### Post by merlinus on 2007-06-22
Partitions have to be unmounted as root.  You can do this in a terminal.

For example:

```

sudo umount dev/sda1

```

To not have them show up as icons on your desktop:

Alt-F2
gconf-editor
apps/Nautilus/desktop

Uncheck volumes visible

-merlin

---

### Post by M249-M4A1 on 2007-06-22
Perfect, thank you VERY much!!!

---

