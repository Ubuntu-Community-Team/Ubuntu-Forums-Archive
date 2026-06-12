---
title: "maintenance commands?"
date: 2005-04-15
forum: Desktop Environments
---

### Post by pruett57 on 2005-04-15
Okay, so I've installed, tweaked, removed, tweaked out my system is there any maintenance I should/can do?

I know apt-get autoclean but I'm talking (from an MS point of view) Defrag, scandisk, delete files in the temp (tmp) folders. etc to make my system run a little better?

Thanks,

jp

---

### Post by Alexander Kirillov on 2005-04-15
[QUOTE=pruett57]Okay, so I've installed, tweaked, removed, tweaked out my system is there any maintenance I should/can do?

I know apt-get autoclean but I'm talking (from an MS point of view) Defrag, scandisk, delete files in the temp (tmp) folders. etc to make my system run a little better?

Thanks,

jp[/QUOTE]
 Defrag and scandisk are not needed for ext2/ext3 filesystems. Temp files should be deleted automatically, via cron job - normally you do not have to do anything. 

So if you have tweaked the system to your liking, the only thing you should do is to get  updates periodically - and enjoy.

---

### Post by Stormy Eyes on 2005-04-15
[QUOTE=pruett57]I know apt-get autoclean but I'm talking (from an MS point of view) Defrag, scandisk, delete files in the temp (tmp) folders. etc to make my system run a little better?[/QUOTE]

Don't worry about it. ext2/ext3 and other Linux filesystems (like ReiserFS) don't have the fragmentation issues FAT32 and NTFS do. Checking the filesystem for errors is done automatically at boot time, and cleaning out /tmp is also done automatically. Just relax and enjoy. Your Ubuntu isn't likely to break unless a component burns out as long as you don't meddle with things you don't understand.

---

### Post by heimo on 2005-04-15
As others have expressed, Linux is quite boring compared to Windows from maintenance point of view. ;) But you still should make sure that routine tasks are taken care of - backups for instance. Occassionally looking in /var/log/ helps to find problems that may arise (/var/log/messages). Checking that disks don't fill up (df)...

I really can't imagine many tasks that are neccassary. Some Linux boxes seem to run forever when setup correctly. You can always set intrusion detection (for example tripwire), make sure that your firewall is running flawlessly (nmap port scanner) or compile a kernel for just the kicks. :D That's what I do when I get bored and miss the days of daily defragging. Or fire up tuxracer for some "maintenance" while Windows admins are installing latest security patches and service packs.

EDIT: > I know apt-get autoclean  And to be a good unix admin, you should script (automate) everything that's done routinely. Learning some bash scripting or perl programming is a major project of its own, if you're interested in such. Or get more involved in community work, helping others, testing applications, filing good bug reports and so on! :) But make sure that you enjoy it. :D

---

