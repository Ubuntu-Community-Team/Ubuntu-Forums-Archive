---
title: "Autologin in Lubuntu 12.04, what USERNAME?"
date: 2012-05-30
forum: Desktop Environments
---

### Post by Lyfang on 2012-05-30
Hi, I installed Lubuntu 12.04 via Wubi. How can I find my USERNAME to enable autologin in Lubuntu 12.04?
LXTerminal shows USERNAME@ubuntu:~$ 
User Settings/Users and Groups shows a different USERNAME.

Caution novice computer users, don't edit without fear of dealing with  problems.

Enable auto login with LXDM (lightweight display manager) in Lubuntu 12.04:

Add autologin=USERNAME to /etc/lxdm/default.conf

gksudo leafpad /etc/lxdm/default.conf
gksudo leafpad /etc/lxdm/lxdm.conf (?)

---

### Post by zombifier25 on 2012-05-30
The username in the terminal is the actual username on the system. The username in User Settings is just the display name. Use the first one.

---

### Post by ajgreeny on 2012-05-30
The terminal command ```
ls /home
``` will also tell you the name to use.

---

### Post by bcbc on 2012-05-30
Wubi defaults the display name to the windows account you installed on and the ubuntu userid to the lower case of the windows logon.

The idea is: Windows account: John, Ubuntu username: john. Then when you logon to Ubuntu you see "John".

But in practice many people login to Windows as: Administrator or M5123, and pick an ubuntu username of e.g. john.

So you see Administrator when you logon and your Ubuntu desktop, but your username is still john. 

If you don't fit into the "John/john" category, I recommend changing it to avoid confusion: [http://askubuntu.com/a/143872/14916](http://askubuntu.com/a/143872/14916)

---

### Post by Lyfang on 2012-05-31
Thank's zombifier25, ajgreeny & bcbc. Adding autologin=USERNAME to default.conf & lxdm.conf USERNAME from USERNAME@ubuntu:~$ or User Settings/Users and Groups doesn't work. I have installed Lubuntu 12.04 through Wubi on Windows XP. Any help appreciated.

@bcbc
```
sudo cat /etc/passwd | grep USERNAME (from USERNAME@ubuntu:~$)
USERNAME (from USERNAME@ubuntu:~$):x:1000:1000:USERNAME (from login screen LXDM),,,:/home/USERNAME (from USERNAME@ubuntu:~$):/bin/bash
```

---

### Post by Lyfang on 2012-06-04
[SOLVED] [lubuntu] Autologin in Lubuntu 12.04, what USERNAME?

WARNING! Caution, don't try on production machines without fear of dealing with problems. Write autologin-user=USERNAME (from USERNAME@ubuntu:~$ or ls /home) below [SeatDefaults]!

gksudo leafpad /etc/lightdm/lightdm.conf

[SeatDefaults]
greeter-session=lightdm-gtk-greeter
user-session=Lubuntu
autologin-user=USERNAME (from USERNAME@ubuntu:~$ or ls /home)
autologin-user-timeout=0

---

### Post by Lyfang on 2012-10-20
[SOLVED] [lubuntu] Autologin in Lubuntu 12.10

**WARNING! Caution, proceed with care!** (# default at fresh 12.10 installation)

Open LXTerminal:
gksudo leafpad /etc/lightdm/lightdm.conf

```
#[SeatDefaults]
#greeter-session=lightdm-gtk-greeter
#user-session=Lubuntu

[SeatDefaults]
greeter-session=lightdm-gtk-greeter
user-session=Lubuntu
autologin-user=USERNAME
autologin-user-timeout=0
```

---

