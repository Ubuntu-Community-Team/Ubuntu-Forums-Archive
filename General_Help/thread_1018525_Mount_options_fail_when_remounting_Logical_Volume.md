---
title: "Mount options fail when remounting Logical Volume"
date: 2008-12-22
forum: General Help
---

### Post by jerremy-tamlin on 2008-12-22
Hi I have several logical volumes on my kubuntu Hardy install.

My problem is that if I try to remount one of the filesystems the -o tag does not take effect and the filesystem is instead remounted rw 0 0

```

$ cat /etc/mtab | grep /var/www
/dev/mapper/VG_JW_Laptop-LV_www /var/www ext3 ro,noexec,nosuid,nodev,relatime 0 0

$ sudo mount -o remount ro,exec,nosuid,nodev,relatime /var/www/

$ cat /etc/mtab | grep /var/www 
/dev/mapper/VG_JW_Laptop-LV_www /var/www ext3 rw 0 0

```

Is there a special way of remounting Logical Volumes?

This is doing my head in :confused:
Cheers

---

### Post by jerremy-tamlin on 2009-01-29
Bugger, I still haven't found the answer to this.

Can anyone tell me if they have the same problem
I'm using kubuntu 8.04 installed via the alternative CD.
lvm2 version 2.02.26-1ubunt
mount version 2.13.1-5ubuntu

Cheers

---

### Post by jerome1232 on 2009-01-29
Couldn't you use lvchange to make the logical volume read-only?

```
sudo lvchange -p r /dev/volume\ group/logical\ volume
```

--edit-- testing it I seem to have the same problem and after using lvchange -p r I can still write to the volume so I'd have to look into though I am curious, it's 1:06 am here and I need sleep lol.

---

### Post by geirha on 2009-01-29
Try with:
```
sudo mount -o remount,ro,exec,nosuid,nodev,relatime /var/www/
```

---

### Post by jerremy-tamlin on 2009-01-29
Thanks so much for your help.

The problem was that I was not entering the mount command properly (there is no example in the man page!)

I was going
```
sudo mount -o remount ro,exec,nosuid,nodev,relatime /var/www
```

when what I needed to do was
```
sudo mount -o remount,ro,exec,nosuid,nodev,relatime /var/www/
```

**Needed a COMMA NOT A SPACE between *remount* and *ro***

So simple and yet so hard to google for.

Thanks again.

---

### Post by jerremy-tamlin on 2009-01-29
Hmm, Don't seem to be able to set this thread to SOLVED.

I thought I went to Thread Tools -> Mark as Solved but There's no option for that there. Am I looking in the wrong place? Where else could it be?

---

### Post by jerome1232 on 2009-01-29
That feature has been temporarily disabled.

---

