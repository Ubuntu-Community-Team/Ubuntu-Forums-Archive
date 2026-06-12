---
title: "CDROM not recognised in jaunty"
date: 2009-05-02
forum: General Help
---

### Post by rajeev1204 on 2009-05-02
Doesnt seem to exist under /dev.

Any clues ? Working fine in windows and also boots fine from live cd.

---

### Post by Peter09 on 2009-05-02
Try /media

---

### Post by rajeev1204 on 2009-05-02
> **Peter09 said:**
> Try /media


There is /media/cdrom but its empty.Its not been mounted there.

---

### Post by Peter09 on 2009-05-02
Is it appearing in the 'Places' menu. You may find it is mounted under /media, but not necessarily under CDROM.

---

### Post by rajeev1204 on 2009-05-02
> **Peter09 said:**
> Is it appearing in the 'Places' menu. You may find it is mounted under /media, but not necessarily under CDROM.


No ,not in places and not in /media either :(

---

### Post by delcypher on 2009-05-02
In the /dev/ folder your CDROM drive may appear as sr0 (on my PC this is symbolic link to scd0) or scd0. If the device doesn't exist in /dev then the kernel can't see it.

To check if it does exist in the terminal type```
ls -l /dev/cdrom
ls -l /dev/scd0
```

The output I get from the commands are```
lrwxrwxrwx 1 root root 4 2009-05-02 11:53 /dev/cdrom -> scd0
``` and 

```

brw-rw----+ 1 root cdrom 11, 0 2009-05-02 12:53 /dev/scd0

```

If the kernel can't see it then nothing else will. You can see if there are any error messages relating to your CD drive by ```
dmesg | grep -i CD-ROM

```

Let us know if you see anything interesting.

---

### Post by rajeev1204 on 2009-05-02
> **delcypher said:**
> In the /dev/ folder your CDROM drive may appear as sr0 (on my PC this is symbolic link to scd0) or scd0. If the device doesn't exist in /dev then the kernel can't see it.

To check if it does exist in the terminal type```
ls -l /dev/cdrom
ls -l /dev/scd0
```

The output I get from the commands are```
lrwxrwxrwx 1 root root 4 2009-05-02 11:53 /dev/cdrom -> scd0
``` and 

```

brw-rw----+ 1 root cdrom 11, 0 2009-05-02 12:53 /dev/scd0

```

If the kernel can't see it then nothing else will. You can see if there are any error messages relating to your CD drive by ```
dmesg | grep -i CD-ROM

```

Let us know if you see anything interesting.


Nothing works.

I have a /dev/sg0 but i dont know what it is.

This is output when i do ls -l /dev/sg0

crw-rw---- 1 root disk 21, 0 2009-05-02 19:07 /dev/sg0

nvm. Its not a block device.Means its something else.

CDROM not recognised by the kernel i guess.

---

