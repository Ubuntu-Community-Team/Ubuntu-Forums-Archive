---
title: "VMware crashed, lost and important VM, where is it?"
date: 2009-06-22
forum: General Help
---

### Post by SypsG on 2009-06-22
Hi everyone. I'm new to the group, primarily because of this seemingly insurmountable problem I'm faced with. Here goes:

I am running 8.10 desktop (2.6.27-14 generic), with VMware server 2.0. VMware server had some issues with it's networking and hung ubuntu (I know, I was surprised to see that happen), so I had to hard power my system.

When it came back up, a file system check fount tons of lost inodes and moved half my system to lost+found (many many gigs). I backed up the lost+found directory to a portable hard drive.

I installed ubuntu 8.10 on a new partition, upgraded it to 27-14, and copied system files and user information to the broken one in order to get it stable. I was then able to login and found some major damage. To the tune of my start-up scripts being gone, many of the progs in etc and bin/sbin being gone.

My main problem is that I need to recover my Windows 2003 Server virtual machine, which is gone. I have been able to find the files (from lost+found, Ie. #3122949 (2.4Gb) for another VM (my Apache rpath linux web server which hosts some ESX backup files) which isn't as important. I have 5 months of data in my Win2k3 VM that I need to recover, but I can't find any files large enough in my lost+found that could be the Win2k3 VM files.

Can anyone tell me what I can do with my system to try to find the VM? Understandably, the directories that contained my running VM's became derefenced/lost when the system crashed. This is a huge heartache for me because I have some deliverables that I need to recover for a very important client.

Please advise ASAP!!

Thanks,
SypsG

---

### Post by Cheesemill on 2009-06-22
Just restore the VM from your last backup.

---

### Post by SypsG on 2009-06-22
> **Cheesemill said:**
> Just restore the VM from your last backup.

They were in one of the directories that is gone. I am thinking that maybe fsck was only able to convert files of up to a certain size into the lost+found dereferenced ones... If this is true, then this is a lost cause for me. Any fsck experts out there?

My last full backup to external media was about 3 months ago (so that has helped a bit), but I was able to recover other things from my home directory that ended up in lost+found, but not the VM or it's local backups. The way I was backing them up was having the VM turned off, and copying all the vm files to a directory in my home directory. My entire /home was converted to lost+found's #5555555 (for example) files, but I can't find any files larger than 2.4Gb (my Apache web server vmdk).

I really need to find my VM and get into it though. The help I'm requesting is beyond the obvious outlets like retrieving from backups. Is there any program that can restore lost+found files? I've done "file *" on them and found the obvious ones that are "VMware VMDK files" and "Vmware VMX" files. That's how I found my web server VM. I've grep'd through every file in there looking for strings like "Windows 2003 Enterprise Server", with unhelpful results (like the Apache VM had that string inside it for some reason).

The latest thing I have been trying is renaming the large files to Windows 2003 Enterprise Server.vmdk, and adding them to a new install of VMware server, but the Win2k3 server vmdk was broken into 4 pieces by VMware (2Gb blocks I'm sure), so I'm only getting "Hard Disk not valid" errors in VMware server:
Windows Server 2003 Enterprise Edition.vmdk ,
Windows Server 2003 Enterprise Edition-000001.vmdk ,
Windows Server 2003 Enterprise Edition-000002.vmdk &
Windows Server 2003 Enterprise Edition-000003.vmdk .

---

### Post by SypsG on 2009-06-22
Maybe I'm on the right track...  I think I may have had an extended file system installed to store /home. Not sure if this is going to help me find my VM (since it was in /var/lib/vmware/Virtual Machines/, but who knows.   Regardless though, the system was corrupted and now I can't mount it:    root@IbexSTVA:/dev# mount -t xfs /dev/sda2 /mnt/sda2target/ mount: /dev/sda2: can't read superblock  root@IbexSTVA:/dev# dumpe2fs /dev/sda2 | more dumpe2fs 1.41.3 dumpe2fs: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda2 Couldn't find valid filesystem superblock.  root@IbexSTVA:/dev# dmesg | tail [255542.840011] sd 3:0:0:0: [sdb] Attached SCSI disk  [255542.840233] sd 3:0:0:0: Attached scsi generic sg2 type 0 [257592.132616] attempt to access beyond end of device  [257592.132632] sda2: rw=0, want=4, limit=2  [257592.133361] EXT3-fs: unable to read superblock  [257749.977055] SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled  [257749.982039] SGI XFS Quota Management subsystem  [257749.984699] attempt to access beyond end of device  [257749.984736] sda2: rw=0, want=8, limit=2 [257749.984745] XFS: SB read failed  Thoughts, suggestions, ideas, help, please?

---

### Post by SypsG on 2009-06-22
Don't know why, but the forum is dorking up the formatting on this... trying again after multiple edit attempts.  root@IbexSTVA:/dev# mount -t xfs /dev/sda2 /mnt/sda2target/ mount: /dev/sda2: can't read superblock  root@IbexSTVA:/dev# dumpe2fs /dev/sda2 | more dumpe2fs 1.41.3 (12-Oct-2008) dumpe2fs: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda2 Couldn't find valid filesystem superblock.  root@IbexSTVA:/dev# dmesg | tail [255542.840011] sd 3:0:0:0: [sdb] Attached SCSI disk [255542.840233] sd 3:0:0:0: Attached scsi generic sg2 type 0 [257592.132616] attempt to access beyond end of device [257592.132632] sda2: rw=0, want=4, limit=2 [257592.133361] EXT3-fs: unable to read superblock [257749.977055] SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled [257749.982039] SGI XFS Quota Management subsystem [257749.984699] attempt to access beyond end of device [257749.984736] sda2: rw=0, want=8, limit=2 [257749.984745] XFS: SB read failed

---

### Post by SypsG on 2009-06-22
Okay, apparently copying and pasting isn't working right, and what the heck is up with that smily face icon? I didn't put that there... grrr...

---

### Post by SypsG on 2009-06-22
Okay, someone please teach me how to keep this forum from removing my carriage-return line-feeds. Please....  Also, note how (in this garbled mess below) that the /dev/sda2 (old) and /dev/sda6 (current) have the same start and end blocks.   This is odd, to say the least:  Device Boot Start End Blocks Id System /dev/sda1 * 1 11593 93120741 83 Linux (My busted file system) /dev/sda2 11594 19457 63167580 5 Extended   /dev/sda5 18663 19457 6385806 82 Linux swap / Solaris   /dev/sda6 11594 18367 54412092 83 Linux (the new file system I am working in)   /dev/sda7 18368 18662 2369556 82 Linux swap / Solaris     Did I overwrite the old extended file system with the new fresh install somehow? If so, how the heck is /dev/sda2 still there, showing the same start and end blocks as the new /dev/sda6?

---

