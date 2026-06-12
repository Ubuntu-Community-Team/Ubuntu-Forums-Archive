---
title: "running nautilus seems to freeze gnome-panel"
date: 2009-01-20
forum: Desktop Environments
---

### Post by Jethro_uk on 2009-01-20
recently my 8.04 Ubuntu started acting weird. I finally pinned it down to a problem with Nautilus. Every time I load nautilus, it causes my gnome-panel to freeze. Killing gnome-panel seems to force it to restart and alls well.

I noticed theres an old bug [https://bugs.launchpad.net/ubuntu/+source/gnome-vfs2/+bug/11283](https://bugs.launchpad.net/ubuntu/+source/gnome-vfs2/+bug/11283) which seems similar, but is very old (and presumably fixed).

Anyone have any suggestions ? Weirdest thing is it started two weeks ago, after running stable since April. I deliberately haven't updated anything since then. After this problem started, I bit the bullet and upgraded, but it hasn't fixed it.

I won't go to 8.10, as I have an nVidia card, and my upgrade to 8.04 was very messy ....

---

### Post by Jethro_uk on 2009-04-02
I think I finally traced things to a shortcut I had in "bookmarks" which referred to a non-existent network location. Since I deleted it, things have been fine :-)

---

