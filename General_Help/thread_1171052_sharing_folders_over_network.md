---
title: "sharing folders over network"
date: 2009-05-27
forum: General Help
---

### Post by drummerstiggs on 2009-05-27
I am very new to Ubuntu and have limited knowledge of how it works. I have recently crossed over from XP. Here is my current set up and issue. I have a tower dual booting xp and ubuntu. I perfer Ubuntu b/c it runs much faster. I plan on using this tower as a file server. I also have a laptop running xp that is networked with this tower.
 
I have installed an additional hard drive and formated it to FAT32 so I can use it on both OS. When running XP I can share the "storage" drive and access it on my laptop. When running Ubuntu, I am able to mount the "storage drive" and access the files with no issue, however I cannot access that drive from my laptop. I cannot figure out how to share the "storage" drive when it is mounted in Ubuntu.
 
If someone could help me with a step by step I would appreciate it.

---

### Post by drummerstiggs on 2009-05-27
any one?

---

### Post by Boondoklife on 2009-05-27
well if you are trying to share a particular folder, you can right click on it and goto sharing options. As far as an entire mounted drive, I only know how to do that by setting it up in the smb.conf file.

maybe if you share a folder on the drive you can look in smb.conf and change the entry to share the entire drive.

---

### Post by ActiveFrost on 2009-05-27
Install Samba : 
```
sudo apt-get install samba
```

Right click on your folder/partition/usb and click "Share" .. Enjoy :D

---

