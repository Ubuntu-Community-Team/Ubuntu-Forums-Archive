---
title: "Install Samsung printer driver"
date: 2006-07-26
forum: Desktop Environments
---

### Post by jacquelineZ on 2006-07-26
I just discover KUbuntu ( but I'had to change my graphic card to perform the install) It works better than my Suse 10.1 which made me crazy !

 On linux printing  ( samsung forum)  i could read an install method for laser printer ML2010 on a Gentoo, with the Samsung driver si I buy this one )


I've a little problem to install the Samsung driver on the Kubuntu from the cdrom but i can see it...

jacqueline@jacqueline-desktop:~$ su jacqueline
Password:
jacqueline@jacqueline-desktop:~$ cd /media/cdrom
jacqueline@jacqueline-desktop:/media/cdrom$ ls
autorun  cups  help      locale  misc  README.txt  setup.data
bin      data  icon.xpm  Manual  ppd   scripts     setup.sh

jacqueline@jacqueline-desktop:/media/cdrom$ /media/cdrom/setup.sh
bash: /media/cdrom/setup.sh : /bin/sh : mauvais interpréteur: Permission non accordée ( bad interpreter !  no permission allowed !)

jacqueline@jacqueline-desktop:/media/cdrom$

There is no root user on Kubuntu....isn't it the problem ? 

I'm as user in the group "cdrom" with  Konqueror: properties  -> access rights, for this driver,   

but i've this with a terminal : owner : root, group : root

-r-xr-xr-x  1 root root   51 2005-08-31 01:57 autorun
dr-xr-xr-x  3 root root 2048 2005-08-31 01:57 bin
dr-xr-xr-x  8 root root 2048 2005-08-31 01:57 cups
dr-xr-xr-x  4 root root 2048 2005-08-31 01:57 data
dr-xr-xr-x  3 root root 2048 2005-08-31 01:57 help
-r--r--r--  1 root root 8517 2005-08-31 01:57 icon.xpm
dr-xr-xr-x  9 root root 2048 2005-08-31 01:57 locale
dr-xr-xr-x 22 root root 4096 2005-08-30 07:39 Manual
dr-xr-xr-x  2 root root 6144 2005-08-31 01:57 misc
dr-xr-xr-x  3 root root 2048 2005-08-31 01:57 ppd
-r--r--r--  1 root root 2555 2005-08-31 01:57 README.txt
dr-xr-xr-x  2 root root 2048 2005-08-31 01:57 scripts
dr-xr-xr-x  4 root root 2048 2005-08-31 01:57 setup.data
-r-xr-xr-x  1 root root 6603 2005-08-31 01:57 setup.sh
jacqueline@jacqueline-desktop:/media/cdrom$       

Isn't it a problem of a "wrong bash" ?

When i put the samsung CD in the lector,  Ubuntu tell me it has found an autorun script and :" do you want to launch it? "  Yessss ! but nothing occurs !


Do I need to change mounting options in fstab for Cdrom ?

/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0 

Thanks for your help.

---

### Post by aysiu on 2006-07-26
Have you tried this? ```
cd /media/cdrom
sudo chmod +x setup.sh
sudo ./setup.sh
```

---

### Post by jacquelineZ on 2006-07-26
I can't do it now, because my printer was configured  by "Install printer" with Ubuntu drivers, like a ML4500 and it works well !  And I need it today !!!!!!
  
I'll try with another one CD, next time, i understand chmod +x, to execute the installer. I've to read docs about "sudo" with Ubuntu different of root user.

 Thank you vm. I enjoy Kubuntu

---

