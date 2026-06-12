---
title: "Resolveconfig error on &quot;Network manager&quot; on startup"
date: 2009-02-23
forum: General Help
---

### Post by kjetilbmoe on 2009-02-23
Hi folks!
A few days ago I noticed an error message during startup. It says something about the networkmanager and not being able to write to the folder / remove files. I 777'ed the directory mentioned, but did not help. Does anybody know what's wrong here? See attached screenshot.

---

### Post by geirha on 2009-02-23
What release are you running? That there is very early in the boot process, and / is only mounted readonly at that stage, so no files can be changed or deleted or created at that time. After the filesystem check has run, it will remount / with read-write.

---

### Post by kjetilbmoe on 2009-03-03
This is the latest version.. 8.10, and everything (else) is up to date, or should be, except this module. I suspected something was wrong when a setup doc for a vpn client was very different from the one on my computer. I can't really tell for sure what's going on during startup, but it looks like an update process is unable of starting... can I in any way fix the permissions so this process can complete?

---

### Post by dcstar on 2009-03-03
> **kjetilbmoe said:**
> Hi folks!
A few days ago I noticed an error message during startup. It says something about the networkmanager and not being able to write to the folder / remove files. I 777'ed the directory mentioned, but did not help. Does anybody know what's wrong here? See attached screenshot.

As it clearly states in the messages: "....read only filesystem".

Your root partition was not shut down correctly and it is mounting as read-only, boot off a Live CD and run an fsck on the partition and (hopefully) it will resolve the problem.

---

### Post by kjetilbmoe on 2009-03-03
> **dcstar said:**
> As it clearly states in the messages: "....read only filesystem".

Your root partition was not shut down correctly and it is mounting as read-only, boot off a Live CD and run an fsck on the partition and (hopefully) it will resolve the problem.

Didn't do much of a difference. Also, this message keeps showing up even though I reboot. I can "perfectly" log in to Ubuntu and use the computer, but I don't like major errors on startup ...

---

### Post by dcstar on 2009-03-03
> **kjetilbmoe said:**
> Didn't do much of a difference. Also, this message keeps showing up even though I reboot. I can "perfectly" log in to Ubuntu and use the computer, but I don't like major errors on startup ...

Post the output of the following:

```
sudo mount | grep /dev
```

---

### Post by kjetilbmoe on 2009-03-03
> **dcstar said:**
> Post the output of the following:

```
sudo mount | grep /dev
```

/dev/sda8 on / type ext3 (rw,relatime,errors=remount-ro)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
/dev/sda6 on /boot type ext3 (rw,relatime)
/dev/sda5 on /home type ext3 (rw,relatime)

---

### Post by dcstar on 2009-03-03
> **kjetilbmoe said:**
> **/dev/sda8 on /** type ext3 (**rw,**relatime,errors=remount-ro)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
/dev/sda6 on /boot type ext3 (rw,relatime)
/dev/sda5 on /home type ext3 (rw,relatime)

It has mounted RW so I don't really understand why you are still getting those same messages, are you sure that they did not change after the fsck?

---

### Post by kjetilbmoe on 2009-03-03
Positive. I did fsck on all the drives just to be sure, and they all returned 'clean'.

Still sure I cannot change any file permissions to solve this? It specifically says that it cannot remove a certain file ...

---

### Post by ChrisMP1 on 2009-03-03
Rather than changing the permissions on the folder (generally a bad idea), go in and manually remove the file. It should be safe to remove that one.

Your file system is started up in read-only mode at first, and then is remounted read/write later.

---

