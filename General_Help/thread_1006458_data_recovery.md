---
title: "data recovery"
date: 2008-12-09
forum: General Help
---

### Post by stmartin on 2008-12-09
Hello!
I suddenly deleted one of my very important .cpp (c++ files) with source code. Could you please tell me how to recover it? (I don't know its name cos it was long and it contained blank spaces). I am using Hardy Heron 8.04.
Please help!
Thanks in advance.

---

### Post by linux_tech on 2008-12-09
If its still in the trashcan then open the trash can and right click on the file and choose restore.  What file system were the files stored on?

---

### Post by linux_tech on 2008-12-09
The trashcan is accessible by clicking on the trash icon in the lower right corner of you screen, or open up a file browser window, and either type "~/.Trash" in the navigation bar, or click "trash" in "Places" on the left side.

How did you delete the file- using a command or by using delete key?

---

### Post by stmartin on 2008-12-10
> **linux_tech said:**
> The trashcan is accessible by clicking on the trash icon in the lower right corner of you screen, or open up a file browser window, and either type "~/.Trash" in the navigation bar, or click "trash" in "Places" on the left side.

How did you delete the file- using a command or by using delete key?

I deleted using Ctrl+Shift, so I permanently deleted it. I searched in the Trash but it wasn't there.

---

### Post by PocketDog on 2008-12-10
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery) You also need to get out of the habit of shift-deleting. It may seem easier at the time...

---

### Post by stmartin on 2008-12-10
Sorry, But I didn't find anything which could help me. The link that you gave me is all about Lost Partiton.

REgards.

---

### Post by linux_tech on 2008-12-10
Check filesystems 1st
```
sudo fdisk -l
```

If ext2 or ext3, then download and try a few linux recovery tools

First try magic rescue-- [http://www.student.dtu.dk/~s042078/magicrescue/](http://www.student.dtu.dk/~s042078/magicrescue/)
read more on magic rescue here- [http://www.linux.com/feature/126525](http://www.linux.com/feature/126525)

Download: [http://www.recoverdatasoftware.com/tool/RecoverDataLinuxTrial.tar.gz](http://www.recoverdatasoftware.com/tool/RecoverDataLinuxTrial.tar.gz) 

[http://www.linuxdiskrecovery.com](http://www.linuxdiskrecovery.com)

If its ntfs, then testdisk will work.  But may or may not work with ext2 or ext3, I'm not sure, but its also worth a try. [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Let me know if any of these hopefully work

---

### Post by az on 2008-12-10
> **stmartin said:**
> Sorry, But I didn't find anything which could help me. The link that you gave me is all about Lost Partiton.

REgards.

Actually, it's a pretty comprehensive list of the data recovery software that is available to you.  If the files was on an NTFS filesystem you can use ntfsundelete.  See the page referred to for details.

If it was on an ext3 filesystem, you cannot undelete it but you may be able to data-carve the file.

Power off your computer and boot the live cd.  Install the testdisk package which contains photorec.  Run photorec on your entire partition where the file was.  Select the file type (file opt) to look for text files (I don<t remember if it can distinguish between c++ and other text files)

Then, sort through the many files that it will recover for you.

Foremost also is a great file-carver.  It can look for cpp specifically, but it may also generate many false-positives.

Both photorec and foremost are also detailed on that excellent page (which I wrote... mostly...)

---

### Post by stmartin on 2008-12-10
I am sure that it is NTFS, because I use dual-boot with Windows Xp, and the file was on the ntfs partition. I tried TestDisk, but it is also only for deleted partitions. I got deleted one file, not whole partition.:confused::confused:

---

### Post by linux_tech on 2008-12-10
Test disk undeletes files on NTFS.  Download it and give it a try.
Instructions 
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

---

### Post by aysiu on 2008-12-10
> **stmartin said:**
> I am sure that it is NTFS, because I use dual-boot with Windows Xp, and the file was on the ntfs partition. I tried TestDisk, but it is also only for deleted partitions. I got deleted one file, not whole partition.:confused::confused:
The *testdisk* package installs a program called *photorec*, which is for recovering deleted files. It is not just for lost partitions.

Stop dismissing the help people are giving you. They know what they're talking about.

There is a comprehensive guide here for how to use this (with screenshots):
[Recovering Windows files with a Ubuntu CD III: deleted files](http://www.psychocats.net/ubuntucat/recovering-windows-files-with-a-ubuntu-cd-iii-deleted-files/)

---

### Post by linux_tech on 2008-12-10
Step By Step for PhotoRec-
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

---

### Post by stmartin on 2008-12-10
Sorry for dissapointing but, after using Photorec,and recovering all files with all file data types except .cpp. I still can't understand.

---

### Post by az on 2008-12-10
> **stmartin said:**
> Sorry for dissapointing but, after using Photorec,and recovering all files with all file data types except .cpp. I still can't understand.

As I mentioned...

I would try ntfsundelete first.  Photorec and foremost are blunt tools which recover every single file they find.  Foremost is more of a forensics program which is why it can do a better job at finding a cpp file.  See the DataRecovery page for details on using it and ntfsundelete.  If the file was deleted a short time ago, ntfsundelete should work fine for you.

---

