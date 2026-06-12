---
title: "accessing existing Windows RAID 5 on HP Smart Array P410"
date: 2020-12-26
forum: Desktop Environments
---

### Post by blfager27 on 2020-12-26
I am new to Linux/Ubuntu and have something I need help on before I mess anything up. I currently have a media server (Windows 10 Pro) with an HP Smart Array P410 RAID card. I have four 4TB mechanical drives in a RAID 5 array. I would like to switch this over to Ubuntu 20.04 LTS. The installation on the system should be easy enough, but i want to make sure i can access that array in Ubuntu. I do not really want to wipe the array and reload. I would also PREFER keeping the current file structure intact. I did find information about "[COLOR=#111111][FONT=monospace]hpsa - HP Smart Array SCSI driver" ([/FONT][/COLOR]http://manpages.ubuntu.com/manpages/cosmic/man4/hpsa.4.html) but i'm hesitant to poke around for fear of losing everything. any assistance would be highly appreciated

Brian

---

### Post by ActionParsnip on 2020-12-27
Make sure that you run a final fill backup before you do anything (if the data is important to you). Great first step. Then verify that you can restore files from the backup you took.

---

