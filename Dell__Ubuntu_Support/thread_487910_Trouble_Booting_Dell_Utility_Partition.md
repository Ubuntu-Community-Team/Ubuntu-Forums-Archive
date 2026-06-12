---
title: "Trouble Booting Dell Utility Partition"
date: 2007-06-29
forum: Dell  Ubuntu Support
---

### Post by thetictacaddict on 2007-06-29
I have a new Inspiron E1505N with Ubuntu from Dell.  I'm trying to boot the dell utility partition so I can check my system fans, but I get stuck at  EULA screen.  There are two ways to get to this.

1) I go to the boot menu and select "Diagnostics".  Some diagnostics run, then I get a message that says "Booting the Utility Partition" and next I see a EULA notice.  I press a key to accept it, but the screen flashes black and the EULA notice pops right back up.  I'm stuck until I power off or hit ctrl+alt+delete to restart.

2) I added the utility partition to GRUB.  When I boot, it goes straight to the EULA notice.  If I hit a key I get dumped back to GRUB again.  It will time out and boot Ubuntu after 3 seconds unless I quickly press escape.

Dell tech support hasn't been able to help me with this so far.  Has anyone else tried to boot the Dell utility partition, and has it worked?

---

### Post by whizbaby on 2007-06-29
Its the first thingy we usually remove while partitioning...
Is there something you could probably need that for?

---

### Post by neptho on 2007-06-29
This *may* work, but I haven't tested it.

Boot into Ubuntu Recovery (press 'esc' at loading screen, choose 'Recovery')

Once you are at the root prompt, run 'fdisk /dev/sda'
```
#fdisk /dev/sda
```

Type 'p' to get your partition scheme, it's likely different than mine, but here's mine as an example:
```
   Device Boot      Start         End      Blocks   Id  System
**/dev/sda1               1           6       48163+  de  Dell Utility**
/dev/sda2               7        1312    10490445   83  Linux
/dev/sda3            1313        1513     1614532+  82  Linux swap / Solaris
/dev/sda4   *        1514       12161    85530060   83  Linux
```

For me, it's partition number 1.  It's not set bootable, so set it bootable with 'a'

```
Command (m for help): a
Partition number (1-4): 1
```

Verify you did it properly:
```
   Device Boot      Start         End      Blocks   Id  System
**/dev/sda1   *           1           6       48163+  de  Dell Utility**
/dev/sda2               7        1312    10490445   83  Linux
/dev/sda3            1313        1513     1614532+  82  Linux swap / Solaris
/dev/sda4   *        1514       12161    85530060   83  Linux
```

Press 'w' to save changes, and exit.

```
Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 16: Device or resource busy.
The kernel still uses the old table.
The new table will be used at the next reboot.
Syncing disks.
```

Sync changes and reboot, then try again.

```
#sync;sync;sync;reboot
```

Good luck!

---

