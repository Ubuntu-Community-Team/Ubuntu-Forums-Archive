---
title: "Accessing Windows 2003 NTFS File servers with Ubuntu Clients. (Is it Safe to write?)"
date: 2006-06-20
forum: Desktop Environments
---

### Post by I_Like_Pie on 2006-06-20
[COLOR=black][FONT=Tahoma][SIZE=3]I looked around and I did not see any posts specifically referring to accessing a Windows 2003 NTFS File server with a Ubuntu Client…so here is my question.[/SIZE][/FONT][/COLOR]

[COLOR=black][FONT=Tahoma][SIZE=3]Ubuntu, like all *nix distros, use FAT as their file system and I am worried that I might run into some problems when interfacing with my server using my laptop running Ubuntu. Despite SAMBA and the responsibility of the server to organize incoming and outgoing activity...I am still somewhat concerned about writing to a server with a NTFS file system using a FAT based client. [/SIZE][/FONT][/COLOR]

[COLOR=black][FONT=Tahoma][SIZE=3]I like NTFS. For what I am using it for it is superior to FAT. I can easily set file security permissions so that my neighbors can listen to my music on my server without having to worry about them messing things up. I can have .iso and .nrg images of my 7.5 gig DL DVDs. I can also have a 4 drive, 900gig RAID 5 setup that I have 100% confidence in. For that reason I will be keeping my server running 2003/NTFS until there is a better option. In short...I won't be running *nix on my server anytime soon. 
 
Most *nix sites warn that you don't want to alter NTFS partitions that are mounted on one machine (e.g. dual booting), so that is a given. I am not mounting a partition from the same disk as my Ubuntu machine. I am connecting to a NTFS server. The server's responsibility is to be the gatekeeper for transfers to the client machine...so either it works or it doesn't. Samba's job is to allow the client, despite the file system on the server, to communicate and transfer properly.
 
I am assuming that I won't have any problems because I have briefly used both of them together before with no problems, but I am just worried in the long run that I will run into file corruption, excessively fragmented drives, or CRC errors when mounting an .iso from the server.[/SIZE][/FONT][/COLOR]

[COLOR=black][FONT=Tahoma][SIZE=3]Am I worrying too much? Does anyone else do this? Has anyone else run into any problems?[/SIZE][/FONT][/COLOR]

---

### Post by jstueve on 2006-06-20
Erm... most *nix distro's do NOT use FAT (or vfat) for their native filesystems.  Vfat as a shared directory (between to dual boot partitions) is common, but not the same thing.

IF the Windows 2003 NTFS file server is sharing directories using CIFS/SMB (aka Samba shares) then it is doing all the read/writes using Windows 2003 OS calls, and is agnostic as to what file system you are using on a client machine.

And you are correct, the NTFS server is responsible for the reads and writes, and the translation occurs much higher in the stack and by the time the actual write occurs it is done natively by the Windows 2003 server.

And you are worrying too much. :)  The problem with NTFS writes is for local hard disks not network shared drives, or NAS.

---

### Post by I_Like_Pie on 2006-06-20
Jstueve,
 
Thanks for the quick reply and correction. I figured that it was a non issue, but I just wanted to make sure before I started hitting the server with a bunch of tasks via Ubuntu. Would be like losing a pet if I poisoned my server with buggy writes.
 
I rationalized that this was a non-issue in the back of my mind, but it is nice to hear it from someone else for that extra little "piece of mind".
 
Have a wonderful day! Thank you

---

