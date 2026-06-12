---
title: "how To Restore the System"
date: 2009-04-27
forum: General Help
---

### Post by suresh_vandiyur on 2009-04-27
Restoring options available in ubuntu.. if it is available means how to resore the my system. Plz Help Me..

---

### Post by sahabcse on 2009-04-27
If you need commercial application means just follow Norton Ghost compatibility with Linux. For command line pls follow below url

[http://sahabm.blogspot.com/2009/04/backup-and-restore-your-system-linux.html](http://sahabm.blogspot.com/2009/04/backup-and-restore-your-system-linux.html)

---

### Post by suresh_vandiyur on 2009-04-27
> **sahabcse said:**
> If you need commercial application means just follow Norton Ghost compatibility with Linux. For command line pls follow below url

[http://sahabm.blogspot.com/2009/04/backup-and-restore-your-system-linux.html](http://sahabm.blogspot.com/2009/04/backup-and-restore-your-system-linux.html)
i dont have any backup in my system. i need resore my system before one month.. its possible in ubuntu?.. because in windows we restore the system via the system restore. This Type option avaiable in ubuntu?.. Plz help me

---

### Post by sahabcse on 2009-04-27
Refer below url it may help

[https://wiki.ubuntu.com/SystemRestore](https://wiki.ubuntu.com/SystemRestore)
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

---

### Post by suresh_vandiyur on 2009-04-27
> **sahabcse said:**
> Refer below url it may help

[https://wiki.ubuntu.com/SystemRestore](https://wiki.ubuntu.com/SystemRestore)
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage) i accidently used rm -r cd/home/suresh.so below the error was occured. i nedd restore my system.it is possible?.. Plz help me..

[B]Your session only lastd less than 10 seconds if u have not logged out yourself, this could mean that there is some instalation problem or that maybe out of diskspace. Try logging in with one of the fail safe session see if you can fix this problem
This process is currently running setuid or setgid.
This is not supported use of gkt+ you must create a helper program instead. For further details
[www.gtk.org/setuid.html](www.gtk.org/setuid.html)[/B]

---

### Post by kpkeerthi on 2009-04-27
Do you have a backup?

---

### Post by suresh_vandiyur on 2009-04-27
> **kpkeerthi said:**
> Do you have a backup? i dont have backup.. how to recover this problem.. plz guide me...

---

### Post by kpkeerthi on 2009-04-27
**Never run a computer without a backup.**

The rm -r /home/suresh command would have completely wiped your home and all its contents. However, the OS is still intact. Unfortunately, unless otherwise the command is not 'rm -r /home/suresh', you have lost all your data. You can use [testdisk]("http://www.cgsecurity.org/wiki/TestDisk") to recover as much data as possible. Give it a try if you had valuable data under /home/suresh.

You can create a new user and continue using the system (you do not have to run testdisk to do this). From the GRUB menu, choose the Recovery Mode. At the command prompt, type:
```
useradd <user-name>
```
* <user-name> = To create a user with login id **john**, the command would be 
```
useradd john
```

To set a password:
```
passwd <user-name>
```

Type **reboot** and from GRUB, boot normally. 

Login with the userId/password you just created. This user will have only limited permissions. See [this]("http://www.techotopia.com/index.php/Managing_Ubuntu_Linux_Users_and_Groups") on how to enable additional privileges for the user (see the User Privileges tab).

---

### Post by suresh_vandiyur on 2009-04-27
> **kpkeerthi said:**
> **Never run a computer without a backup.**

The rm -r /home/suresh command would have completely wiped your home and all its contents. However, the OS is still intact. Unfortunately, unless otherwise the command is not 'rm -r /home/suresh', you have lost all your data. You can use [testdisk]("http://www.cgsecurity.org/wiki/TestDisk") to recover as much data as possible. Give it a try if you had valuable data under /home/suresh.

You can create a new user and continue using the system (you do not have to run testdisk to do this). From the GRUB menu, choose the Recovery Mode. At the command prompt, type:
```
useradd <user-name>
```
* <user-name> = To create a user with login id **john**, the command would be 
```
useradd john
```

To set a password:
```
passwd <user-name>
```

Type **reboot** and from GRUB, boot normally. 

Login with the userId/password you just created. This user will have only limited permissions. See [this]("http://www.techotopia.com/index.php/Managing_Ubuntu_Linux_Users_and_Groups") on how to enable additional privileges for the user (see the User Privileges tab). i had created new user that also the same problem. and then this error also occured /.drmc has 644 permission in gui login.. so plz guide me..

---

### Post by kpkeerthi on 2009-04-27
> **suresh_vandiyur said:**
> i had created new user that also the same problem. and then this error also occured /.drmc has 644 permission in gui login.. so plz guide me..

Its [fixable]("http://www.google.co.in/search?q=ubuntu%2C+dmrc%2C+644").

---

### Post by suresh_vandiyur on 2009-04-27
> **kpkeerthi said:**
> Its [fixable]("http://www.google.co.in/search?q=ubuntu%2C+dmrc%2C+644"). can u tell me ur mail id?? Plz...

---

### Post by 3rdalbum on 2009-04-27
FYI, if you'd done this on Windows, the System Restore option wouldn't have done anything - it doesn't track user documents and settings, only system files.

If you haven't set up any such solution for automated backups or restore points (such as Time Vault), then the answer is clear: You can't restore the files you deleted.

---

### Post by suresh_vandiyur on 2009-04-28
> **3rdalbum said:**
> FYI, if you'd done this on Windows, the System Restore option wouldn't have done anything - it doesn't track user documents and settings, only system files.

If you haven't set up any such solution for automated backups or restore points (such as Time Vault), then the answer is clear: You can't restore the files you deleted. how to use the sbackup software. any one know means plz advice me..

---

