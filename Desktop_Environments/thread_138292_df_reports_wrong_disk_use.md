---
title: "df reports wrong disk use"
date: 2006-03-01
forum: Desktop Environments
---

### Post by Teunis on 2006-03-01
I run Kubuntu with the 2.6.12-10-686 kernel.

And I use an (external) USB 120GB harddisk with two FAT32 partitions, 100 and 20 GB, usually mounted as /dev/sda1 and /dev/sda5
Since some time I cannot get the system to report the free disk space correctly.
Under WinXP I can see some 14GB is free on the larger partition yet df -h gives me 100% use.

When looking at the properties of the disk in Konqueror and using the Calculate button I do get the same used space value as under Windows yet the system (df -h) still sees the disk as 100% full.

(This happens on both partitions)

Any ideas on how to regain use of these disks?

---

### Post by incubus on 2006-03-02
I'm sorry I don't have the answer for you, but rather a question. I thought FAT32 had a size limit of 32Gb. How did you create them? In windows or linux?

Oh, here:
[http://www.microsoft.com/resources/documentation/Windows/2000/server/reskit/en-us/Default.asp?url=/resources/documentation/Windows/2000/server/reskit/en-us/core/fncc_fil_tvjq.asp]("http://www.microsoft.com/resources/documentation/Windows/2000/server/reskit/en-us/Default.asp?url=/resources/documentation/Windows/2000/server/reskit/en-us/core/fncc_fil_tvjq.asp")

It's strange that both are shown incorrectly. Have you tried running windows scandisk thoroughly?

incubus

EDIT: This is a more useful source of information: [http://en.wikipedia.org/wiki/File_Allocation_Table]("http://en.wikipedia.org/wiki/File_Allocation_Table")
See that you're not violating any of those size limits. I'm not sure how VFAT is implemented, but I would still try to run scandisk under Windows.

---

### Post by ytene on 2006-03-26
For what it's worth, I think you may find that the 32Gb partition limit for FAT32 has been "imposed" by Microsoft and exists within their software, not as a result of field limits within the file structure. If you run Windows and are willing to purchase a tool such as PartitionMagic, you will discover that you can create much larger FAT32 partitions. I am running a 320Gb SATA Drive that has 3 x 64Gb FAT32 partitions, 1 x 64Gb NTFS partition and the remainder of the drive, some 100Gb or so, formatted with ReiserFS.

However, like other posts here I am experiencing problems when trying to configure my ubuntu 5.10 machine to have the ability to read and write to these devices.

On the same machine, with exactly the same hardware, I have been able to install Mandriva 2006 LE and have obtained instant read/write access to these FAT32 partitions, but have tried and failed with ubuntu.

Digging further, it seems to me that the standard ubuntu config in /etc/fstab, which in my case says something like

/dev/hdc1 /media/hdc1 vfat defaults 0 0

is being crippled by the "defaults" option. Checking around, a working configuration for FAT32 on an older Mandriva 2005LE box I see something like

/dev/hdd2 /mnt/win_2 vfat umask=0,iocharset=iso8859-15,codepage=850 0 0

which is way different from anything that ubuntu delivers. Have tried "man" pages and a few reference books without much luck. Checking here prior to googling! Will report back if I succeed or find anything of further use.

---

