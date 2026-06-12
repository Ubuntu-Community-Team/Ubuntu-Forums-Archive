---
title: "Disk failure imminent"
date: 2011-10-13
forum: Desktop Environments
---

### Post by nitromx7 on 2011-10-13
I have a SEAGATE 1TB HD that is failing after 1 year of use. I have backed up the bad HD and reinstalled a new one. Is the bad one repairable with SW or terminal commands that is available from Ubuntu? I tried to reformat with DISK UTILITY and was unsuccessful. I tried GParted but it would not read the drive. Terminal/Command line recognizes the HD though.

I attached a few screenshots.

My intent is two fold:
1: Repair the HD if possible but I need help with the solution and I do not want to purchase software to do this like SPINRITE6.
2: If unable to repair, I will send the HD back to SEAGATE, but I want to erase all data from the HD first. How do I do that from terminal window? I am new to LINUX/UBUNTU

Thank you

---

### Post by mcduck on 2011-10-13
Bad sectors are physical errors on the disc platter surface, not something you could repair by any means, and definitely not with software.

To erase all data on the disc you could use the *dd* command:

```
dd if=/dev/zero of=/dev/sdf bs=1M
```
Make *absolutely* sure you have the correct device name in the *of* field, the command will erase all data on the device so using wrong device name would have really bad results.

It will take quite a while to write through the 1TB drive. You'll know that dd has finished when it returns back to normal terminal prompt.

---

