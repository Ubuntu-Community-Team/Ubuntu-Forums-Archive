---
title: "Nautilus really slow to launch"
date: 2008-04-04
forum: Desktop Environments
---

### Post by bkline on 2008-04-04
Any tips for eliminating the excessive sluggishness when opening up Nautilus?  I saw the post suggesting disabling of assistive technologies if that's turned on, but it isn't.

Gnome/Nautilus 2.20 on gutsy on i686

Thanks.

Bob

---

### Post by bkline on 2008-04-07
I'm not really certain of the cause and effect relationship, but it appears that the sluggishness problem has been resolved.  I ran "ls -a ~|wc" to see if Nautilus was trying to gather information on a ton of files (even though is doesn't show the hidden files), but there weren't much more than 100 entries in the directory listing, even including the .* entries.  So then I ran "ls -la" for a closer look and noticed that a few were owned by root instead of the normal user account).  So I ran "chown" to take back ownership on those, and now the problem seems to be gone.  No idea why, but perhaps this will help someone else with the same problem

---

