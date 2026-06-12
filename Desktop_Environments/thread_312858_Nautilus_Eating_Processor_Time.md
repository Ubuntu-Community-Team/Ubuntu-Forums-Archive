---
title: "Nautilus Eating Processor Time"
date: 2006-12-05
forum: Desktop Environments
---

### Post by gerowen on 2006-12-05
I've noticed in the past little bit that for some reason nautilus will randomly just start using a large portion of my processing power.  I haven't really been able to pin-point any clear events that lead up to it, so I was wondering if anybody else is having the issue.  It will be using like 0% of my CPU one minute, and then I'll start noticing programs lagging, and when I check it's because nautilus is using 80+% of my CPU.  Logging out and back in solves it, or just killing nautilus and letting it restart on its own, but I'd like to stop the issue altogether.

---

### Post by zgornel on 2006-12-05
Probably just bugs. :???:

---

### Post by gerowen on 2006-12-05
I've noticed that it happens when I try accessing my 80 GB Seagate External hard drive.  I formatted in FAT32 so both Linux and Windows could read/write to and from it, and when I access it the CPU usage for nautilus goes up.

---

### Post by zgornel on 2006-12-06
You should have left it ext3. For accessing ext3 partitions (i think in read-only mode) I used the ext3fs plugin for Total Commander :D

---

### Post by gerowen on 2006-12-06
I never had it in ext3 but I just formatted it in ext3.  I'm moving some files into it via command line for backup because nautilus still goes on crack every time I try to use it to browse the disk.  I can't even make a new folder.  If I do it doesn't ask me to name it, it leaves it as "unnamed folder" and when I try to name it I have like 2 seconds to do it in before it cancels and resets it to "unnamed folder" again.  This is "really" starting to get on my nerves.  I've never had this issue with thumb drives or anything.

---

### Post by gerowen on 2006-12-06
I've noticed that it doesn't happen if I have someone else browse it remotely(it's shared) from a Windows box, and other applications can access and use the device with no adverse effects, but as soon as I try opening the drive as a folder with nautilus, nautilus suddenly starts using like 80% of my processor time, even if I close the drive and unmount it, it continues to do this.

---

### Post by zgornel on 2006-12-07
Watch *dmesg* and */var/log/messages* for anything suspect. There might be something wrong although I suspect Nautilus is buggy.

---

### Post by gerowen on 2006-12-07
Wow, I fixed the issue.  I have an ext* driver installed on my Windows hdd so I can browse all my Linux partitions, and therefore my now ext3 external showed up.  I just renamed it so it wouldn't just say "Local Disk" or "usbdisk", and now Nautilus acts just fine when browsing it...

---

