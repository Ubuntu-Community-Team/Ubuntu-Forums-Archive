---
title: "If I were to boot into Hardy Heron on any given..."
date: 2009-03-29
forum: General Help
---

### Post by r0g on 2009-03-29
...Windows system with an NTFS drive, mount that drive and create a samba share of it and then mount that share on another Ubuntu machine and tell rsync to copy it to a folder on that machine...

Are there any files that might not get read? and more importantly...
Assuming I use --progress, if it does try to read a given file /folder and it fails, will I definitely get a message/warning to let me know?


At the moment I back up windows systems by physically removing their drives, hooking them up to a clean XP system and using Y-copy which grind away copying everything it can and generates a report of what files/folders it couldn't copy in the process. I need to do this on a regular basis so I'd rather do it via the network instead, and I'd far rather work in a Linux environment too, but I need to be certain that nothing has been missed. It's no biggie if a particular file or folder won't copy but it's really REALLY important to know that it hasn't.

Will theprocess I descibe at the beginning give me that? or are their potentially silent fail modes or other ways things can be overlooked / missed?

Cheers,

Roger.

---

