---
title: "Accessing FTP mount on desktop"
date: 2007-10-25
forum: Desktop Environments
---

### Post by pylon42 on 2007-10-25
Hello,

I used Gnome to mount an ftp server. It worked great, I can access everything fine via an icon on my desktop.

My problem is I want to edit the files using vim and can't seem to find this mounted ftp folder anywhere in the filesystem. Where exactly does it live?

---

### Post by taurus on 2007-10-25
Probably in /media.  

```
df -h
```

---

### Post by pylon42 on 2007-10-26
Nothing. I'm beginning to think it's an illusion.

---

### Post by taurus on 2007-10-26
Can you at least post the output of that command here?

---

### Post by pylon42 on 2007-10-26
Sure thing:

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              25G   12G   12G  52% /
varrun               1013M  220K 1013M   1% /var/run
varlock              1013M     0 1013M   0% /var/lock
udev                 1013M   76K 1013M   1% /dev
devshm               1013M     0 1013M   0% /dev/shm
lrm                  1013M   34M  980M   4% /lib/modules/2.6.22-14-generic/volatile
/dev/sda1              35G   15G   21G  42% /media/sda1
/dev/sda2              33G   24G  9.3G  72% /media/sda2
```

---

### Post by chunderbunny on 2007-10-26
Gnome doesn't actually mount the ftp server anywhere, it just turns nautilus into an ftp client (it does the same thing with SMB shares which I find annoying). 

FTP servers can be mounted onto the filesystem using FUSE and a module called fuseFTP, but fuseFTP is not found in any of the Ubuntu repositories, so I think you would have to install it from [http://wiki.thiesen.org/page/Fuseftp](http://wiki.thiesen.org/page/Fuseftp) by hand.

---

### Post by pylon42 on 2007-10-27
excellent, thank you.

---

