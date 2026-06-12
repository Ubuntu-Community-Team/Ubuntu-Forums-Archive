---
title: "Serious partition problem!!!"
date: 2009-02-25
forum: General Help
---

### Post by upapilot on 2009-02-25
OK
I had only Ubuntu installed on my PC. Then i decided to install microsoft windows xp. After installing it, i found that the GRUB menu has disappeared and XP boots up automatically. So i decided to reinstall Ubuntu and delete the old Ubuntu partitions. But when i opened the partition editor via, the CD, it showed that the entire disk was unallocated. Please help me out.
Thanks;)

---

### Post by caljohnsmith on 2009-02-25
It sounds like your partition table is probably corrupt, because that often happens after installing Windows to a drive that has linux partitions. How about posting the output of:
```
sudo fdisk -lu
sudo sfdisk -d
```
And we can work from there.

---

### Post by upapilot on 2009-02-26
You don't get it do you? THERE IS NO UBUNTU TO TYPE THOSE COMMANDS!!!!:mad:

---

### Post by caljohnsmith on 2009-02-26
> **upapilot said:**
> You don't get it do you? THERE IS NO UBUNTU TO TYPE THOSE COMMANDS!!!!:mad:
I apologize for not being more explicit: I meant you could run those commands from the Live CD, but if that is your attitude, you are welcome to wait for someone else to offer their help.

---

