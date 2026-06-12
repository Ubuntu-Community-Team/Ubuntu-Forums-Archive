---
title: "Ubuntu Can't Connect to Samba Share"
date: 2009-02-17
forum: General Help
---

### Post by lvleph on 2009-02-17
I setup a samba share on one of my computers, and was able to connect to it through my wife's vista comp and was able to connect to it through XP on virtualbox. I was also able to connect to it with Vista on my laptop. However, using Ubuntu 8.10 on my laptop I cannot seem to connect to that share. I can see the print file system that is shared, but just not the the folder that is shared. I have smbfs and smbclient installed. The shared fs is ntfs and is shared from a Ubuntu 8.10 desktop. Thanks in advance for the help.

EDIT: Here is the result of 'smclient -L //ubuntu' of the computer that cannot see the share:
```

Domain=[UBUNTU] OS=[Unix] Server=[Samba 3.2.3]

	Sharename       Type      Comment
	---------       ----      -------
	print$          Disk      Printer Drivers
	IPC$            IPC       IPC Service (ubuntu server (Samba, Ubuntu))
Domain=[UBUNTU] OS=[Unix] Server=[Samba 3.2.3]

	Server               Comment
	---------            -------

	Workgroup            Master
	---------            -------
	WORKGROUP 
```

and here is from the machine with the share
smbclient -L 127.0.0.1
```

Domain=[UBUNTU] OS=[Unix] Server=[Samba 3.2.3]

	Sharename       Type      Comment
	---------       ----      -------
	print$          Disk      Printer Drivers
	Backup          Disk      
	IPC$            IPC       IPC Service (ubuntu server (Samba, Ubuntu))
	PSC-1500-series Printer   HP PSC 1500 Series
Domain=[UBUNTU] OS=[Unix] Server=[Samba 3.2.3]

	Server               Comment
	---------            -------

	Workgroup            Master
	---------            -------
	WORKGROUP            UBUNTU 
```

EDIT2: Looking at the above, I realized that I also don't have my printer shared correctly. I have not tried to connect to it yet, but the problem computer doesn't see the printer.

EDIT3: I can confirm that print sharing isn't working on the problem computer. I am going to reboot and test from vista.

EDIT4: Was not able to see the shared folder or even the computer with the share through network places on Vista, but I was able to manually mount the shared folder and manually add the printer.

EDIT5: Okay, solved my problem. The issue was that when I used Wubi to install it automatically name both computers Ubuntu. Once I changed the hostname in /etc/hostname and /etc/hosts everything began to work.

Oh and just in case you were wondering why I installed from wubi; well using wubi one can install ubuntu from iso and then move the install to a partition. It takes longer, but then I don't waste dvds.

---

