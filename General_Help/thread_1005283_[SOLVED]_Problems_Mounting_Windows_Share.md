---
title: "[SOLVED] Problems Mounting Windows Share"
date: 2008-12-08
forum: General Help
---

### Post by falconed7 on 2008-12-08
Hey everyone!

I am having trouble permanently mounting a windows share (From a Vista PC). I am following [this guide]("http://ubuntuforums.org/showthread.php?t=255872") and I have installed smbfs and get up to the following line:

```
smbmount //WindowsPC/Videos /home/ubuntulaptop/WindowsShare -o username=X,password=Y
```

I get an error that says:

```
mount error 113 = No route to host
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)
```

Being very new to Ubuntu I don't know how to go about fixing this, so any help would be great.

Cheers.

EDIT: I can't seem to even connect to the share via Places>Connect to Server...

---

### Post by theozzlives on 2008-12-08
Can you see it in olaces>network???

If not then try:
```
sudo apt-get install samba
```
```
sudo smbpasswd -a username
```
```
sudo gedit /etc/samba/smb.conf
```
Under Global, you'll find:
```
workgroup=WORKGROUP
```
change "WORKGROUP" to your Windows workgroup name, save and restart.

---

### Post by RomanIvanov on 2008-12-08
Try to mount by this way:
sudo mkdir -p /mnt/romanihome_share/MyDownloads
sudo mount -t cifs //192.168.0.100/MyDownloads /mnt/romanihome_share/MyDownloads -o username=romani,rw,noperm,iocharset=utf8,file_mode=0777,dir_mode=0777

---

### Post by falconed7 on 2008-12-08
Okay I tried both ways then and they havent worked. I read in the documentation that samba wasn't needed to access Windows shares. Is this wrong? Must I setup samba in order to access a windows share?

---

### Post by falconed7 on 2008-12-08
Okay I've managed to get it working by using my PC's IP address instead of it's name... Go figure.

However, now a new problem has arisen. When I shutdown the laptop stalls at a message saying:

[I]CIFS VFS: vfs server not responding
CIFS VFS: No response for cmd 50 mid 6109[/I]

It stalls at this screen for quite a while (possibly a minute) then continues to reboot. It seems to be some sort of bug according to [Google]("http://www.google.com.au/search?hl=en&safe=off&rlz=1B3GGGL_enAU285AU285&sa=X&oi=spell&resnum=0&ct=result&cd=1&q=cifs+vfs+vfs+server+not+responding&spell=1").

I believe this is from the line Roman asked me to use. Is there a way to 'undo' that command?

---

### Post by matthewboh on 2008-12-08
I'm running into the same problem with shutdown using the cifs mount command.  I have to use it in order for OpenOffice 3.0 to correctly deal with network drives - so would love for it to work correctly.

---

### Post by theozzlives on 2008-12-08
> **falconed7 said:**
> Okay I tried both ways then and they havent worked. I read in the documentation that samba wasn't needed to access Windows shares. Is this wrong? Must I setup samba in order to access a windows share?

Yes, you need Samba to access Windows shares and printers

---

### Post by ThrobbingBrain66 on 2008-12-08
> **falconed7 said:**
> Okay I've managed to get it working by using my PC's IP address instead of it's name... Go figure.

However, now a new problem has arisen. When I shutdown the laptop stalls at a message saying:

[I]CIFS VFS: vfs server not responding
CIFS VFS: No response for cmd 50 mid 6109[/I]

It stalls at this screen for quite a while (possibly a minute) then continues to reboot. It seems to be some sort of bug according to [Google]("http://www.google.com.au/search?hl=en&safe=off&rlz=1B3GGGL_enAU285AU285&sa=X&oi=spell&resnum=0&ct=result&cd=1&q=cifs+vfs+vfs+server+not+responding&spell=1").

I believe this is from the line Roman asked me to use. Is there a way to 'undo' that command?

First, if you want to access your share by netbios name instead of ip address, do the following:

edit your /etc/nsswitch.conf file
```
gksudo gedit /etc/nsswitch.conf
```
In this file, add 'wins' to the 'host' line BEFORE 'dns'
So the line will look something like this
```
hosts:          files mdns4_minimal [NOTFOUND=return] wins dns mdns4
```

After a restart, you'll be able to access your drive with netbios names.

To get rid of the error on shutdown, you have to follow the instructions at the "Fixing a CIFS bug with network manager" section of the howto.  Actually, this howto walks you through everything you are trying to do.
[https://wiki.edubuntu.org/MountWindowsSharesPermanently](https://wiki.edubuntu.org/MountWindowsSharesPermanently)

Bascially, the two commands just shutdown the network connection to your share before network-manager shuts down.

---

### Post by falconed7 on 2008-12-08
Thank you everyone for the help!

I fixed the bug as well from Throbbing's link.

Cheers,
falconed

---

### Post by pcrudy on 2008-12-11
Thanks!  the mnt etc. command finally  allowed me to map to my windows shares again.   Been trying for months to map to my windows shares; otherwise I would have had to say 'goodbye' to Ubuntu.  Too bad it's so difficult to map to these shares - unless Ubunutu is fixed so mapping to windows shares was like it was in pre 8.04 versions, ubuntu is on it's way out.  thanks again to the members of this forum for solving this and other issues.

---

