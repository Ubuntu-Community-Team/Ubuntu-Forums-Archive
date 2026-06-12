---
title: "how to safely remove a usb stick"
date: 2014-04-30
forum: Desktop Environments
---

### Post by ErikMAkkerman on 2014-04-30
In ubuntu 12.04 there was a pop-up-menu-item "safely remove".
In ubuntu 14.04 I only see "eject".
Observing that my usb-stick keeps on blinking for a while, after
having ejected it, I conclude that this is not a "safe" eject.

Where has the "safely remove" command gone?
How can I add it again?

Erik

---

### Post by sudodus on 2014-04-30
when you 'eject' a pendrive, the action 'behind the curtain' is unmounting the partition(s) on the usb drive. It may also switch it off completely. The unmount command will first make a sync command to flush buffered data to the drive (the flash memory), and then unmount it (so that it will not be available for read/write operations. When you see it blinking, it is busy flushing data to the drive. It may take time, because a pendrive is usually much slower compared to hard disk drives and SSDs.

So do not unplug the drive while it is blinking.

If you want to be quite sure, look behind the curtain with terminal window commands.

Run ```
sudo parted -l
``` and ```
df
``` to identify the mounted partitions.

Example:
```
[COLOR=#0000ff]sudo [/COLOR][COLOR=#0000ff]parted -l[/COLOR]
...
Model: Kanguru SS3 (scsi)
Disk /dev/sdd: 15.9GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system     Flags
 1      1049kB  3664MB  3663MB  primary  ext4            boot
 2      3664MB  3999MB  336MB   primary  linux-swap(v1)

[COLOR=#0000ff]df[/COLOR]
Filesystem     1K-blocks      Used Available Use% Mounted on
/dev/sdb5       53527044  29404572  21403448  58% /
...
/dev/sdc7      880870988 370228920 465896392  45% /media/multimed-2
/dev/sdd1        3520656   1103644   2238172  34% /media/Trusty-B1-nonpae

```


Flush the buffers with ```
sync
```

When everything is flushed the terminal window returns to prompt (in my case [COLOR=#008000]sudodus@ssd-grund[/COLOR] **[COLOR=#0000cd]~[/COLOR] $**)

Now you can unmount the partition quickly (in this example  **/dev/sdd1** mounted on **/media/Trusty-B1-nonpae**)

```
sudo umount /dev/sdd1
```

and it is ready for unplugging.

If you skip the sync command, unmounting will be slower, because it has to do the flushing before it can finish. Wait until the command finishes and the terminal window returns to prompt.

-o-

If you use the eject button in your file browser, and wait for the process to finish, it is also safe to unplug the pendrive.

---

