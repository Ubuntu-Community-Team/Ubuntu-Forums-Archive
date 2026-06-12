---
title: "Dual Boot Windows and Ubuntu (Ubuntu installed first) issues"
date: 2012-03-02
forum: Desktop Environments
---

### Post by Scopic on 2012-03-02
Hi there!

I am attempting to dual boot Windows HPC Server 2008 on my existing  Linux(Ubuntu) HPC machine. I know that Windows will wipe the MBR and I  have the Ubuntu LiveCD to restore GRUB when that happens, but I am  having some trouble with my disk partitions.

As of right now, when I boot into the Windows installation, it shows no  disks available to install onto. I ran 'diskpart' and it returned with  "There are no fixed disks to show." I made sure to use GParted to  partition the main (sda2) drive in half and format the unallocated space  to an NTFS partition, yet Windows still refuses to see it!

I am at a loss, I have absolutely no clue why it is not recognized. The  BIOS sees it, Ubuntu sees it, but Windows is standing blind. Any ideas?

I tried deleting the partition and just leave it as unallocated space, but Windows still didn't pick it up. My drives currently look like this:

/dev/sda1 bios_grub
/dev/sda2 ext4
/dev/sda4 unallocated
/dev/sda3 linux-swap

Very curious as to why this is happening, any help would be great. Thanks!

---

### Post by oldfred on 2012-03-02
You show bios_grub which is used with the newer gpt partitioning. Windows only works with gpt on new systems with UEFI booting. You then have to have an efi partition as the first partition.

You can add another MBR partitioned drive or if you really want Windows you have to convert back from gpt to mbr. If drive is over 2.2TiB then you only can have a 2.2TiB drive in MBR.

If you really have MBR, did you set boot flag on the NTFS partition?

---

### Post by Scopic on 2012-03-02
I may have been incorrect in saying that I have a MBR. The drive is  larger than 2.2TB (3.0TB) and all of it is detected in Ubuntu.

Also, I executed the **fdisk -l** command and received this:

```
WARNING: (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.

~information about the disk itself~

Device Boot
/dev/sda1

(other information about sda1)                      
```It only shows that 'device', sda1. In GParted, though, it shows sda1,  sda2, sda3, and sda4. In any case, I believe I am using GPT judging from the above message. Is reverting to MBR the only way to use Windows? Could you explain further please? I am hoping to preserve the current data on the main Ubuntu partition if possible.

Thanks again.

---

### Post by Scopic on 2012-03-02
RESOLVED:

I found that the HDD's were connected to an LSI RAID Controller which needed necessary drivers during the Windows install. I copied them to a flash drive and loaded them up during installation and Windows sees everything now!

Thanks for all the help and hopefully this can help others! :D

---

### Post by oldfred on 2012-03-02
That worked with gpt. They have said you cannot install Windows in gpt unless UEFI. So this must be a work around.

---

