---
title: "Accessing shared drive on Windows network"
date: 2006-07-02
forum: Desktop Environments
---

### Post by alanh on 2006-07-02
I'm having some problems accessing a shared drive on my Windows network.  In Windows, I've created a shared drive (actually a FAT32 partition on a USB hard drive).  I've set up the appropriate permissions, in Windows, for reading and writing.   In Ubuntu, I've found and mounted the drive using the Places>Network Servers menu and Ubuntu has placed a link in the Places menu and on the desktop.   I can use this to open the drive and browse it's contents.  However, I can't find the drive anywhere in the file browser.  I assume it is mounted somewhere but I can't find a mount point anywhere.  What am I doing wrong?

---

### Post by Thund3rstruck on 2006-07-02
I've found the linux GUIs pretty unreliable when it comes to this sort of thing. Its best to make a folder in /mnt or /media called 'windows' or something like that and then mount it. 

```

sudo mount -t smbfs -o username=MyWinUserName,password=MyPassword //ServerName/Sharename /mnt/windows 

```

If you get unknown filetype 'smbfs' you need to install the samba filesystem
```

sudo apt-get install smbfs

```

Keep in mind if this Windows machine is a 2003 server then smbfs won't work and you'll need to use CIFS

---

### Post by alanh on 2006-07-03
If I'm understanding correctly, the drive must be mounted somewhere, as it is accessible from the desktop.   Is there a terminal command I can use to list all the mounted drives and their mount point?   I tried df -h and the Windows network drives didn't show.

---

### Post by TuxCrafter on 2006-07-05
Try looking at /mnt/ and /media/ for mounted devices.

I also notice that accesing a network share form nautilus without doing the mount command is not the same as mouning a network to some folder. 

I tink something with premisions. I also have te problem that i cant open rar files ect and that time an data are wrong. When I mount the share i can open rar files. 

Hopes this gives you some ideas

---

### Post by Thund3rstruck on 2006-07-05
type
```

sudo mount

```

this will list all mounted drives. You'll need to mount the shared folders if you want to do things such as watch mplayer videos over the network

---

