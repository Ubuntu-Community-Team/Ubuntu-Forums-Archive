---
title: "Really confused - chmod"
date: 2009-02-05
forum: General Help
---

### Post by mistaWAC on 2009-02-05
So I'm setting up an FTP server right now and I'm creating a directory where users can manage their own folder (full permissions) and other users can download from any other folder. Here's how I'm doing this:

```

sudo mkdir folder1
sudo chown user:user folder1
sudo chmod -R 644 folder1

```

I've tried doing the chmod line without the recursive, but I still have the same issue.  The issue being that when I'm logged into the FTP server it says "550 folder1: no such directory"  I'm getting that error in Total Commander, FlashFXP, and Firefox.  What the hell?  I've had the server setup like this before so I'm at a loss...

For informative purposes - Running 8.04 LTS

---

### Post by mistaWAC on 2009-02-05
bump

Can anyone please help me?  I could certainly use some help!

---

### Post by albinootje on 2009-02-05
> **mistaWAC said:**
> So I'm setting up an FTP server right now and I'm creating a directory where users can manage their own folder (full permissions) and other users can download from any other folder. Here's how I'm doing this:

```

sudo mkdir folder1
sudo chown user:user folder1
sudo chmod -R 644 folder1

```
"550 folder1: no such directory" 

Which ftp-server software is it, and did you follow a certain howto ?
Are you using system users or virtual ftp users ?

You have to realize that some ftp-server software has configuration that needs to be adjusted before your permission setup can work, some ftp-server software even has ACL options in the configuration file afair.
If that's the case you will have to adjust those settings first before your change of permissions will be used.

---

### Post by mistaWAC on 2009-02-05
I'm using proFTPd, but I think this is something with the filesystem.  I do all my work via SSH in the terminal and I can't even cd into the folder after I chmod it.  All of this is being done via the storage partition I have sectioned off on the HDD.  So maybe it's my fstab file?  I can post it if anyone thinks it could have to do with the options I have enabled in that.

BTW, after I chmod it and try to cd into it it tells me Permission Denied unless I sign into the root account.  I also ls -l and it's listed on the terminal.

---

### Post by albinootje on 2009-02-05
> **mistaWAC said:**
> 
BTW, after I chmod it and try to cd into it it tells me Permission Denied unless I sign into the root account.  I also ls -l and it's listed on the terminal.

I read your posting too quickly, sorry. A first step is to do this :
```

sudo mkdir folder1
sudo chown user:user folder1
sudo chmod 755 folder1

```
Because for a directory you need the executable bit on it, otherwise you cannot "cd" into it.

Does your folder1 have subdirectories ? If so, then that needs to be fixed too.

See also here : [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by mistaWAC on 2009-02-05
755 Worked, but that's what it defaults to after I execute mkdir, so nothing changes.  I tried 777 and I can get into it, but it highlights green (I'm guessing that's because 777 is complete anarchy).  I tried about seven or eight other values and the same thing as 644 happened.

---

### Post by albinootje on 2009-02-05
> **mistaWAC said:**
> I tried about seven or eight other values and the same thing as 644 happened.

I just searched for "permissions proftpd" and found similar questions but no answers.
You might want to try vsftpd and/or pureftpd.
[https://help.ubuntu.com/community/PureFTP](https://help.ubuntu.com/community/PureFTP)

[http://vsftpd.beasts.org/](http://vsftpd.beasts.org/)
[http://viki.brainsware.org/?en/Home](http://viki.brainsware.org/?en/Home)

---

### Post by mistaWAC on 2009-02-05
I've been looking since 4.00pm (it's not 9.00pm here) and I've found little assistance as well.  Like I said though, something is wrong from within the filesystem and not the FTP server because I can't access the folder from the terminal I'm operating from and not just FTP connection alone.

If anyone else has anymore assistance to offer I'm still trying to fix this.  Once I figure this out it'll only take me about a half hour to set the rest of my server up.  So PLEASE help if you can!

---

### Post by mistaWAC on 2009-02-08
Anyone had this issue before?  I really don't want to have to reformat this thing...

---

