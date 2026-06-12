---
title: "How do I work around KDE's headache of not being able to stream videos over Samba?"
date: 2013-08-24
forum: Desktop Environments
---

### Post by Roasted on 2013-08-24
In Gnome, I open Nautilus, CTRL + L, smb://ip.address.to.server, click video, it plays.
In KDE, I open Dolphin, CTRL + L, smb://ip.address.to.server, click video, fail.

This is seemingly due to some remaining issues in Kio as well as the lack of .gvfs. This makes me wonder... I'd like to get another KDE install going again so I can see what's new in recent revisions, but this problem is literally a 100% show stopper. I have a media center server with all of my content on it. I'd like to find a way to make this work, but if there's no way around it, this will be a dead end post. Any ideas?

---

### Post by bra|10n on 2013-08-25
I waited 4 years for the plasma-panel bug to be fixed.
Persistence is not futile...

---

### Post by SeijiSensei on 2013-08-25
> **Roasted said:**
> I have a media center server with all of my content on it. I'd like to find a way to make this work, but if there's no way around it, this will be a dead end post. Any ideas?

Use NFS to export the share.  I stream video from my NFS server to a Kubuntu 13.04 machine all the time.  I use **smplayer** as the video client.  I mount the exported share automatically at boot in /etc/fstab, then open the folder, double-click the file, and we're off.  I watch a lot of multi-episode anime programs and construct a playlist in smplayer.  It will keep track of which episodes you have watched and even where you are in a program if you stop viewing it before it ends.

---

