---
title: "I've lost my Windows after system upgrade!"
date: 2006-08-18
forum: Desktop Environments
---

### Post by Janek on 2006-08-18
I've freshly installed Ubuntu as dual-boot with Windows and everything was fine. I've set Windows in GRUB menu.lst as my default system to boot and I had an access to mounted Windows partition from Ubuntu.

Then, I've updated all my Linux software (including new kernel) through Synaptic. And something went horribly wrong: now I can't run Windows from GRUB (it displays an error message and then returns to the list) and I can't mount my Windows partition, neither on boot nor manually.

I beg you for help as my parents are using Windows and they will probably kill (or at least torture) me if they won't gain access to it as soon as possible.

Some random files and error messages which may give you the hint (I may post more of them, just tell me what's needed):

(When I try to mount)
```
jan@jan-desktop:~$ sudo mount /dev/hda1 /media/Windows/ -t ntfs -o nls=utf8,umask=0222
Password:
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

(after command dmesg | tail)
```
[17180107.084000] NTFS-fs warning (device hda1): is_boot_sector_ntfs(): Invalid boot sector checksum.
[17180107.084000] NTFS-fs error (device hda1): read_ntfs_boot_sector(): Primary boot sector is invalid.
[17180107.084000] NTFS-fs error (device hda1): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[17180107.084000] NTFS-fs error (device hda1): ntfs_fill_super(): Not an NTFS volume.
[17181057.852000] NTFS-fs warning (device hda1): is_boot_sector_ntfs(): Invalid boot sector checksum.
[17181057.852000] NTFS-fs error (device hda1): read_ntfs_boot_sector(): Primary boot sector is invalid.
[17181057.852000] NTFS-fs error (device hda1): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[17181057.852000] NTFS-fs error (device hda1): ntfs_fill_super(): Not an NTFS volume.

```

(Windows entry in my menu.lst)
```
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1
```

Any suggestions? Please? 
I hope that's nothing *really* bad and that there's one wise command which will undo everything.
Thanks in advance.

---

### Post by goatflyer on 2006-08-18
This looks very bad.  Your first partition doesn't appear like it has a valid NTFS file system.

what is the output of:

fdisk -l /dev/hda

This will show all partitions, and what filesystem is (supposed to be) stored on each.

How exactly did you do the upgrade?  And what went wrong?

---

### Post by Janek on 2006-08-18
Thanks for fast response, **goatflyer**.

I've used all my superpowers and now, after using fixmbr and fixboot, I'm back on Windows.

My new problem is, I'm *quite* scared about restoring Ubuntu and GRUB with Live CD. Does anybody know what is the actual risk of that situation happening once again and how could I prevent the potential danger?

I've updated my system by clicking that orange star icon on the top panel; I think it's pretty standard way of doing it. There were no error messages or whatsoever; I was just unable to run Windows during the next boot.

---

### Post by goatflyer on 2006-08-18
Here are instructions to reinstall grub only from live cd:

[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

Since you are only reinstalling grub, there is no risk to any of your partitions, only to the MBR, and you know how to fix that if something goes wrong (unlikely).

I don't see what could have caused your initial problem, but try the above to see if you get your dual-boot system back.

---

### Post by Janek on 2006-08-18
Well, thanks a lot. I will try that and tell you if I messed up something once again.

---

