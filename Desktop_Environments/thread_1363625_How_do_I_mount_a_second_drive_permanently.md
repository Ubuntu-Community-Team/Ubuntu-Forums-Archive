---
title: "How do I mount a second drive permanently?"
date: 2009-12-24
forum: Desktop Environments
---

### Post by Maheriano on 2009-12-24
I boot Ubuntu from a terabyte SATA drive and I also have a smaller IDE drive for backups. I'm trying to schedule CRON to automatically back up my important folders every day onto the second drive but it errors because the drive has to be mounted manually before CRON can access it. How do I set my second drive to mount permanently and never ask for a password?

---

### Post by taurus on 2009-12-24
Look in System -> Administration -> Disk Utility.

---

### Post by Maheriano on 2009-12-24
That doesn't give me any mounting options. Just to change the file systems.

---

### Post by taurus on 2009-12-24
You can always edit /etc/fstab by hand and add an entry in there for your second harddrive.  You can either use the old method, /dev/sdXX, or you can use a better way with UUID.

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/fstab
```
Don't forget to create a mount point or it won't be mounted.

---

### Post by Morbius1 on 2009-12-24
Use something like this as a template:

(1) Create a mount point for the partition in your home directory

Open **Terminal**
Type **mkdir /home/morbius1/Backup**

[COLOR=Blue]*Change morbius1 to your own user name*[/COLOR]

(2) Create an entry in fstab that will mount the partition at boot

Open **Terminal**
Type **sudo su**
Type **echo "/dev/[B]sdxx** /home/**morbius1/Backup** ext3 defaults,noatime 0 2" >> /etc/fstab

[/B][COLOR=Blue]Replace sdxx with the actual device[/COLOR]
[COLOR=Blue]I'm assumming the partition is ext3, substitute ext4 above if it's ext4
You'll need a different entry for FAT32 or NFTS - so let us know[/COLOR] [COLOR=Blue]if that's[/COLOR] [COLOR=Blue]the case[/COLOR]

(3) Reboot the system

(4) Fix the ownership of the mount point and it's contents

Open **Terminal**
Type **sudo chown -R morbius1:morbius1 /home/morbius1/Backup**

---

### Post by falconindy on 2009-12-24
> **Morbius1 said:**
> (3) Reboot the system
This isn't Windows. Running `sudo mount -a` is sufficient.

---

### Post by Morbius1 on 2009-12-24
No it isn't because I don't know what he has mounted and what he doesn't.

---

### Post by falconindy on 2009-12-24
> **Morbius1 said:**
> No it isn't because I don't know what he has mounted and what he doesn't.
I'm not sure you understand what the -a flag does. Regardless of how its accomplished, you never need to reboot just to mount a new drive added to /etc/fstab.

---

### Post by Morbius1 on 2009-12-24
> **Mounting all filesystems**

 mount -a
This command will mount all (not-yet-mounted) filesystems mentioned in fstab and is used in system script startup during booting.


I do not know at this exact moment what he has mounted and what he has not mounted. Without me standing behind him the best thing would be to do a reboot. If either one of us were there this would be a non-issue.

---

### Post by falconindy on 2009-12-24
'mount -a' is called during the boot process. I'm not sure what you're afraid of. No one's dog is going to get set on fire. If anything, OP might find out that he typed something wrong and he'll know that immediately rather than having to reboot and find that his drive still isn't mounted for reasons he may not immediately discern.

---

