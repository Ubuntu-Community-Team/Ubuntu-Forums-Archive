---
title: "remove ubuntu on dual boot"
date: 2013-08-23
forum: Desktop Environments
---

### Post by vs-punn on 2013-08-23
I have ubuntu 9.10 with windows xp. 
I now want just win xp on that machine.
How do I do it.
SShould I go in Disk Management of windows and format the partition that has Ubuntu or is there any other way out.

The machine is quite old and cannot handle new versions of Ubuntu.

---

### Post by erasmusp on 2013-08-23
Go into a command line within XP (Start/Run/cmd.exe) and type in the command *fixmbr* and Enter. Then, as you suggested, use the Windows Disk Management utility and just format the Ubuntu partition(s) into NTFS format.

---

### Post by oldfred on 2013-08-23
I do not think XP has Disk tools like Vista or 7 do.

You can use gparted, parted magic, the Ubuntu installer has gparted, or third party Windows disk tools.

---

### Post by hg-knight on 2013-08-23
unsure if disk manager is in xp.if it is format partition and allocate disc number

---

### Post by 2Stoned on 2013-08-24
You can use third party apps like partition wizard home edition, you have to format the ubuntu partition and resize/allocate more space to winxp.
And i would suggest to use the WinXP installation disk and use the recovery mode to fix the MBR. This might might be very usefull for you: [https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

---

### Post by Jonathan Precise on 2013-08-25
Before doing this, _**backup,**_ as this has the possibility of causing **_LOSS OF DATA!!!!!!!!_**

I recommend using [clonezilla]("http://ufpr.dl.sourceforge.net/project/clonezilla/clonezilla_live_stable/2.1.2-20/clonezilla-live-2.1.2-20-i486.iso") to backup your system. Burn the CD, and reboot with the CD inside. Follow the instructions, and continue. If you decide to not backup, then **_proceed at your own risk!!!_**

Then use [OS uninstaller]("http://sourceforge.net/projects/boot-repair-cd/files/boot-repair-disk-32bit.iso/download") to uninstall ubuntu.

Afterwards, use gparted to re-size the windows C: drive. After all of this, you should be able to use Windows XP only. If not, use your Windows XP restore disk to run:

```
fixboot
fixmbr
exit
```

Then restart. That should fix the problem.

Edit: If not, try "Automatic Repair"
Edit 2: If that also goes wrong, use clonezilla to restore the backup you previously created.

---

### Post by erasmusp on 2013-08-27
> **oldfred said:**
> I do not think XP has Disk tools like Vista or 7 do.

You can use gparted, parted magic, the Ubuntu installer has gparted, or third party Windows disk tools.

Hi, yes XP does have Disk Tools, or at leat XP Professional does. It is Right Click/My Computer/Manage/Storage/Disk Management.

Regards,
Phill

---

### Post by erasmusp on 2013-08-27
> **oldfred said:**
> I do not think XP has Disk tools like Vista or 7 do.

You can use gparted, parted magic, the Ubuntu installer has gparted, or third party Windows disk tools.

Hi, yes XP does have Disk Tools, or at least XP Professional does. It is Right Click/My Computer/Manage/Storage/Disk Management.

Regards,
Phill

---

