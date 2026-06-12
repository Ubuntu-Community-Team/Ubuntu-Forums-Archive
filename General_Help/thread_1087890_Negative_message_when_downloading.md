---
title: "Negative message when downloading"
date: 2009-03-05
forum: General Help
---

### Post by Benbow on 2009-03-05
When downloading updates or patches etc (not Ubuntu)I seem to get the following message frequently, in this case it is with Adobe. Could anyone explain to me what this means and what I need to do to correct it?

"/tmp/AdobeReader_enu-8.1.3-1.i486.rpm could not be saved, because you cannot change the contents of that folder.

Change the folder properties and try again, or try saving in a different location."

---

### Post by jerrrys on 2009-03-05
".rpm"  isnt that for redhat/suse/fedora

---

### Post by jmszr on 2009-03-05
Benbow,
       .rpm is a Package Manager for Red Hat, Suse and Fedora . With Ubuntu you need to use .deb though some .rpm can be used through *alien* [http://www.ubuntugeek.com/install-rpm-files-in-ubuntu.html](http://www.ubuntugeek.com/install-rpm-files-in-ubuntu.html). A .deb version of Adobe Reader can be found here:  [http://get.adobe.com/reader/otherversions/](http://get.adobe.com/reader/otherversions/) .

---

### Post by heindsight on 2009-03-05
It seems you don't have write permissions for /tmp

perhaps post the output of the following:
```

id
ls -ld /tmp

```

Also post:
```
cat /etc/fstab
```

---

### Post by Benbow on 2009-03-05
Hi Heindsight

Apologies for the delay, Herewith -

benbow@benbow-desktop:~$ id
uid=1000(benbow) gid=1000(benbow) groups=4(adm),20(dialout),24(cdrom),46(plugdev),108(lpadmin),123(admin),128(sambashare),1000(benbow)
benbow@benbow-desktop:~$ ls -ld /tmp
drwxrwxrwt 14 root root 4096 2009-03-05 22:01 /tmp
benbow@benbow-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=0ff5a351-fd01-40f9-b168-798aaa272345 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda11
UUID=69d2baf3-a8b1-4191-938c-481b3c38e05e none            swap    sw              0       0
# /dev/sda6
UUID=41ffd153-ae30-4fa6-b051-26e058e6d755 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
benbow@benbow-desktop:~$

---

### Post by heindsight on 2009-03-05
> **Benbow said:**
> Hi Heindsight

Apologies for the delay, Herewith -

benbow@benbow-desktop:~$ id
uid=1000(benbow) gid=1000(benbow) groups=4(adm),20(dialout),24(cdrom),46(plugdev),108(lpadmin),123(admin),128(sambashare),1000(benbow)
benbow@benbow-desktop:~$ ls -ld /tmp
drwxrwxrwt 14 root root 4096 2009-03-05 22:01 /tmp
benbow@benbow-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=0ff5a351-fd01-40f9-b168-798aaa272345 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda11
UUID=69d2baf3-a8b1-4191-938c-481b3c38e05e none            swap    sw              0       0
# /dev/sda6
UUID=41ffd153-ae30-4fa6-b051-26e058e6d755 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
benbow@benbow-desktop:~$
Well, I don't see anything unusual there, you should be allowed to write to /tmp.

Perhaps the file you are trying to write to, already exists in /tmp but you don't have permission to access it.
Try doing:
```
ls -l /tmp
```
to see if this is the case.

I'm fairly sure lack of disk space would not cause the kind of error you're getting, but just in case, how much free space do you have?
Use:
```
df -h
```
to find out.

Btw. just a tip, if you're posting output of commands in a terminal, put it in [CODE] tags, it makes it a lot easier to read.

---

