---
title: "deb package installation issues"
date: 2009-05-25
forum: General Help
---

### Post by ki4jgt on 2009-05-25
When I install programs, they always install, but I get an error message dealing with ipppd. When I type sudo aptitude install ipppd to reinstall it, this message prints out:


```
The following partially installed packages will be configured:
  ipppd 
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up ipppd (1:3.12.20071127-0ubuntu5) ...
Note: running MAKEDEV to create ISDN devices in /dev...
/var/lib/dpkg/info/ipppd.postinst: 112: ./MAKEDEV: not found
dpkg: error processing ipppd (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 ipppd
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up ipppd (1:3.12.20071127-0ubuntu5) ...
Note: running MAKEDEV to create ISDN devices in /dev...
/var/lib/dpkg/info/ipppd.postinst: 112: ./MAKEDEV: not found
dpkg: error processing ipppd (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 ipppd

```

---

### Post by fenzik on 2009-06-21
This helps to fix this issue

```
 ls /sbin/MAKEDEV ls / sbin / MAKEDEV 

```


```
 sudo ln -s /sbin/MAKEDEV /dev sudo ln-s / sbin / MAKEDEV / dev 
```


```
 sudo apt-get install --reinstall makedev sudo apt-get install - reinstall MAKEDEV 

```

```
 sudo dpkg --configure -a sudo dpkg - configure-a 
```

---

### Post by michy99 on 2009-06-21
> **fenzik said:**
> This helps to fix this issue

```
 ls /sbin/MAKEDEV ls / sbin / MAKEDEV 

```


```
 sudo ln -s /sbin/MAKEDEV /dev sudo ln-s / sbin / MAKEDEV / dev 
```


```
 sudo apt-get install --reinstall makedev sudo apt-get install - reinstall MAKEDEV 

```

```
 sudo dpkg --configure -a sudo dpkg - configure-a 
```

I think you've got some formatting issues here.

---

### Post by fenzik on 2009-06-21
michy99. I mentioned the commands within the code, is this wrong?

---

### Post by ki4jgt on 2009-06-30
Thanks, sorry it took so long to respond. It works now

---

### Post by zzeroo on 2009-08-20
Just for the record. Here the commands in nicer format.

```
sudo ln -s /sbin/MAKEDEV /dev

sudo apt-get install --reinstall makedev

sudo dpkg --configure -a
```But, thank you very mutch "[enzik]("http://ubuntuforums.org/member.php?u=702225")". 
It helps

---

### Post by duanedesign on 2009-10-02
here is the bug report for this problem. Looks like the problem has been well reported and a fix is coming.

[https://bugs.launchpad.net/ubuntu/+source/isdnutils/+bug/414537](https://bugs.launchpad.net/ubuntu/+source/isdnutils/+bug/414537)

---

### Post by WhisperiN on 2010-10-14
Hello all..

I have the same problem, I'm running Kubuntu 10.10..

I've issued the commands mentioned above..
But, I still get the error message..

Should I restart the system and try after those commands are issued ??

Regards

---

