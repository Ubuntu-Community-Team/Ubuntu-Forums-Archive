---
title: "Help with stuff in Ubuntu"
date: 2007-08-16
forum: Desktop Environments
---

### Post by Vow of Silence on 2007-08-16
I am new to Linux. I installed today.

I have Ubuntu 7.04 Fiesty Fawn. There are some programs and things I want to install. I have a USB wireless adapter I want to set up. I also want to install EasyUbuntu. HOWEVER....

> Failed to run gdebi-gtk '--non-interactive' '/home/tristicus/Desktop/easyubuntu_latest.deb' as user root.

The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator.

Thats what popped up when i tried to install EasyUbuntu.....Even other things.

What is wrong????

---

### Post by aysiu on 2007-08-17
Are you in the *admin* group? Have you toyed with the /etc/sudoers file?

---

### Post by Vow of Silence on 2007-08-17
I don't know if I am in the admin group and tried all that stuff and no cigar!

I haven't toyed with any files.

---

### Post by aysiu on 2007-08-17
Type the word ```
groups
``` in [the terminal](http://www.psychocats.net/ubuntu/terminal). If all goes well, your output should be ```
vowofsilence adm dialout cdrom floppy audio dip video plugdev lpadmin scanner **admin**
```

---

### Post by Vow of Silence on 2007-08-17
I re-installed and everything was fine.

---

