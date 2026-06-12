---
title: "Mounting windows partition"
date: 2024-10-23
forum: Desktop Environments
---

### Post by AnupamMitra on 2024-10-23
In my PC there are two hard disks, one for Ubuntu 24.04 and the other one Windows 10 with NTFS file systems. Out of two partitions of Windows viz. sda3 and sda4, earlier it was possible to mount both the partitions from the left pane of the file manager. Nowadays I can't mount sda4. While I'm going to mount sda4 it shows "Failed to mount 104 GB Volume. Error mounting /dev/sda4 at/media/anupam/74EAAD22EAACE19A: wrong fs type, bad option, bad superblock on dev/sda4, missing codepage or helper program, or other error". How to fix it?

---

### Post by yancek on 2024-10-23
Linux will not mount an ntfs filesystem if it was left hibernated but that usually produces a different error than the one you posted.  You might check that.  Another possibility is corruption of the filesystem.  You could try booting into windows and running chkdsk /f from their command prompt.  You may want to read through a page discussing the various parameters for that specific windows software such as the one at the link below.

 [https://www.avg.com/en/signal/how-to-use-chkdsk-windows](https://www.avg.com/en/signal/how-to-use-chkdsk-windows)

---

### Post by AnupamMitra on 2024-10-23
> **yancek said:**
> Linux will not mount an ntfs filesystem if it was left hibernated but that usually produces a different error than the one you posted.  You might check that.  Another possibility is corruption of the filesystem.  You could try booting into windows and running chkdsk /f from their command prompt.  You may want to read through a page discussing the various parameters for that specific windows software such as the one at the link below.

 [https://www.avg.com/en/signal/how-to-use-chkdsk-windows](https://www.avg.com/en/signal/how-to-use-chkdsk-windows)

Thanks for your reply. When I typed *chkntfs C*, it prompted that "C: is not dirty". Then I typed *chkdsk C: /f  *and after the restart Windows checked the disk*. *It might have rewrote the directory. However, now from Ubuntu I can mount sda4 i.e. Drive C of Windows. Thanks a lot for your cooperation.

---

### Post by yancek on 2024-10-23
If you plan to access a windows filesystem from any Linux, you need to either have hibernation off or properly shutdown windows before trying to access it from Linux.  You should be able to find how to do this on windows forums or the microsoft support site.

You can save yourself future problems by not accessing the system partition (C"\) or if you do that, at least do not modify any system files.

---

### Post by Morbius1 on 2024-10-23
The filemanger ( and only the file manager ) will mount an ntfs partition using the new ntfs3 driver.

ntfs3 is broke.

If you blacklist ntfs3 ( prevent the system from using ntfs3 ) the file manager will use the old ntfs-3g driver.

ntfs3-3g is not broke.

To blacklist ntfs3 run the following command:
```
echo 'blacklist ntfs3' | sudo tee /etc/modprobe.d/disable-ntfs3.conf
```

Reboot your system.

---

### Post by AnupamMitra on 2024-10-24
> **yancek said:**
> If you plan to access a windows filesystem from any Linux, you need to either have hibernation off or properly shutdown windows before trying to access it from Linux.  You should be able to find how to do this on windows forums or the microsoft support site.

You can save yourself future problems by not accessing the system partition (C"\) or if you do that, at least do not modify any system files.

Oh, be rest assured I never put Windows in hibernation mode and only after proper shutdown I open Ubuntu in case of need, though I use Windows occasionally.  Question of modifying C drive does not arise at all.

However, thanks for your care.

---

### Post by alextopic on 2024-11-26
Hello, I solved this problem with the help of Gemini AI and was able to copy files from my Windows SSD to Ubuntu SSD.
I figure my notes might help you out and give you an idea what to do for your needs, don't copy verbatim the ssd names, since
your system might be different. Below will serve as an example to help others, okay good luck.
------------
# How to Mount a path to a Windows 11 partition NTFS
# So from Ubuntu I can access read this partition.

1> $ lsblk
nvme0n1p3 259:3    0   1.9T  0 part

2> $ sudo mkdir /mnt/windows

3> $ sudo apt install ntfs-3g
**IF necessary but with apt list ntfs-3g shows already installed.
4> $ sudo mount /dev/nvme0n1p3 /mnt/windows -t ntfs-3g

5> $ cd /mnt/windows
*To change to this directory to test
6> $ lsblk
*To see if changes were made properly.
nvme0n1     259:0    0   1.9T  0 disk 
&#9500;&#9472;nvme0n1p1 259:1    0   100M  0 part 
&#9500;&#9472;nvme0n1p2 259:2    0    16M  0 part 
&#9500;&#9472;nvme0n1p3 259:3    0   1.9T  0 part /mnt/windows
&#9492;&#9472;nvme0n1p4 259:4    0   674M  0 part 
nvme1n1     259:5    0   1.8T  0 disk 
&#9500;&#9472;nvme1n1p1 259:6    0     1G  0 part /boot/efi
&#9492;&#9472;nvme1n1p2 259:7    0   1.8T  0 part /var/snap/firefox/common/host-hunspell

GEMINI AI OUTPUT: Thanks for helping

Based on the lsblk output you provided, it seems like you have two NVMe SSDs:

    nvme0n1: This is likely your Windows SSD, with multiple partitions:
        nvme0n1p1 and nvme0n1p2: Small partitions, possibly for system boot or recovery.
        nvme0n1p3: The main partition containing your Windows system and data.
        nvme0n1p4: Another small partition, possibly for system recovery or other purposes.

    nvme1n1: This is likely your Ubuntu SSD, with two partitions:
        nvme1n1p1: The EFI System Partition, which is essential for booting your system.
        nvme1n1p2: The main partition where your Ubuntu system and data are stored.

To mount the Windows SSD partition:

    Identify the partition: In your case, it's likely nvme0n1p3.
    Create a mount point: Use the following command to create a directory where you want to mount the partition:
    Bash

   $ sudo mkdir /mnt/windows



Mount the partition: Use the mount command to mount the partition to the created directory:
Bash

$ sudo mount /dev/nvme0n1p3 /mnt/windows -t ntfs-3g


Remember:

    NTFS-3G: Ensure you have the ntfs-3g package installed to read and write NTFS partitions. You can install it using your package manager:
    Bash

    $ sudo apt install ntfs-3g

    Permissions: Make sure you have the necessary permissions to access the files on the Windows partition. You might need to adjust file permissions or use sudo for certain operations.
    Automatic Mounting: If you want to automatically mount the partition on boot, you can add an entry to the /etc/fstab file. However, be cautious when editing this file, as incorrect entries can prevent your system from booting.

By following these steps, you should be able to access and copy files between your Ubuntu and Windows partitions.
profile picture

How do I cd over to the windows mount now?
Bash

$cd /mnt/windows

This command will change your current directory to the /mnt/windows directory, which is where you mounted your Windows partition.

Once you're in this directory, you can use standard Linux commands like ls, cd, cp, mv, etc., to navigate and manipulate files and directories on the Windows partition.

---

### Post by ActionParsnip on 2024-11-26
You may also want to check the NTFS from within Windows so you know the file system is happy. NTFS is proprietary to Microsoft and only they know how it truly works

---

