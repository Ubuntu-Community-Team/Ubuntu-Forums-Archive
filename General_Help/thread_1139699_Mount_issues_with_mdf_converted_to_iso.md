---
title: "Mount issues with mdf converted to iso"
date: 2009-04-27
forum: General Help
---

### Post by nullhility on 2009-04-27
Well I got some mdf files and converted them to iso format:
```
mdf2iso SH2_CD1.mdf
```
which worked without a hitch.

I then tried mounting it:
```
$ sudo mount -o loop -t iso9660 SH2_CD1.iso /media/mounted-iso
mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

Heres the relevant "dmesg | tail" output:
```
[108654.568461] ISOFS: Unable to identify CD-ROM format.
```

After googling for awhile I tried this:
```
$ sudo modprobe loop
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
FATAL: Module loop not found.
```

Strange.. no loop module.. make one:
```
$ sudo mknod /dev/loop0 b 7 0
mknod: `/dev/loop0': File exists

```

Now that's where I give up and ask the ubuntu elite for help. As an additional note I upgraded to Jaunty Jackalope just recently but I wouldn't go as far as saying it's a bug yet because this is the first time i've dealt with mdf files.

---

### Post by bacardiandwatermelon on 2009-04-27
I use AcetoneISO to convert mdf files to Iso. It might make things easier..

---

