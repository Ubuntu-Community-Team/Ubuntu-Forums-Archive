---
title: "nautilus-cd-burner does not list my dvd-recorder"
date: 2005-10-13
forum: Desktop Environments
---

### Post by maddin on 2005-10-13
Hi all,

Yesterday I upgraded from hoary to breezy. It seems that everything
went well unless nautlilus-cd-burner does not list my dvd-recorder. In
the list there is only one option to create an ISO-File.

Here is what I've done and some relevant informations:

After upgrading I added some repos to /etc/apt/source.list:


```
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release Candidate i386
(20051005)]/ breezy main restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main universe multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main universe
multiverse restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
```


After refreshing the source list there where about 300 packages to
update. So one can say my system is up to date.

My dvd-recorder is on /dev/hdd:

```
martin@martin:~$ ls -l /dev/hdd
brw-rw----  1 root cdrom 22, 64 2005-10-12 16:02 /dev/hdd
martin@martin:~$
```

A symlink from /dev/cdrw to /dev/hdd exists:

```
martin@martin:~$ ls -l /dev/cdrw
lrwxrwxrwx  1 root root 3 2005-10-12 16:03 /dev/cdrw -> hdd
martin@martin:~$
```

On my mind /proc/sys/dev/cdrom/info is OK:

```
martin@martin:~$ cat /proc/sys/dev/cdrom/info
CD-ROM information, Id: cdrom.c 3.20 2003/12/17

drive name:             hdd     hdc
drive speed:            40      32
drive # of slots:       1       1
Can close tray:         1       1
Can open tray:          1       1
Can lock tray:          1       1
Can change speed:       1       1
Can select disk:        0       0
Can read multisession:  1       1
Can read MCN:           1       1
Reports media changed:  1       1
Can play audio:         1       1
Can write CD-R:         1       0
Can write CD-RW:        1       0
Can read DVD:           1       1
Can write DVD-R:        0       0
Can write DVD-RAM:      0       0
Can read MRW:           0       1
Can write MRW:          0       1
Can write RAM:          1       1


martin@martin:~$
```

I'm a member of the group cdrom:

```
martin@martin:~$ groups
martin adm dialout fax cdrom floppy tape audio dip backup video
plugdev lpadmin scanner admin burn
martin@martin:~$
```

Burning a dvd+rw on the commandline with growisofs was successfully. But cdrecord coud not scan for bus:

```
martin@martin:~$ sudo cdrecord -scanbus
Password:
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.12-9-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
cdrecord: No such file or directory. Cannot open '/dev/pg*'. Cannot open SCSI driver.
cdrecord: For possible targets try 'cdrecord -scanbus'.
cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
cdrecord:
cdrecord: For more information, install the cdrtools-doc
cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .
martin@martin:~$

```

The new Gnome-application Serpentine for creating music-cds says: 

> No recording drive found
No recording drive found on your system, therefore some of Serpentine's functionalities will be disabled.

The dvd-recorder is a RICOH MP5240A. With Hoary the recorder worked without any problems out of the box.

I would be glad if you coud give me any hints :) 

-- 
Greetings Martin Rozmus

---

### Post by maddin on 2005-10-14
Hi, I have new Informations. Although scanbus does not work with cdrecord (see my first posting) I was able to blank a CD-RW on the commandline:

```

 cdrecord dev=/dev/cdrw blank=fast

```

Thereafter I was able to write an ISO-file to the blank RW-disk:

```

 cdrecord -v speed=10 dev=/dev/cdrw /var/local/ISO/2005-10-12-Breezy_cache.iso

```

When I put a blank CD-RW in my recorder an Icon with the right lable (CD-RW blank disk) appears on my Desktop but the nautilus burn:/// does not pop up. So maybe the problem is caused by dbus or nautilus. The command-line tools (cdrecord and growisofs) seem to work well.

I dont know where I could stillt look up. Do you have any suggestions?

---

### Post by SAMsan on 2005-10-27
HI,

Have the same problem since Breezy :/
I don't have no clue for now. Hope some Great Brain will help us :D


+++
SAMsan.

---

