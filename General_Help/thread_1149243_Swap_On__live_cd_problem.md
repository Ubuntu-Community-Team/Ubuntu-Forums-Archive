---
title: "Swap On / live cd problem"
date: 2009-05-05
forum: General Help
---

### Post by gibxam on 2009-05-05
Hello Ubuntuers,

I have two pretty quick questions. The first: I have two Ubuntu distros on my HDD, and I only use one swap partition for both of them. Someone told me that Ubuntu will automatically start using the swap but once I boot into Ubuntu and start gparted, it lets me turn the swap partition on. Shouldn't it already be on? This is my fdisk output:
```

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        4831        9726    38941560   83  Linux
/dev/sda2               1        4366    35110026   83  Linux
/dev/sda3            4367        4830     4072477+  82  Linux swap / Solaris

Partition table entries are not in disk order

Command (m for help): 

```

Second: I was showing my friend how to boot from the Live CD from a removable cd drive and while I was shutting down Ubuntu he turned off the CD drive causing multiple errors in the shutdown process. Now, it might just be me but I swear Ubuntu takes much longer to boot up and I am blank screened for a good 15 seconds before the login prompt. Is this related? Is there even a problem?

Thank you for any help.

Max

---

### Post by kpkeerthi on 2009-05-05
You need to add an entry to /etc/fstab so it is automatically recognized on boot.

From the fdisk output, it appears that /dev/sda3 is your swap partition.
1. Find the UUID of sda by running this command:
```
sudo blkid
```
* It should look like 3f8c5321-7181-40b3-a867-9c04a6cd5f2f
2. Backup fstab```
sudo cp /etc/fstab /etc/fstab.backup
```
3. ```
gksudo gedit /etc/fstab
```
4. Add this line to the end of the file - [COLOR="Red"]change UUID to what you found in Step 1[/COLOR]:
```

UUID=3f8c5321-7181-40b3-a867-9c04a6cd5f2f   swap  swap  defaults  0  0

```
5. Save and exit.
6. **Reboot**

If you face issues, you can restore the backup:
```
sudo mv /etc/fstab.backup /etc/fstab
```

---

### Post by gibxam on 2009-05-05
Terrific thank you kpkeerthi that solved my swap problem :)

---

### Post by gibxam on 2009-05-05
Is there anything I can do besides run memtest that would check if shutting down my computer wrong has done any damage?

---

### Post by gibxam on 2009-05-05
*bump :)*

---

