---
title: "Steam games location"
date: 2013-10-18
forum: Gaming &amp; Leisure
---

### Post by dannyboy79 on 2013-10-18
Has anyone tried to use an NFS or SAMBA share to store and play their steam games from? Currently my games are located in the default location which is ~/.local/share/Steam and my home partition is very small. I have read that I can just close steam, move the entire Steam folder to another drive/partition and then symlink to it BUT I am wondering if it would work over a 100Mbit LAN using an NFS or SAMBA share? If not I can understand that the write/read speed is just not up to par to play a game over my LAN but I also want other's feedback about the symlink solution to moving ones steam games to another partition.

If the LAN idea won't work, do you think a USB2.0 connected drive formatted as ext4 would suffice?

---

### Post by Ranko Kohime on 2013-10-21
I'm not sure how Steam handles it's files disappearing.  Which is something that occurs in my experience with Samba.  (The mount point just sometimes randomly unmounts itself, most common with high activity).

I've not had the same problem with NFS.

And I think a USB2 drive would be fine, but very slow to launch.  (Steam seems to do a fair amount of grinding on startup)

---

### Post by dannyboy79 on 2013-10-21
i ended up settling with symlinking ~/.local/share/Steam to an external hard drive formatted as EXT4 and it does take a moment for steam to start up but games play fine from it. I'll mark it solved.

---

