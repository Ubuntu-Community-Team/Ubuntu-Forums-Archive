---
title: "Unable to Mount a share on a Windows Machine"
date: 2005-09-08
forum: Desktop Environments
---

### Post by Scanner on 2005-09-08
I am running Hoary 5.04 with the latest patches and have searched the forum but have not been able to find any reference to the error I am getting.

I am trying to /etc/fstab to auto mount a share on a Windows 2000 server

this is the line I have in fstab:
//192.168.51.59/user	/home/user/Windows_Docs	smbfs	username=user,password=,umask=007,uid=1000,gid=10

When I run sudo mount -a i get the following error message:
mount: wrong fs type, bad option, bad superblock on //192.168.51.59/user,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

This is what I get from dmesg | tail:
/dev/vmnet: open called by PID 8151 (vmnet-bridge)
/dev/vmnet: hub 0 does not exist, allocating memory.
/dev/vmnet: port on hub 0 successfully opened
bridge-eth0: enabling the bridge
bridge-eth0: up
bridge-eth0: already up
bridge-eth0: attached
smbfs: mount_data version 1919251317 is not supported

When I google that message it talks about a file called mount.smbfs not being in the correct location, but that file is nowhere on my system and I cannot find a package in the repositories that provides it, I am at my wits end on this, I know Samba is working, because I can open the share in Nautilus using the PLaces menu, and I can copy documents form it, but I cannot open them in OO.o from Nautilus.

---

### Post by KingBahamut on 2005-09-08
But you do have Samba installed? can you mount the volume inherently, without using fstab?

---

### Post by Scanner on 2005-09-08
Samba Client (smbclient 3.0.14a-3ubuntu3~5.04ubp1) is installed and I can access the share through Nautilus and use files, I can copy them to my local fs and edit them and copy them back this seems to work fine, but I cannot open them directly that is the reason I want to mount the share.

Thanks

---

### Post by Scanner on 2005-09-08
Sorry I miss understood, I get the same messages when I try:

sudo mount -t smbfs //192.168.51.59/user /home/user/Windows_Docs

mount: wrong fs type, bad option, bad superblock on //192.168.51.59/user,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


Thanks

---

### Post by KingBahamut on 2005-09-08
hmmmm.....

and sudo apt-get install samba samba-common 

tells you what?

---

### Post by Scanner on 2005-09-08
samba-common is already the latest version but it wants to install samba. I thought I did not need the server package if I am not going to share files from this computer, my understanding was that all I needed was the smbclient and Smaba-common?

---

### Post by KingBahamut on 2005-09-08
I always do it out of habit. 

whether im serving or not.

---

### Post by Scanner on 2005-09-08
Okay installed samba, same messages.  This is just not making any sense to me, I know I am misssing something small but hugely significant.

---

### Post by bdamon on 2005-09-08
[QUOTE=Scanner]Okay installed samba, same messages.  This is just not making any sense to me, I know I am misssing something small but hugely significant.[/QUOTE]


Try installing smbfs

---

### Post by KingBahamut on 2005-09-08
[QUOTE=bdamon]Try installing smbfs[/QUOTE]
 derf.......Idve though apt-get install samba would have done that.

---

### Post by bdamon on 2005-09-08
[QUOTE=KingBahamut]derf.......Idve though apt-get install samba would have done that.[/QUOTE]

Yea me too, that one has caught me more than once. It should really be part of the base install.

---

### Post by Scanner on 2005-09-08
Well, yep would have thought that would have been default as part of one of the other packages, but that seems to have fixed at least a part of it, now I am getting access errors that I can start to deal with.  Thanks!!

---

