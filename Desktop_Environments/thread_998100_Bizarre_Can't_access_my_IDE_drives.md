---
title: "Bizarre: Can't access my IDE drives"
date: 2008-11-30
forum: Desktop Environments
---

### Post by 4dummies on 2008-11-30
I've got a mix of SCSI and IDE drives, with my Ubuntu stuff only on the SCSI, and grub, Windoze and a few other things on IDE.

I just noticed I cannot access my IDE drives once I'm in Ubuntu.  This makes no sense.  They're essential to the bootup process, and I can boot to 2 different flavors of Windoze if the urge overtakes me.  But somewhere along the line, Ubuntu decides there's a conflict in what I think are the port numbers for access.

This is an old P-III machine, a mix of ISA and old PCI bus, with everything currently PCI.

Any ideas how to get it back?

++ kevin

---

### Post by taurus on 2008-11-30
Open a terminal and post the outputs of these commands.

```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by 4dummies on 2008-11-30
Here it is (attached).

---

