---
title: "fsck and chkdsk"
date: 2009-04-09
forum: General Help
---

### Post by measekite on 2009-04-09
fsck is a command to check a Linux filesystem.

Does this mean any filesystem supported by Linux like ntfs?

If so then how do you use it for an ntfs filesystem?

chkdsk is a similar Windows command that checks an ntfs filesystem.

I have a couple of ntfs formatted drives.  One is an EIDE and the other is an external USB2.  After the fact I found that there was corruption in the EIDE drive and all of the free space was allocated on the USB2 drive so new files could not be written but existing files could be overwritten.

In both cases I [COLOR=Red]corrected[/COLOR] this by booting Windows and using the Windows command:

```
chkdsk /f X:
```where X is the Windows drive letter.

):P [COLOR=Red]** Is it possible to make the same checks and corrections using a Linux command and not  having to boot to Windows.**[/COLOR]

I would like to remove Windows from my machine when I do the next upgrade and still keep ntfs.

In Windows (Norton) used to have a utility that would reformat a loaded drive by moving a sector to another place, reformatting the sector and moving the data back so you did not have to temporarily park the data. 

** Is there a good Linux utility that does that?**

---

### Post by pablopancho on 2009-04-09
fsck can deal with linux filesystems.

For ntfs you need to install ntfsprogs (I think that the correct name) which is a set of tools for ntfs. 

To check the ntfs partiton for errors you should run in the terminal

```
sudo ntfsfix /dev/**disk**
```
where disk is the partition you want to check
in my case is sda5 - because sata disks are called sda but it may be hda as well. You can check that in eg. properties of the drive or in gparted

---

### Post by measekite on 2009-04-09
> **pablopancho said:**
> fsck can deal with linux filesystems.

For ntfs you need to install ntfsprogs (I think that the correct name) which is a set of tools for ntfs. 

To check the ntfs partiton for errors you should run in the terminal

```
sudo ntfsfix /dev/**disk**
```where disk is the partition you want to check
in my case is sda5 - because sata disks are called sda but it may be hda as well. You can check that in eg. properties of the drive or in gparted

Thanks

I downloaded ntfsconfig tools that included ntfsfix and others.  There is no items installed in the menu systems and no documentation that I can see.

As for  ```
sudo ntfsfix /dev/**disk**
``` What are the switches.  For example the windows command
```

chkdsk x: 
```just checks and reports on drive x while
```

chkdsk /f x: 
```checks and fixes (/f) drive x:

so at the very leasts I need to know what these switches are for ntfsfix.

Thanks in advance.

---

### Post by MysticGold04 on 2009-04-09
If you go to the terminal, what does 

```

man ntfsfix

```

return?  If it scrolls by too quickly you can do: 

```

man ntfsfix |more

```

so that you can read the help on it if available.

---

### Post by measekite on 2009-04-09
> **pablopancho said:**
> fsck can deal with linux filesystems.

For ntfs you need to install ntfsprogs (I think that the correct name) which is a set of tools for ntfs. 

To check the ntfs partiton for errors you should run in the terminal

```
sudo ntfsfix /dev/**disk**
```
where disk is the partition you want to check
in my case is sda5 - because sata disks are called sda but it may be hda as well. You can check that in eg. properties of the drive or in gparted
Do you have to unmount the partition before using ntfsfix?  I was informed that on Linux partitions fsck can ruin the partition if it is mounted.

---

### Post by coffeecat on 2009-04-09
Read what MysticGold04 posted before using ntfsfix. Then you'll see why you don't want to use that as a substitute for a Windows chkdsk.

---

### Post by pablopancho on 2009-04-09
Yes, we need to be aware that ntfs is Windows file system so the best tool for it will be Windows chkdsk. That means some errors cannot be repaired by ntfsfix. According to man ntfsfix deals only with common problems.

But it comes handy when Windows partition is broken preventing the system from booting - instead of recovery console you can just repair it under Ubuntu.

I usually use ntfsfix but sometimes I notice that although the partition had beed "fixed" under Ubuntu, Windows still finds some errors and repairs them (usually deletes some indexes).

If I was to get rid of Windows completely (now I'm dual booting) I probably wouldn't use ntfs any more (on my external hd maybe I'd use fat32??? I don't know...)

---

### Post by pablopancho on 2009-04-09
> **measekite said:**
> Do you have to unmount the partition before using ntfsfix?  I was informed that on Linux partitions fsck can ruin the partition if it is mounted.

I'm not sure, personally I don't think it matters for ntfsfix...

---

