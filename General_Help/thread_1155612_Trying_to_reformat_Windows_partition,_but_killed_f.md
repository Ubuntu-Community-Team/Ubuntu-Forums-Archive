---
title: "Trying to reformat Windows partition, but killed fstab!"
date: 2009-05-11
forum: General Help
---

### Post by xirrin on 2009-05-11
Here's the start to my problem: I have 3 hard drives on my computer. One 74GB Raptor HDD which has my Windows partition on it, one 300GB Maxtor HDD that is just for storage, and the 80GB drive that I have Ubuntu installed on. Now, the 300GB and 74GB drives would load right up with icons on my desktop when I loaded in to Ubuntu graphical interface, and they would show up in the File Browser as well. When I opened up Ubuntu today the icons were not there.

I was confused by this, and was also preparing to reformat both the storage drive as well as the 74GB raptor due to a suspected virus infection. What I ended up doing was finding a walk-through at this website: 

[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

that showed me how to mount the drives in Ubuntu so I could modify them. The problem is that in the process of following the directions (which I thought I had done perfectly) I managed to completely screw the fstab file it seems. Now even when I go in through the Windows XP install disk it tells me I need a Windows-compatible partition to install to, even when trying to use the Windows installer-based formatting. I went to go through the instructions again and was unable to even locate the backup that it supposedly walked me through doing. 

So, now I'm left with no Windows installation since I killed the partitions, and no way to install Windows on those drives seemingly because I killed the fstab file and it doesn't recognize the drives as being Windows compatible.

Does anyone have any suggestions? I just want to get the drives Windows formattable at this point!



Edit: I found and restored the fstab backup file I made. Still having the same problem where it won't let me open the drives from Ubuntu or format them through Windows installer screen.

---

### Post by blazemore on 2009-05-11
Install gparted
```
sudo apt-get install gparted
```

Run gparted
```
sudo gparted
```

**Pick the correct hard drive from the drop-down menu on the right**

Delete all the partitions on your XP disk.

Now reboot, and try to install XP again, this time to the unpartitioned space. Let XP create a partition, and format it as NTFS (quick).

Install XP in the usual way.

Note: XP will overwrite Grub, so you'll have to reinstall it. There are plenty of guides on this site.

---

### Post by xirrin on 2009-05-11
> **blazemore said:**
> Install gparted
```
sudo apt-get install gparted
```

Run gparted
```
sudo gparted
```

**Pick the correct hard drive from the drop-down menu on the right**

Delete all the partitions on your XP disk.

Now reboot, and try to install XP again, this time to the unpartitioned space. Let XP create a partition, and format it as NTFS (quick).

Install XP in the usual way.

Note: XP will overwrite Grub, so you'll have to reinstall it. There are plenty of guides on this site.

Will try this as soon as I get home from work. THANK YOU!

---

### Post by xirrin on 2009-05-12
Tried what you wrote, with no change in my result. I was able to delete the partitions, but when the windows installer partitioned them it continued to tell me that it wasn't windows-compatible. :(

---

### Post by blazemore on 2009-05-12
Go into your BIOS by following the instructions when your computer first turns on. It might be "Press F2 for Setup" or something like that.

Look for an option to restore default settings. Use it, and see if that works.

---

### Post by xirrin on 2009-05-12
> **blazemore said:**
> Go into your BIOS by following the instructions when your computer first turns on. It might be "Press F2 for Setup" or something like that.

Look for an option to restore default settings. Use it, and see if that works.

No luck. Tried it and nothing changed. :(

---

### Post by blazemore on 2009-05-13
Are you sure all the partitions are deleted?

Go back into GParted, and make sure there are NO partitions listed for the drive.

Try creating a partition in gParted, and formatting it as NTFS. XP might be able to see it (But I'd still recommend formatting it again as part of the install)

If this doesn't help, I'd have a look on Google for some more info, search "XP COmpatible Partition" or something.

Good luck!

---

### Post by xirrin on 2009-05-13
I downloaded the NTFS support files for GParted and was able to reformat the drives as NTFS. Windows gave me the same results again. I did that whole google search and found the following on another forum earlier but it makes no sense to me. I'm hoping someone could explain to me what the heck I need to do to follow this.



As Train was alluding to, when you use FDISK to partition a new hard disk, it creates a partition sector beginning at cylinder 0, head 0, sector 1. When you repartition though, FDISK does NOT update this entire sector. The following DEBUG routine will clear it however:

```
Addresses  What you type
---------  -------------
           F 200 L1000 0
           A CS:100
xxxx:0100  MOV AX,0301
xxxx:0103  MOV BX,0200
xxxx:0106  MOV CX,0001
xxxx:0109  MOV DX,0080
xxxx:010C  INT 13
xxxx:010E  INT 20
xxxx:0110  [Enter]
           G
           Q
Note: The "Addresses" on the left are for reference only, do not type them in. And on line 0110, just press the [Enter] key.
```

When you land back at the DOS prompt, reboot.

Back at work right now, but am I to assume you need a DOS boot floppy, then type DEBUG and then just type in the commands listed?

---

### Post by xirrin on 2009-05-15
Aparrantly that is what you're supposed to do. Unfortunately the DEBUG command appears to be missing from MS-DOS now? *sigh* It seems that the problem lies within the fact then when a reformat is done it doesn't actually start at the front of the drive, but a couple bytes later in order to preserve some information that there (the boot record I think?). I need to find a way to format a drive that starts at the very first part of it, which is not done when you do a typical partition/repartition. Any suggestions?

---

