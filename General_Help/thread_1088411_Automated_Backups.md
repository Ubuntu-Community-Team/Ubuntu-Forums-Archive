---
title: "Automated Backups?"
date: 2009-03-06
forum: General Help
---

### Post by Roasted on 2009-03-06
I currently have a bin/bash script that rsync's several things on my computer. I have 4 drives in my computer, 500gb/500gb and 250gb/250gb.

I use the first 500gb drive, and the 2nd 500gb drive is an rsync'd copy of the first.

The first 250gb drive is a network drive using samba which other users in my house (parents and brother) use a windows xp program to automatically back up to their designated share.

The 2nd 250gb drive is an rsync'd copy of the first 250gb drive.

All I have to do is type sudo backup. No biggie. The script works fine. But is there a way to automatically make this thing run automatically at a given time?

I know crontab exists, but I'm looking for something else. Maybe grsync? Will that run automatic backups? I know all it is is a frontend for what I'm already doing in my script, but if it does it automatically it does it automatically.

EDIT - Also, just to throw out there... for my Ubuntu laptop, how would I set up rsync to run across the network to my home directory on my Ubuntu desktop?

---

### Post by Roanoke on 2009-03-06
Why won't cron do? It's the best tool for this that I know of.
As for the network thing, I have no clue, try checking the rsync manual.

---

### Post by amac777 on 2009-03-06
About using rysnc accross a network, it is easy if you have ssh installed on one of the computers. For example this command will copy (synchronize) the ~/Pictures directory on the local computer to /media/backups on the server:

```
rsync -azve ssh --delete ~/Pictures username@server:/media/backups
```

in that command the -azve means (a) recursively go down the source directory and keep all time stamps and permissions the same, (z) compress the information while being transferred across the network, (v) display verbose information about which files are currently being copied, and (e ssh) use ssh. The --delete means to remove files on the destination that are no longer found on the source. Username should be a user the user who has ssh access and permission to the backup folder on the server, and server is the ip address or server name on the network.

Of course, that command can be modified for any directory or computers on the network.

---

