---
title: "Dpkg wrecked, no installs or uninstalls allowed."
date: 2006-09-16
forum: Desktop Environments
---

### Post by NMUrugbysteve on 2006-09-16
So the other day my computer was thrown into a loop and I had to do a hard restart. I started it back up and my /etc/apt/sources.list was for some reason replaced with my fstab!! I fixed that because I had a back up of my sources. Then however, I found out that I couldn't use dpkg, even on the simplest levels. I kept getting errors about the /var/lib/dpkg/available being messed up, but I have no idea how that file works or what to do with it. The first error was "dpkg: parse error, in file `/var/lib/dpkg/available' near line 1:
 field name `<?xml' must be followed by colon"

---

### Post by hajk on 2006-09-19
This happens sometimes, but luckily there is a fix: 

1. Remove the offending file with "sudo rm /var/lib/dpkg/available".

2. Run the command: "sudo dselect update", which will make a new available file.

---

