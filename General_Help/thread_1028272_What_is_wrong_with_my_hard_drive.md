---
title: "What is wrong with my hard drive?"
date: 2009-01-02
forum: General Help
---

### Post by seks2 on 2009-01-02
Ubuntu, grub, and gparted live do not recognize and cannot read my secondary hard drive unless I set it to first boot priority in BIOS. If the main HDD has boot priority (or I boot from a cd), it isn't recognized at all. It's like it doesn't want to be seen unless the system relies on it. Please Help!

Example: I boot into a live CD and open GParted. Only my primary HDD is shown under "devices" regardless of BIOS boot settings or which sata port I have it plugged into. It's an older sata-150 drive, if that helps.

---

### Post by wmdiem on 2009-01-02
donno what it is. Do they show up in /dev/disk/by-path ?

---

### Post by seks2 on 2009-01-02
the output of "ls /dev/disk/by-path" is (last 3 put in new lines for clarity)

pci-0000:00:0f.0-scsi-0:0:0:0        
pci-0000:00:0f.0-scsi-0:0:0:0-part1  
pci-0000:00:0f.0-scsi-0:0:0:0-part2  
pci-0000:00:0f.0-scsi-0:0:0:0-part3
pci-0000:00:0f.0-scsi-0:0:0:0-part5
pci-0000:00:0f.1-scsi-0:0:0:0
pci-0000:00:0f.1-scsi-0:0:1:0

No external media has been plugged in since the last reboot, and my primary disk only has 3 partitions(/, /home, and swap). Both drives are sata, but recognized as scsi because my controller is old. Theres a glimmer of hope here :)

---

