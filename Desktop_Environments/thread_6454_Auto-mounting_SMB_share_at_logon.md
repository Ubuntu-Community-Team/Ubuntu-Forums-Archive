---
title: "Auto-mounting SMB share at logon"
date: 2004-11-28
forum: Desktop Environments
---

### Post by bazuka on 2004-11-28
Well, I have tried all I know, and I can not get an SMB share on my Mac to mount automatically.  I have modified /etc/fstab as such...

> //192.168.1.107/storage	/mnt/mac	smbfs		credentials=/root/.smbcredentials,dmask=000,fmask=000	0	0

If I log in, then do "sudo mount -a," it mounts.

I can also manually mount it from the command line like this...
> sudo mount -t smbfs //192.168.1.107/storage /mnt/mac -o username=*myusername*,password=*mypassword*

Am I just missing something fundamental?  My Windows partitions that I mount auto on install also show up under computer:///, but no such luck for the mac share.

---

### Post by jiyuu0 on 2004-11-28
//192.168.1.107/storage /mnt/mac smbfs credentials=/root/.smbcredentials,dmask=000,fmask=000 0 0

try

in fstab:
 //192.168.1.107/storage /mnt/mac smbfs credentials=/root/.smbcredentials,dmask=777,fmask=777 0 0

did you set your username and password for mac in /root/.smbcredentials file?

---

### Post by bazuka on 2004-11-29
Ok, I tried your suggestion, and it doesn't seem to be working. I did notice one similarity in the boot error, and I can reproduce it from the command line.

When I do "mount -t smbfs //192.168.1.107/storage /mnt/mac" it prompts me for a password, but no username, and I get this...
> 4377: session setup failed: ERRDOS - ERRnoaccess (Access denied.)
SMB connection failed That's what I get at boot as well.


When I do "mount -t smbfs //192.168.1.107/storage /mnt/mac -o username=*myusername*" it prompts me for my password, then mounts.



It almost seems like it's not finding /root/.smbcredentials at all. I verified the information in there is correct, and it is formatted like this...

> 
username=*myusername*
password=*mypassword*


I'm really kinda stumped. Is there any way I can put the username in /etc/fstab and have it work that way?


BTW, thanks for the help.

---

### Post by jiyuu0 on 2004-11-29
yes you can

//192.168.1.107/storage /mnt/mac smbfs username=myusername,password=mypassword,dmask=777,fmask=777 0 0

---

### Post by bazuka on 2004-11-30
I actually tried exactly that, and still get errors on boot about bad username/password combination.  I can do this from command line and it works:
> mount -t smbfs //192.168.1.107/share /mnt/mac -o credentials=/root/.smbcredentials

I am really stumped on this.

---

### Post by Skip Da Shu on 2007-11-14
Let me join in the fray because I'd posted almost the same question in the noob section.

/etc/fstab entry ```

//C17-E64desktop/xfer /home/c17xfer smbfs credentials=/home/skip/.smbcredentials,1000 0 0
```

right now .smbcredentials is
```
username=default
password=default
```

Read someplace this was OK since the winxp machine the share is on doesn't have this folder passworded.

Something about this must be working because I can go to the Xubuntu desktop, open a terminal and do
```
sudo mount -a
``` and the c17xfer dir is populated.  However I don't know how to get this command to execute at desktop logon.  I tried adding it to Applications>Settings>Autostarted Applications but that didn't work (xubuntu).

---

