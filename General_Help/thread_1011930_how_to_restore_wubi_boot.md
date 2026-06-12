---
title: "how to restore wubi boot"
date: 2008-12-15
forum: General Help
---

### Post by vadash on 2008-12-15
Hi, i´ve installed ubuntu 8.10 via Wubi and i was wondering if you guys know how in the case of reinstalling winXP how to be cappable of launch ubuntu without reinstalling it
Thanks, Sorry but my english is not good as a would like

---

### Post by Jammanuser on 2008-12-15
Hi, see this link. it may help

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

):P

Jam Man

:guitar:

---

### Post by ago on 2008-12-15
> **vadash said:**
> Hi, i´ve installed ubuntu 8.10 via Wubi and i was wondering if you guys know how in the case of reinstalling winXP how to be cappable of launch ubuntu without reinstalling it
Thanks, Sorry but my english is not good as a would like

Just make a backup copy of boot.ini, wubildr, wubildr.mbr and the ubuntu folder. Then restore them after installation.

---

### Post by csh on 2009-07-07
I installed Ubuntu with Wubi to another partition (D:), but the Wubildr and Wubildr.mbr files still inside C:.

That means if I reinstall Windows, only the Wubildr and Wubildr.mbr files will be deleted, and the whole Ubuntu directory will still exist.

In case the following circumstances occured:
1. I forgot to backup the Wubildr and Wubildr.mbr files before reinstall Windows, OR
2. I backed up the Wubildr and Wubildr.mbr, but the backup files was corrupted, OR
3. I lost the backup files, OR
4. I cannot boot into Windows nor Ubuntu to backup the files due to corrupted boot.ini file, OR
5. I just cannot boot into Windows.

In case the above circumstances occurred, after reinstall Windows, how to restore both Wubildr and Wubildr.mbr files without reinstalling Ubuntu?

---

### Post by atwin on 2009-10-08
If your ubuntu installation is on another partition within the same harddisk, just go to that partition and copy the two files; (wubildr and wubildr.mbr) which you can find under D:\Ubuntu\winboot\ . (Replace "D:" with the partition on which you installed ubuntu.)

Then Paste the two files in the root Windows partition, i.e C:.

Show all Hidden and System files in Windows and then uncheck boot.ini's read-only attribute in its properties.  Open boot.ini and add the following line at the end and save:

C:\wubildr.mdr = "Ubuntu"

Reboot your PC and you can now get back into your ubuntu installation.

Hope this helps.

---

### Post by iasenko on 2009-10-30
I have the same issue, but the only deference is that I have Win 7 instead of XP. Any ideas how to recover my previous ubuntu (wubi) installation .

---

