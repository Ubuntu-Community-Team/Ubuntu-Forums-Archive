---
title: "changed hostname, now apt-get is not working"
date: 2006-08-29
forum: Desktop Environments
---

### Post by rkakkar on 2006-08-29
I changed my hostname by modifying the /etc/hostname file. but now when i try to use apt-get i get the following error.

```

$ sudo apt-get install xmms
sudo: unable to lookup ECS-100 via gethostbyname()

$ cat /etc/hostname
ECS-100

```

---

### Post by anthro398 on 2006-08-29
See [http://ubuntuguide.org/wiki/Dapper#How_to_change_computer_name]("http://ubuntuguide.org/wiki/Dapper#How_to_change_computer_name").  It was the [first hit]("http://www.scroogle.org/cgi-bin/nbbw.cgi?Gw=ubuntu+change+hostname"), which means you probably didn't look.

---

### Post by rkakkar on 2006-08-29
i had read somewhere that you can change the hostname by modifying the /etc/hostname file. Networking Administration is not starting...

$ sudo network-admin
sudo: unable to lookup ECS-100 via gethostbyname()

---

### Post by jrib on 2006-08-29
> **rkakkar said:**
> i had read somewhere that you can change the hostname by modifying the /etc/hostname file. Networking Administration is not starting...

$ sudo network-admin
sudo: unable to lookup ECS-100 via gethostbyname()

make sure /etc/hosts has a line that looks like:
```
127.0.0.1 localhost.localdomain localhost HOSTNAME
```

where HOSTNAME is the same as the contents of /etc/hostname.  In your case it seems to be, ECS-100

---

### Post by rkakkar on 2006-08-30
/etc/hosts has the wrong hostname but i am unable to modify the file because sudo isn't working. i'm unable to run anything with sudo.

$ sudo gedit /etc/hosts
sudo: unable to lookup ECS-100 via gethostbyname()

any workarounds?? :(

---

### Post by watto_one on 2006-08-30
Try restarting your computor and logging into safe mode this should have you as a root user. You can then fix the problem.

---

### Post by rkakkar on 2006-08-30
err i kinda screwed myself there :D. i modified the menu.lst earlier to only show ubuntu and windows xp.

## ## End Default Options ##

title           Ubuntu, kernel 2.6.15-23-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-23-386
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# Windows
title Windows
rootnoverify (hd1,0)
savedefault
makeactive
chainloader +1


so .. umm.. i can't modify it now because sudo isn't working.. any other alternatives? :(

---

### Post by rkakkar on 2006-08-30
is reinstalling ubuntu my only hope? if so, i think this is a bug in ubuntu :(

---

### Post by rkakkar on 2006-08-30
*bump* :|

---

### Post by xtknight on 2006-08-30
Does **sudo nano /etc/hosts** work?  Why would sudo be looking up a hostname?  Hmm...

---

