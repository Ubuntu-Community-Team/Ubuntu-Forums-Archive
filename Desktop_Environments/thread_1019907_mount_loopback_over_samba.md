---
title: "mount loopback over samba"
date: 2008-12-23
forum: Desktop Environments
---

### Post by open_coder on 2008-12-23
I just helped my friend install Linux Mint. So far he loves it. 

However, he has a Windows 2003 Server running on his local network that he uses to share rips of movies and television shows with his desktop and laptop. On Windows he uses DaemonTools for this. I figured it would be fairly simple to get this running using a simple loopback mount. I even installed Gmount-iso for him so he can use a GUI to do this (although I explained how to use the CLI for it as well). 

Here's the problem. I can't seem to get the ISO image to mount across the network. I successfully mounted the windows share with smbfs, but I can't get the ISO inside the share to mount.

```
$ sudo mount -t smbfs -o credentials=/home/mjw260/.smbcreds,rw "//Zion03/Server Files/" /media/samba
$ sudo mount -t iso9660 -o loop /media/samba/Images/Antitrust.iso /media/cdrom
/media/samba/Images/Antitrust.iso: Permission denied

```

I have tried to add options to the smbfs mount like umask=002, but to no avail. Has anybody tried this and got it working. This is the first time I have ever had to do anything like this. I've been working on it all afternoon and I'm getting nowhere.

All help appreciated. Thanks guys

--Alex

---

