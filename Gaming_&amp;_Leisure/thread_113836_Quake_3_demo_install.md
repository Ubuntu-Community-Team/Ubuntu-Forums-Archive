---
title: "Quake 3 demo install"
date: 2006-01-07
forum: Gaming &amp; Leisure
---

### Post by Jedeye on 2006-01-07
Hi all I downloaded the quake 3 demo from id as I thought it would be a good "first game" for me to try in linux. Im still new at installing things with the terminal. the file is "linuxq3ademo-1.11-6.x86.gz.sh" this is how I put it in the terminal and the result 

```
jon@ubuntu:~$ sudo /home/jon/Desktop/linuxq3ademo-1.11-6.x86.gz.sh
Password:
sudo: /home/jon/Desktop/linuxq3ademo-1.11-6.x86.gz.sh: command not found
jon@ubuntu:~$

```

any help would be great :D

---

### Post by Perfect Storm on 2006-01-07
```
sudo sh /home/jon/Desktop/linuxq3ademo-1.11-6.x86.gz.sh

```

---

### Post by Jedeye on 2006-01-07
allright! linux gaming here I come!

---

### Post by Moucxs on 2006-01-07
i did it this way

comp@printer:/home/name/Desktop# sudo sh linuxq3ademo-1.11-6.x86.gz.sh

and after that i got lots of this

Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed

my sound is working , driver for the Nvidia is installed.

how can i overcome this error :S

---

### Post by lotusleaf on 2006-01-07
Doesn't checkinstall allow for the quick creation of a .deb for easy install+uninstall?

```

sudo checkinstall bash filename.run
```

Or so I read [here](http://ubuntuforums.org/archive/index.php/t-86051.html).

Would this also work for the Quake 3 demo or not?

---

### Post by slux on 2006-01-08
Moucxs: the error is caused because you are running the command as root (and sudo is completely unnecessary if you already are). Try running the command while being your regular user and it should work. There are ways past that error too of course but they're not really needed...

---

