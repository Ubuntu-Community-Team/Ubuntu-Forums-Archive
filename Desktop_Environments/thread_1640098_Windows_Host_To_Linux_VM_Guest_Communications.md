---
title: "Windows Host To Linux VM Guest Communications"
date: 2010-12-07
forum: Desktop Environments
---

### Post by turfnsurf4me on 2010-12-07
I'm running Ubuntu 10.10 desktop in a VirtualBox VM on a Windows 2008 host machine. The end goal is join the the Ubuntu VM to a Windows 2008 domain.
 
 
I've downloaded 
 
likewilikewise-open_5.4.0.42111-2ubuntu1.2_i386.deb se-open_5.4.0.42111-2ubuntu1.2_i386.deb 
 
to get the joining of the VM to the domain. But from this point forward, I'm completely lost.
 
1) How do I implement this likewise package?
2) How do I get files from my Windows 2008 host to the Ubuntu guest VM?
 
The likewise file is burned to a DVD. When I try to read the DVD, I get the "My Disk" icon but only one file gets displayed. In other words, the DVD the likewise file is burned to has a ton of files. Ubuntu doesn't see any of them expect one .exe file.
 
The /etc/fstab had no entry for cdrom, so I put a line in that says
 
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0 
 
rebooted and that didn't do squat. There is no entry /etc/cdrom but there is directory /etc/My Disc. And I suppose that's what gets mounted because I can see one file on that disc.
 
So then I thought, to hell with the DVD drive and I'll just get the Linux guest to see a "shared drive" on the host. I shared out a folder on the host via the Virtualbox "shared folders". But how I get the Ubuntu guest to see this shared folder is as big a mystery to me as is the creation of life.
 
 
So the bottom line is, I dont' know what the hell I'm doing and need some help. Thanks.

---

### Post by turfnsurf4me on 2010-12-07
Yeah for me... lol.  I discoverd how to get the Ubuntu VM guest to talk to the Windows host share drives..
 
[SIZE=2][FONT=Courier New]mkdir /media/windows-share[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]mount -t vboxsf folder-name /media/windows-shared[/FONT][/SIZE]
[SIZE=2][FONT=Courier New] 
[/FONT][/SIZE][SIZE=2][FONT=Courier New]Where *folder-name*will be the name you assigned for this folder when you were adding it in the shared folders list.[/FONT][/SIZE]
[FONT=Courier New][SIZE=2][/SIZE][/FONT] 
[SIZE=2][FONT=Courier New][/FONT][/SIZE] 
[SIZE=2][FONT=Courier New]Worked like a champ. I can see all the files in the shared folder. So now I copied that likewise-open... file to the Ubuntu VM. I've been told that file with the .deb extension is like a windows .msi file. So I should just be able to double click on it, and install the features. Then....configure.  Sounds logical to me.[/FONT][/SIZE]
[SIZE=2][FONT=Courier New][/FONT][/SIZE] 
[SIZE=2][FONT=Courier New][/FONT][/SIZE] 
[SIZE=2][FONT=Courier New] 

[/FONT]

[/SIZE]

---

