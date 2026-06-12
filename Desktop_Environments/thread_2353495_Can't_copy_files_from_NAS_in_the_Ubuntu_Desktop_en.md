---
title: "Can't copy files from NAS in the Ubuntu Desktop enviroment"
date: 2017-02-22
forum: Desktop Environments
---

### Post by kisify on 2017-02-22
Hello,
I am quite new to Ubuntu an so far I have been always able to find a suited solution to my problems, but now a problem occured where I don't find any suitable solution.

The problem consists of the fact that I can not copy any files via drag & drop in the desktop enviroment from my NAS to my PC. However the " cp -a  " function in the Terminal works perfectly fine as well as I am able open the files directly on the NAS(attached to my fritz box).
When I want to drag & drop a file, the popup window (File operations) appears, but it doesn`t move at all. (an empty file is created in the destination folder though)

Any suggestions what the problem might be.

Thanks a lot in advance.

---

### Post by TheFu on 2017-02-22
Welcome to the forums.

There are many different file managers. Which are you using?  caja, thunar, pcmanfm, nautilus and there must be 10 others.  Try each.

Which network protocol is being used?  CIFS, NFS, AFS, SFTP, FTP, DAV, .... ?

When you drop the files, is that into a directory where your userid has "write" permissions?  Try a different directory. Make one under your HOME or under /tmp/ somewhere. Does it work then?

---

### Post by kisify on 2017-02-23
Hello,

for the moment I am using Nautilus but I already had the idea to switch to Nemo which did not work either . The copy window pops up but the transfer doesn't start at all.
My NAS has been mounted with a CIFS protocol!

Unfortunately that doesn't work either because I tried to drop a file to different locations (Desktop, documents folder,...)

---

### Post by kisify on 2017-02-23
Just for info:

 //192.168.178.1/fritz-nas/ /media/NASfritz cifs credentials=/home/k**/.smbcredentials,user  0 0

thats the way I mounted the NAS.
As I said, i can write to the NAS but copying files to the PC doesn't work

---

### Post by TheFu on 2017-02-23
>  Try a different directory. Make one under your HOME or under /tmp/ somewhere. Does it work then? 

What are the directory permissions where you are trying to write the files?

---

### Post by kisify on 2017-02-23
the permissions are the following: drwxr-xr-x while I am the user.

strangely, with alt-Tab I can not find the "file operations" pop-up so that I have to minimize all the windows in order to see the pop-up and thus cancel the transfer

For my mounted folder I am as well the owner with writing and reading permissions.


This is a very strange problem indeed.

---

### Post by TheFu on 2017-02-23
>  Try a different directory. Make one under your HOME or under /tmp/ somewhere. Does it work then? 

Did you try this?

---

### Post by kisify on 2017-02-23
no that doesn't work either

Ithink that the problem was not there before an update. Do you think it is worth to rollback to an older nautilus version?

---

### Post by TheFu on 2017-02-23
I don't use nautilus and my NAS uses NFS for Unix clients. NFS is the native network storage protocol for all Unix systems.

Does the same stuff work from other clients?  Are there any log files that have info?

---

### Post by kisify on 2017-02-23
Okay, well my NAS is an NTFS connected to my fritzbox

I have been using this NAS now for months and I did not encounter any Problems from my MAC or WIndows PCs

---

### Post by TheFu on 2017-02-23
Fritzbox is a router?  Almost all home routers have poor security.  May want to rethink connecting storage to it. About 50% of them allow external people access to connected storage even when configured NOT to allow it.

The other issue is that most Linux-based home routers that implement samba/CIFS use a cut down version that doesn't follow the specs.

None of this matters today.  [http://ubuntuhandbook.org/index.php/2014/08/map-network-drive-onto-ubuntu-14-04/](http://ubuntuhandbook.org/index.php/2014/08/map-network-drive-onto-ubuntu-14-04/) says you have to specify the uid and gid and a few other options.

Their example:
> //192.168.1.5/share /media/Ji-share cifs credentials=/home/handbook/.smbcredentials,iocharset=utf8,gid=1000,uid=1000,file_mode=0777,dir_mode=0777 0 0


The 'id' command will show the uid and gid you probably want to use.  I'd make the file_mode 0664 and dir_mode=0775 myself.

I'd ssh into the fritzbox and monitor the samba logs during the connection and copy attempts.  Could the GUI be using FUSE and the CLI be using smbclient connection methods?  Just a thought.  Maybe the client GUI libraries for FUSE aren't properly installed?

---

### Post by kisify on 2017-02-24
Hello again,

I just found out that when I connect to my NAS share directly via the nautilus(Ctrl-L) with smb://192.168.178.1, then it works perfectly fine. Only if I want to mount the NAS via the fstab or mount function, then the problem occurs.

---

### Post by TheFu on 2017-02-24
FUSE is much slower than real mounts. Much slower.

Did you add the other options to your fstab and try again?  Did it work?

---

### Post by kisify on 2017-02-24
<Sorry but that didn`t work either.

But there is one detail that could be interesting for you. I think the problem appeared after I updated the kernel as I had some system freeze problems a while ago. Could that have any influence on the Fuse libraries?

---

### Post by TheFu on 2017-02-24
I'll await the answer to my prior questions, but seems we are probably beyond my ability to help. Sorry.

My 2 CIFS mounts are managed through autofs.  About once a month, I have to reboot a Win7 box because of a flaw in their implementation (they don't close files correctly). [https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently) might help. You've probably already seen that pg.  I didn't realize you could place UID/GID info into the credentials file, just been using username= and password= myself. Interesting.

---

