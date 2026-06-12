---
title: "RAID HDD increase"
date: 2009-04-15
forum: General Help
---

### Post by halcyonhell on 2009-04-15
Hi there. I'm new to the forums. I have a little problem. I have a file server with 2X 320GB HDD in a hardware RAID 1 array. I want to replace them with 2X 500GB HDD. I sit with the problem of the logical volume staying 320GB. The server has Ubuntu 7.04 X86 running (Q laughter). I have very little xp with Ubuntu therefore i seeked help from a friend to install everything the first time. Of course i wasn't taking notes. Anywho, I won't have the time to reinstall everything and setup Samba, ect... I can't afford any down time. What must I do to get full usage of the 500GB HDDs in the RAID without having to do everything over? Oh yes its a Intel board (S5000VSASATA). Thanks in advance!!!!

---

### Post by JochenJung on 2009-04-16
Depends on the Raid adapter you are using. But most Raid adapters I know use the size of the smallest disk in the array, which does not increse if you replace them with larger disks.
You have to create a new array. If you don't want to reinstall, you have to attach all 4 disks to the adapter and move the data to the new created array.

---

### Post by halcyonhell on 2009-04-21
thanks JochenJung. Will i be able to remove the 320GB hdds then, and will the new RAID array take over?

---

