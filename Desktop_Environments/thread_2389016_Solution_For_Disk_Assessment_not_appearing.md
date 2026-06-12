---
title: "Solution For Disk Assessment not appearing"
date: 2018-04-10
forum: Desktop Environments
---

### Post by jman17712 on 2018-04-10
You may have noticed "Asessment" missing from all or some of your SATA drives inside "Disks" section.

The solution was to access BIOS & disable "External SATA" on all disks + also confirm S.M.A.R.T is enabled in BIOS.

(By default "External SATA" is enabled on most motherboards which breaks it)

You can still have "Hot Plug" enabled as this doesn't appear to affect S.M.A.R.T on Ubuntu.

(I had two different PCs an i5 & AM2+ this solution worked on both PCs which were running buntu 16.04.3 LTS version)
Let me know if this helped :-)

---

