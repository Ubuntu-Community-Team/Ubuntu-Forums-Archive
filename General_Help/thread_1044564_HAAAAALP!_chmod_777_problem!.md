---
title: "HAAAAALP! chmod 777 problem!"
date: 2009-01-19
forum: General Help
---

### Post by cyberfin on 2009-01-19
Ok so I didn't have my brightest moment.

I entered this:
```

sudo chmod 777 ./ -r
```

and then this:
```

sudo chmod 777 /. -r
```

I did this as recommended on IRC:

```
ls -la /
```

which returned this:

```
cyberfin@cyberfin-office:/$ sudo ls -la /.
total 26
d-wx--x--x  22 root root   680 2009-01-18 17:01 .
d-wx--x--x  22 root root   680 2009-01-18 17:01 ..
drwxr-xr-x   2 root root  2896 2008-12-18 15:01 bin
drwxr-xr-x   4 root root  1024 2008-12-18 15:03 boot
lrwxrwxrwx   1 root root    11 2008-11-17 22:54 cdrom -> media/cdrom
drwxr-xr-x  14 root root 14000 2009-01-19 20:33 dev
drwxr-xr-x 156 root root  7800 2009-01-19 20:32 etc
drwxr-xr-x   6 root root   160 2009-01-04 13:09 home
lrwxrwxrwx   1 root root    32 2008-12-05 01:08 initrd.img -> boot/initrd.img-2.6.27-9-generic
lrwxrwxrwx   1 root root    32 2008-11-17 23:16 initrd.img.old -> boot/initrd.img-2.6.27-7-generic
drwxr-xr-x  15 root root  5224 2009-01-09 08:40 lib
drwxr-xr-x   4 root root  3048 2008-11-17 23:31 lib32
lrwxrwxrwx   1 root root     4 2008-11-17 22:54 lib64 -> /lib
drwxr-xr-x   5 root root   264 2009-01-19 20:32 media
drwxr-xr-x   3 root root    72 2009-01-18 17:04 mnt
drwxr-xr-x   6 root root   160 2009-01-19 15:57 opt
dr-xr-xr-x 183 root root     0 2009-01-18 16:59 proc
drwxr-xr-x  26 root root   896 2009-01-19 16:00 root
drwxr-xr-x   2 root root  4504 2008-12-18 15:01 sbin
drwxr-xr-x   3 root root    72 2008-12-13 15:14 srv
drwxr-xr-x  12 root root     0 2009-01-18 16:59 sys
drwxrwxrwt  21 root root   776 2009-01-19 20:26 tmp
drwxr-xr-x  13 root root   480 2008-11-18 09:34 usr
drwxr-xr-x  17 root root   408 2009-01-04 11:40 var
lrwxrwxrwx   1 root root    29 2008-12-05 01:08 vmlinuz -> boot/vmlinuz-2.6.27-9-generic
lrwxrwxrwx   1 root root    29 2008-11-17 23:16 vmlinuz.old -> boot/vmlinuz-2.6.27-7-generic
```

and then this command:

```
ls -la /.
```

Which in turn returned this:

```

total 26
d-wx--x--x  22 root root   680 2009-01-18 17:01 .
d-wx--x--x  22 root root   680 2009-01-18 17:01 ..
drwxr-xr-x   2 root root  2896 2008-12-18 15:01 bin
drwxr-xr-x   4 root root  1024 2008-12-18 15:03 boot
lrwxrwxrwx   1 root root    11 2008-11-17 22:54 cdrom -> media/cdrom
drwxr-xr-x  14 root root 14000 2009-01-19 20:33 dev
drwxr-xr-x 156 root root  7800 2009-01-19 20:32 etc
drwxr-xr-x   6 root root   160 2009-01-04 13:09 home
lrwxrwxrwx   1 root root    32 2008-12-05 01:08 initrd.img -> boot/initrd.img-2.6.27-9-generic
lrwxrwxrwx   1 root root    32 2008-11-17 23:16 initrd.img.old -> boot/initrd.img-2.6.27-7-generic
drwxr-xr-x  15 root root  5224 2009-01-09 08:40 lib
drwxr-xr-x   4 root root  3048 2008-11-17 23:31 lib32
lrwxrwxrwx   1 root root     4 2008-11-17 22:54 lib64 -> /lib
drwxr-xr-x   5 root root   264 2009-01-19 20:32 media
drwxr-xr-x   3 root root    72 2009-01-18 17:04 mnt
drwxr-xr-x   6 root root   160 2009-01-19 15:57 opt
dr-xr-xr-x 183 root root     0 2009-01-18 16:59 proc
drwxr-xr-x  26 root root   896 2009-01-19 16:00 root
drwxr-xr-x   2 root root  4504 2008-12-18 15:01 sbin
drwxr-xr-x   3 root root    72 2008-12-13 15:14 srv
drwxr-xr-x  12 root root     0 2009-01-18 16:59 sys
drwxrwxrwt  21 root root   776 2009-01-19 20:26 tmp
drwxr-xr-x  13 root root   480 2008-11-18 09:34 usr
drwxr-xr-x  17 root root   408 2009-01-04 11:40 var
lrwxrwxrwx   1 root root    29 2008-12-05 01:08 vmlinuz -> boot/vmlinuz-2.6.27-9-generic
lrwxrwxrwx   1 root root    29 2008-11-17 23:16 vmlinuz.old -> boot/vmlinuz-2.6.27-7-generic
cyberfin@cyberfin-office:/$ 
```

Is this possible to fix or am I really SOL?

Please someone help!

---

### Post by jespdj on 2009-01-19
That first command made everything in the whole file system readable and writable for everybody. That's VERY unsafe.

There is no easy way to undo this. Backup all your important data and reinstall Ubuntu... :(

---

### Post by cyberfin on 2009-01-19
(sigh)

---

### Post by taurus on 2009-01-19
> **cyberfin said:**
> (sigh)

If you took a command from someone on IRC and ran it without knowing exactly what it would do to your system, then why don't you take up the issue with that person?

---

### Post by adamlau on 2009-01-19
Just in case you have reservations regarding what jespdj recommended, I'll second his thoughts :( .

---

### Post by sisco311 on 2009-01-19
bah. see my post below

---

### Post by Iowan on 2009-01-19
> **taurus said:**
> If you took a command from someone on IRC and ran it without knowing exactly what it would do to your system, then why don't you take up the issue with that person?As I read it, the IRC advice was to run **ls -la /**

File permissions don't (all) LOOK like 777 - in fact, they look pretty much like my system.  Maybe you were saved by a syntax error?

---

### Post by drubin on 2009-01-19
> **adamlau said:**
> Just in case you have reservations regarding what jespdj recommended, I'll second his thoughts :( .

> **jespdj said:**
> That first command made everything in the whole file system readable and writable for everybody. That's VERY unsafe.

There is no easy way to undo this. Backup all your important data and reinstall Ubuntu... :(

[LIST=1]
[*]Take the system off the internet.  After it is offline you can take your time about backing up/re-installing
[*]Back up all important data. 
[*]Maybe take a snap shot of the system just for verification/checks after to check if the system has been comprimised. 
[*]**Format**
[*]Fresh clean install
[/LIST]


This isn't as bad as removing ALL your data but comes very close to it. Any form of hole/bug found in software could execute any file on your system very very very unsafe.

Hope this helps you.

---

### Post by TreeFinger on 2009-01-19
what dir did you run this command from?

if you did it from your root dir you are screwed...

but it doesn't seem like you did.


"." made it your current dir...

---

### Post by sisco311 on 2009-01-19
well
```
chmod 777 /path/to/dir **-r**
chmod: cannot access `777': No such file or directory
```

from man chmod:
```
 -R, --recursive
              change files and directories recursively

```

**linux is case sensitive!!!**


in the above command:

-r is interpreted as *remove read permission* ([COLOR="Red"]NOT[/COLOR] recursively)
777 and /path/to/dir are interpreted as paths to directories.

OP: you need to restore the r (read) permission on /

```
sudo chmod +r /
```

if you can't use your system, then boot a live cd, mount the root ("/")
partition and change the permissions to 755:
```
sudo chmod 755 /media/root
```(assuming that the partition is mounted in /media/root)

---

### Post by Iowan on 2009-01-19
My system...```
drwxr-xr-x  21 root root  4096 2008-12-01 05:02 .
drwxr-xr-x  21 root root  4096 2008-12-01 05:02 ..

```
I'm a little surprised it changed even that. 
 man page suggests the option comes before the file name: **chmod -r /** would remove all read.
... but, nevertheless, that is what it appears to have done.

---

### Post by sisco311 on 2009-01-19
> **Iowan said:**
> My system...```
drwxr-xr-x  21 root root  4096 2008-12-01 05:02 .
drwxr-xr-x  21 root root  4096 2008-12-01 05:02 ..

```
I'm a little surprised it changed even that. 
 man page suggests the option comes before the file name: **chmod -r /** would remove all read.
... but, nevertheless, that is what it appears to have done.

yes, it's strange:
```

[sisco@acme ~]$ touch /tmp/myfile
[sisco@acme ~]$ ls -l /tmp/myfile 
-rw-r--r-- 1 sisco users 0 2009-01-20 01:54 /tmp/myfile
[sisco@acme ~]$ chmod /tmp/myfile -r
[sisco@acme ~]$ ls -l /tmp/myfile 
--w------- 1 sisco users 0 2009-01-20 01:54 /tmp/myfile
[sisco@acme ~]$ chmod /tmp/myfile +r
chmod: invalid mode: `/tmp/myfile'
Try `chmod --help' for more information.
[sisco@acme ~]$ chmod +r /tmp/myfile 
[sisco@acme ~]$ ls -l /tmp/myfile 
-rw-r--r-- 1 sisco users 0 2009-01-20 01:54 /tmp/myfile
[sisco@acme ~]$ chmod +x /tmp/myfile 
[sisco@acme ~]$ ls -l /tmp/myfile 
-rwxr-xr-x 1 sisco users 0 2009-01-20 01:54 /tmp/myfile
[sisco@acme ~]$ chmod /tmp/myfile -x
[sisco@acme ~]$ chmod /tmp/myfile +x
chmod: invalid mode: `/tmp/myfile'
Try `chmod --help' for more information.

```

you can use chmod /path -MODE to remove a permission, but
chmod /path +MODE returns an error.

```
chmod --version
chmod (GNU coreutils) 6.12
Copyright (C) 2008 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is **NO WARRANTY**, to the extent permitted by law.

Written by David MacKenzie and Jim Meyering.
[sisco@acme ~]$ uname -a
Linux acme 2.6.27-ARCH #1 SMP PREEMPT Sun Dec 21 09:13:30 UTC 2008 x86_64 AMD Sempron(tm) Processor 2800+ AuthenticAMD GNU/Linux

```

bug or feature?
:evil:

---

### Post by cyberfin on 2009-01-20
Ok, basically I did not change all of my files because this is the contents of /etc:

```
cyberfin@cyberfin-office:/etc$ ls -la 
total 1057
drwxr-xr-x 156 root root      7800 2009-01-19 20:32 .
d-wx--x--x  22 root root       680 2009-01-18 17:01 ..
drwxr-xr-x   8 root root      1792 2009-01-16 09:01 acpi
-rw-r--r--   1 root root      2986 2008-10-29 22:05 adduser.conf
-rw-r--r--   1 root root        46 2009-01-17 13:37 adjtime
-rw-r--r--   1 root root         0 2008-12-10 22:32 akiradnews.conf
drwxr-xr-x   2 root root      6360 2009-01-09 08:42 alternatives
-rw-r--r--   1 root root       395 2008-09-03 01:38 anacrontab
drwxr-xr-x   7 root root       352 2009-01-04 15:55 apache2
drwxr-xr-x   6 root root       160 2008-10-29 22:12 apm
drwxr-xr-x   2 root root       184 2008-11-28 08:44 apparmor
drwxr-xr-x   6 root root       304 2009-01-16 09:01 apparmor.d
drwxr-xr-x   3 root root       112 2008-10-29 22:21 apport
drwxr-xr-x   4 root root       384 2009-01-09 08:37 apt
-rw-r-----   1 root daemon     144 2008-07-10 17:02 at.deny
drwxr-xr-x   3 root root       176 2008-12-25 18:17 avahi
-rw-r--r--   1 root root      1733 2008-05-12 20:49 bash.bashrc
-rw-r--r--   1 root root    216757 2008-06-19 21:18 bash_completion
drwxr-xr-x   2 root root       224 2009-01-16 09:01 bash_completion.d
drwxr-xr-x   2 root root       112 2008-10-29 22:05 belocs
-rw-r--r--   1 root root       332 2008-09-29 11:20 bindresvport.blacklist
-rw-r--r--   1 root root       676 2009-01-17 12:25 blkid.tab
-rw-r--r--   1 root root       655 2009-01-17 12:25 blkid.tab.old
drwxr-xr-x   2 root root       208 2008-10-29 22:27 bluetooth
-rw-r--r--   1 root root      6924 2008-06-19 05:52 bogofilter.cf
drwxr-xr-x   2 root root        96 2008-10-29 22:16 bonobo-activation
-rw-r--r--   1 root root        33 2008-10-29 22:26 brlapi.key
drwxr-xr-x   2 root root      3072 2008-10-29 22:26 brltty
-rw-r--r--   1 root root     15596 2008-08-06 11:10 brltty.conf
drwxr-xr-x   3 root root        72 2008-10-29 22:05 ca-certificates
-rw-r--r--   1 root root      6256 2008-12-05 19:52 ca-certificates.conf
-rw-r--r--   1 root root      6204 2008-10-29 22:05 ca-certificates.conf.dpkg-old
drwxr-xr-x   2 root root        72 2008-10-29 22:19 calendar
drwxr-s---   2 root dip         96 2008-12-18 15:02 chatscripts
drwxr-xr-x   4 root root       184 2008-12-06 20:40 clamav
drwxr-xr-x   2 root root        72 2008-10-29 22:21 compizconfig
drwxr-xr-x   4 root root       104 2008-10-29 22:09 ConsoleKit
drwxr-xr-x   2 root root      1208 2008-12-18 15:02 console-setup
drwxr-xr-x   3 root root        72 2008-10-29 22:15 console-tools
drwxr-xr-x   2 root root       128 2009-01-04 11:16 cron.d
drwxr-xr-x   2 root root       384 2009-01-09 08:42 cron.daily
drwxr-xr-x   2 root root        80 2008-10-29 22:20 cron.hourly
drwxr-xr-x   2 root root       128 2008-10-29 22:20 cron.monthly
-rw-r--r--   1 root root       724 2008-09-09 21:52 crontab
drwxr-xr-x   2 root root       248 2009-01-04 15:21 cron.weekly
drwxr-xr-x   4 root lp         664 2009-01-18 17:46 cups
-rw-r--r--   1 root root        89 2008-12-13 15:14 cvs-cron.conf
-rw-r--r--   1 root root       126 2008-12-13 15:14 cvs-pserver.conf
drwxr-xr-x   5 root root       192 2008-10-29 22:26 dbus-1
-rw-r--r--   1 root root      2969 2008-10-10 12:32 debconf.conf
-rw-r--r--   1 root root        10 2007-04-01 13:47 debian_version
drwxr-xr-x   3 root root      1032 2009-01-16 09:01 default
drwxr-xr-x   4 root root       312 2008-10-29 22:18 defoma
-rw-r--r--   1 root root       600 2008-06-26 10:33 deluser.conf
drwxr-xr-x   2 root root        80 2008-10-29 22:05 depmod.d
drwxr-xr-x   4 root root       192 2008-11-18 00:12 dhcp3
drwxr-xr-x   2 root root        72 2008-11-17 23:35 dictionaries-common
drwxr-xr-x   3 root root       160 2008-11-17 23:35 dkms
drwxr-xr-x   2 root root        48 2008-10-15 12:09 dm
drwxr-xr-x   3 root root        80 2008-10-29 22:13 doc-base
drwxr-xr-x   3 root root       160 2008-11-17 23:35 dpkg
-rw-r--r--   1 root root        34 2008-02-19 05:33 e2fsck.conf
drwxr-xr-x   3 root root        80 2008-10-29 22:11 emacs
-rw-r--r--   1 root root        79 2008-10-29 22:05 environment
drwxr-xr-x   2 root root        72 2008-10-29 22:17 esound
drwxr-xr-x   2 root root       568 2008-10-29 22:31 event.d
-rw-r--r--   1 root root      8530 2008-10-04 00:44 ffserver.conf
drwxr-xr-x   4 root root        96 2008-10-29 22:13 firefox-3.0
drwxr-xr-x   4 root root       168 2008-10-29 22:16 fonts
drwxr-xr-x   3 root root       136 2008-10-29 22:16 foomatic
-rw-r--r--   1 root root       679 2008-11-17 23:16 fstab
-rw-r-----   1 root fuse       216 2008-09-25 18:06 fuse.conf
-rw-r--r--   1 root root      2689 2008-03-26 18:44 gai.conf
drwxr-xr-x   2 root root        72 2008-10-29 22:26 gamin
drwxr-xr-x   7 root root       208 2008-10-29 22:10 gconf
drwxr-xr-x   7 root root       504 2008-12-16 00:32 gdm
-rw-r--r--   1 root root       588 2008-07-04 10:10 GeoIP.conf.default
drwxr-xr-x   2 root root       104 2008-12-18 11:41 gftp
drwxr-xr-x   3 root root       136 2008-11-17 23:36 ggi
drwxr-xr-x   3 root root        72 2008-10-29 22:13 gimp
drwxr-xr-x   4 root root       128 2008-11-30 10:25 gnome
drwxr-xr-x   2 root root        88 2008-10-29 22:21 gnome-app-install
drwxr-xr-x   3 root root        72 2008-10-29 22:13 gnome-system-tools
drwxr-xr-x   3 root root        72 2008-10-29 22:09 gnome-vfs-2.0
-rw-r--r--   1 root root     10852 2007-04-28 04:27 gnome-vfs-mime-magic
drwxr-xr-x   2 root root       168 2008-12-18 15:02 gre.d
drwxr-xr-x   2 root root       112 2008-10-29 22:19 groff
-rw-r--r--   1 root root      1077 2009-01-04 15:22 group
-rw-------   1 root root      1088 2009-01-04 13:10 group-
drwxr-xr-x   2 root root        80 2008-10-29 22:20 grub.d
-rw-r-----   1 root shadow     911 2009-01-04 15:22 gshadow
-rw-------   1 root root       919 2009-01-04 13:10 gshadow-
drwxr-xr-x   2 root root      1576 2008-12-12 21:32 gtk
drwxr-xr-x   2 root root        88 2008-10-29 22:16 gtk-2.0
drwxr-xr-x   2 root root       208 2008-11-28 16:27 gxine
drwxr-xr-x   3 root root        72 2008-10-29 22:14 hal
-rw-r--r--   1 root root      4793 2008-06-19 10:47 hdparm.conf
-rw-r--r--   1 root root       418 2008-10-29 22:23 hesiod.conf
-rw-r--r--   1 root root        92 2008-08-08 19:53 host.conf
-rw-r--r--   1 root root        16 2008-11-17 23:07 hostname
-rw-r--r--   1 root root       368 2008-11-19 20:18 hosts
-rw-r--r--   1 root root       287 2008-11-19 20:10 hosts~
-rw-r--r--   1 root root       579 2008-10-29 22:24 hosts.allow
-rw-r--r--   1 root root       878 2008-10-29 22:24 hosts.deny
drwxr-xr-x   2 root root        80 2008-10-29 22:19 hp
drwxr-xr-x   2 root root       112 2008-10-29 22:23 hwtest.d
-rw-r--r--   1 root root         0 2009-01-16 09:01 inetd.conf
drwxr-xr-x   2 root root      3080 2009-01-16 09:01 init.d
drwxr-xr-x   5 root root       216 2008-11-28 08:44 initramfs-tools
-rw-r--r--   1 root root      1723 2007-10-02 16:35 inputrc
drwxr-xr-x   2 root root       240 2008-10-29 22:05 iproute2
-rw-r--r--   1 root root        19 2008-10-20 14:27 issue
-rw-r--r--   1 root root        12 2008-10-20 14:27 issue.net
drwxr-xr-x   3 root root        72 2008-11-17 23:59 java
drwxr-xr-x   3 root root        80 2008-11-17 23:44 .java
drwxr-xr-x   5 root root       608 2008-11-17 23:44 java-6-openjdk
drwxr-xr-x   4 root root       392 2008-11-17 23:45 java-6-sun
drwxr-xr-x   3 root root       120 2008-10-29 22:15 kbd
drwxr-xr-x   4 root root       472 2008-12-22 20:19 kde3
drwxr-xr-x   3 root root       104 2008-12-13 12:45 kde4
-rw-r--r--   1 root root        89 2008-10-16 13:21 kde4rc
-rw-r--r--   1 root root       144 2008-10-16 13:21 kderc
-rw-r--r--   1 root root        18 2008-10-16 13:21 kde-user-profile
drwxr-xr-x   5 root root       144 2008-10-29 22:31 kernel
-rw-r--r--   1 root root       167 2008-11-17 23:16 kernel-img.conf
-rw-r--r--   1 root root      1129 2008-01-05 00:55 ksysguarddrc
drwxr-xr-x   2 root root       144 2008-12-13 12:45 kubuntu-default-settings
drwxr-xr-x  10 root root       320 2008-10-29 22:20 laptop-mode
drwxr-xr-x   2 root root        80 2008-10-29 22:06 ldap
-rw-r--r--   1 root root    122220 2009-01-16 09:02 ld.so.cache
-rw-r--r--   1 root root        34 2008-10-29 22:04 ld.so.conf
drwxr-xr-x   2 root root       192 2008-11-17 23:34 ld.so.conf.d
-rw-r--r--   1 root root      3578 2008-10-10 16:54 lftp.conf
-rw-r--r--   1 root root        20 2008-05-03 03:29 libao.conf
drwxr-xr-x   2 root root       104 2008-11-18 18:45 libgda-3.0
drwxr-xr-x   2 root root        48 2008-06-19 15:12 libpaper.d
-rw-r--r--   1 root root      2586 2008-03-11 12:02 locale.alias
-rw-r--r--   1 root root      2593 2008-11-17 23:15 localtime
drwxr-xr-x   5 root root       160 2009-01-04 11:15 logcheck
-rw-r--r--   1 root root      9676 2008-12-13 12:10 login.defs
-rw-r--r--   1 root root       599 2008-10-09 09:12 logrotate.conf
drwxr-xr-x   2 root root       488 2009-01-16 09:01 logrotate.d
drwxr-xr-x   2 root root        48 2008-09-16 14:53 lsb-base
-rw-r--r--   1 root root      3820 2008-03-10 20:00 lsb-base-logging.sh
-rw-r--r--   1 root root        99 2008-10-20 14:07 lsb-release
-rw-r--r--   1 root root     13144 2008-07-02 18:00 ltrace.conf
-rw-r--r--   1 root root       111 2008-07-11 12:24 magic
-rw-r--r--   1 root root       111 2008-07-11 12:24 magic.mime
-rw-r--r--   1 root root     29914 2009-01-19 15:08 mailcap
-rw-r--r--   1 root root       449 2008-06-19 14:50 mailcap.order
-rw-r--r--   1 root root      4630 2008-07-11 17:03 manpath.config
drwxr-xr-x   2 root root       264 2009-01-04 21:40 mediawiki
drwxr-xr-x   2 root root        72 2008-11-17 23:33 menu
drwxr-xr-x   2 root root       184 2008-11-17 23:36 menu-methods
-rw-r--r--   1 root root     21373 2008-06-19 14:50 mime.types
-rw-r--r--   1 root root       803 2008-10-13 15:13 mke2fs.conf
drwxr-xr-x   3 root root       560 2009-01-16 09:01 modprobe.d
-rw-r--r--   1 root root       212 2008-11-17 23:15 modules
drwxr-xr-x   4 root root       152 2008-10-29 22:22 mono
lrwxrwxrwx   1 root root        13 2008-11-17 22:54 motd -> /var/run/motd
-rw-r--r--   1 root root       346 2008-10-29 22:05 motd.tail
drwxr-xr-x   2 root root       144 2008-11-17 23:44 mplayer
-rw-r--r--   1 root root       969 2009-01-19 20:32 mtab
-rw-r--r--   1 root root       624 2008-05-29 22:55 mtools.conf
drwxr-xr-x   3 root root       160 2009-01-04 15:23 mysql
drwxr-xr-x   2 root root       112 2009-01-04 13:10 mythtv
-rw-r--r--   1 root root      7672 2008-09-24 10:38 nanorc
-rw-r--r--   1 root root      2064 2006-11-23 20:33 netscsid.conf
drwxr-xr-x   6 root root       232 2008-12-07 12:04 network
drwxr-xr-x   4 root root       160 2008-12-18 15:02 NetworkManager
-rw-r--r--   1 root root        91 2008-08-08 19:53 networks
-rw-r--r--   1 root root       513 2008-10-29 22:29 nsswitch.conf
drwxr-xr-x   2 root root       120 2008-10-29 22:21 obex-data-server
drwxr-xr-x   2 root root        48 2008-09-01 09:15 ODBCDataSources
-rw-r--r--   1 root root         0 2008-09-01 09:15 odbc.ini
-rw-r--r--   1 root root         0 2008-09-01 09:15 odbcinst.ini
-r--r--r--   1 root root      1520 2008-11-18 09:38 opasswd_a
drwxr-xr-x   2 root root        80 2008-11-17 23:44 openal
drwxr-xr-x   2 root root       184 2009-01-16 09:01 openoffice
-rw-r--r--   1 root root       138 2008-10-28 14:59 opera6rc
-rw-r--r--   1 root root        53 2008-10-28 14:59 opera6rc.fixed
drwxr-xr-x   3 root root        72 2008-12-22 20:19 opt
-r--------   1 root root       908 2008-11-18 09:38 oshadow_a
-rw-r--r--   1 root root       552 2008-10-16 06:32 pam.conf
drwxr-xr-x   2 root root       768 2009-01-16 09:01 pam.d
drwxr-xr-x   2 root root        80 2008-10-29 22:16 pango
-rw-r--r--   1 root root         7 2008-11-17 23:16 papersize
-rw-r--r--   1 root root      1756 2009-01-04 15:22 passwd
-rw-------   1 root root      1792 2009-01-04 13:10 passwd-
drwxr-xr-x   2 root root        80 2008-10-29 22:24 pcmcia
drwxr-xr-x   5 root root       120 2008-10-29 22:20 perl
drwxr-xr-x   5 root root       120 2009-01-04 11:54 php5
drwxr-xr-x   2 root root       256 2009-01-04 15:09 phpmyadmin
drwxr-xr-x   5 root root       120 2008-10-29 22:14 pm
-rw-r--r--   1 root root      7649 2008-10-29 22:24 pnm2ppa.conf
drwxr-xr-x   2 root root        80 2008-10-29 22:26 PolicyKit
-rw-r--r--   1 root root       342 2008-11-17 23:15 popularity-contest.conf
drwxr-xr-x   4 root root       104 2008-10-29 22:12 power
drwxr-xr-x   8 root dip        440 2008-12-18 15:02 ppp
-rw-r--r--   1 root root       497 2008-11-17 23:56 profile
drwxr-xr-x   2 root root        88 2008-10-29 22:22 profile.d
-rw-r--r--   1 root root      2626 2008-06-23 17:12 protocols
drwxr-xr-x   2 root root       144 2009-01-09 08:42 pulse
drwxr-xr-x   2 root root        80 2008-10-29 22:23 purple
-rw-------   1 root root         0 2008-10-29 22:05 .pwd.lock
drwxr-xr-x   2 root root        80 2008-10-29 22:05 python
drwxr-xr-x   2 root root        80 2008-10-29 22:04 python2.5
drwxr-xr-x   2 root root       264 2008-12-13 12:45 qt3
-rw-r--r--   1 root root      1018 2008-06-19 22:05 rarfiles.lst
drwxr-xr-x   2 root root      1280 2009-01-04 15:21 rc0.d
drwxr-xr-x   2 root root      1352 2009-01-04 15:22 rc1.d
drwxr-xr-x   2 root root      1664 2009-01-06 23:12 rc2.d
drwxr-xr-x   2 root root      1624 2009-01-04 15:22 rc3.d
drwxr-xr-x   2 root root      1528 2009-01-04 15:22 rc4.d
drwxr-xr-x   2 root root      1624 2009-01-04 15:22 rc5.d
drwxr-xr-x   2 root root      1288 2009-01-04 15:21 rc6.d
-rwxr-xr-x   1 root root       306 2008-10-29 22:05 rc.local
drwxr-xr-x   2 root root      1288 2008-10-29 22:26 rcS.d
drwxr-xr-x   2 root root        96 2008-10-29 22:24 readahead
drwxr-xr-x   3 root root        80 2008-10-29 22:12 resolvconf
-rw-r--r--   1 root root        49 2008-12-07 12:06 resolv.conf
-rw-r--r--   1 root root        75 2008-12-07 12:03 resolv.conf~
-rw-r--r--   1 root root        53 2008-11-18 00:11 resolv.conf.auto
-rwxr-xr-x   1 root root       268 2008-05-03 11:14 rmt
-rw-r--r--   1 root root       887 2008-06-23 17:12 rpc
drwxr-xr-x   2 root root       136 2009-01-09 08:42 samba
drwxr-xr-x   3 root root      2176 2008-10-29 22:24 sane.d
drwxr-xr-x   2 root root        96 2008-10-29 22:26 scim
-rw-r--r--   1 root root      3663 2008-06-13 12:24 screenrc
-rw-r--r--   1 root root      1254 2008-06-09 20:10 securetty
drwxr-xr-x   2 root root       328 2008-11-28 08:42 security
-rw-r--r--   1 root root     85602 2008-07-04 10:17 sensors.conf
-rw-r--r--   1 root root     18449 2008-06-23 17:12 services
drwxr-xr-x   3 root root       432 2008-11-30 10:25 sgml
-rw-r-----   1 root shadow    1030 2009-01-04 15:22 shadow
-rw-------   1 root root      1055 2009-01-04 13:10 shadow-
-rw-r--r--   1 root root       192 2008-12-13 12:10 shells
drwxr-xr-x   2 root root       152 2008-10-29 22:13 skel
drwxr-xr-x   3 root root        72 2008-10-29 22:09 sound
drwxr-xr-x   2 root root       280 2008-11-18 11:49 ssh
drwxr-xr-x   4 root root       128 2009-01-09 08:42 ssl
-r--r-----   1 root root       557 2008-11-17 23:07 sudoers
-rw-r--r--   1 root root        19 2008-08-15 13:44 su-to-rootrc
drwxr-xr-x   2 root root        88 2008-12-12 21:32 synfig
-rw-r--r--   1 root root      2333 2008-12-12 14:52 sysctl.conf
-rw-r--r--   1 root root      2281 2008-10-27 12:17 sysctl.conf~
drwxr-xr-x   2 root root       256 2008-12-11 10:03 sysctl.d
-rw-r--r--   1 root root      1626 2008-08-30 02:41 syslog.conf
-rw-r--r--   1 root root        65 2008-01-05 00:55 systemsettingsrc
drwxr-xr-x   2 root root        72 2008-10-29 22:04 terminfo
drwxr-xr-x  15 root root       400 2009-01-04 12:49 texmf
-rw-r--r--   1 root root        14 2008-11-17 23:15 timezone
drwxr-xr-x   2 root root        80 2008-11-17 23:35 timidity
drwxr-xr-x   2 root root        80 2008-11-30 19:29 tomatoes
-rw-r--r--   1 root root       645 2008-02-08 17:36 ts.conf
-rw-r--r--   1 root root      1260 2008-05-30 08:22 ucf.conf
drwxr-xr-x   3 root root       136 2008-11-18 00:02 udev
drwxr-xr-x   3 root root       264 2008-10-29 22:20 ufw
-rw-r--r--   1 root root       142 2008-07-18 15:39 uniconf.conf
-rw-r--r--   1 root root       214 2008-06-26 16:18 updatedb.conf
drwxr-xr-x   2 root root       112 2008-11-18 00:02 update-manager
drwxr-xr-x   2 root root        48 2008-10-24 07:57 update-notifier
-rw-r--r--   1 root root       116 2008-11-17 23:15 usplash.conf
drwxr-xr-x   2 root root        80 2008-11-24 15:10 vbox
drwxr-xr-x   2 root root       176 2008-11-17 23:36 vga
drwxr-xr-x   2 root root       104 2008-10-29 22:05 vim
drwxr-xr-x   2 root root        96 2008-10-29 22:20 w3m
drwxr-xr-x 112 root root      3408 2009-01-04 11:40 webmin
-rw-r--r--   1 root root      4221 2008-07-25 09:40 wgetrc
drwxr-xr-x   2 root root        80 2008-11-17 23:35 wildmidi
-rw-r--r--   1 root root      1343 2007-01-09 19:39 wodim.conf
drwxr-xr-x   2 root root       112 2008-10-29 22:24 wpa_supplicant
-rw-r-----   1 root dialout     66 2008-10-29 22:25 wvdial.conf
drwxr-xr-x   9 root root       488 2008-12-18 09:21 X11
drwxr-xr-x   5 root root       200 2008-10-29 22:25 xdg
drwxr-xr-x   2 root root       432 2008-11-30 10:25 xml
drwxr-xr-x   2 root root        88 2008-12-18 15:02 xulrunner-1.9
-rw-r--r--   1 root root       461 2008-04-03 21:33 zsh_command_not_found
```

I ran the command from /media/GOLIATH which is an external usb plugged hd. I had just formated a new partition of it to reiserfs and needed to make it very accessible (on all my systems without exception). I therefore entered the chmod 777 command. The intention was to do it in the local folder, but it was late and I was tired.

So assuming that I actually have only changed the permissions in "/"...

How can I change it back? Do I need to change each folder at a time? If I reboot without fixing this am I going to be up shootcreeck and without a paddle? Will Larry King wear suspenders this week?

Thank you for your input guys, I was just about to throw the towel in (peer pressure of "hey you're SOL, you need to reinstall").

Thanks again.

---

### Post by cyberfin on 2009-01-20
Oh and another thing I forgot to mention; I can open "/" in nautilus but I only see two folders /media and /mnt.

If I go t to / in terminal and do ls it says ls: cannot open directory .: Permission denied

Ironically I did an 777 so I thought if anything I would have been able to see /'s underwear.

Anyway, any help will be veeeeeery appreciated!

---

### Post by cyberfin on 2009-01-20
bump?

---

### Post by sisco311 on 2009-01-20
> 

So assuming that I actually have only changed the permissions in "/"...

How can I change it back? Do I need to change each folder at a time? If I reboot without fixing this am I going to be up shootcreeck and without a paddle? Will Larry King wear suspenders this week?

Thank you for your input guys, I was just about to throw the towel in (peer pressure of "hey you're SOL, you need to reinstall").

Thanks again.

There are three types of access restrictions: read(4), write(2) and execute(1). There are also three types of user restrictions: owner, group and other.

You can changes this permissions with:
[list=a]
[*]octal numbers:
```
chmod 777 /path/to/dir
```
[*]letters:
```
chmod u+rwx,g-r /path/to/dir
```
[/list]
more details here:[uhelp]community/FilePermissions[/uhelp]

The command:
```
chmod -r 777 /path
``` removes the read permission from the 777 directory(error: *chmod: cannot access `777': No such file or directory*) and from /path directory. To recursievly change the permissions you have to use -R (uppercase r).


> How can I change it back? Do I need to change each folder at a time?

"/" is a single directory. To restore the permissions run:
```
sudo chmod 755 /
```
or with letters:
```
sudo chmod u=rwx,g=rx,o=rx /
```

> If I reboot without fixing this am I going to be up shootcreeck and without a paddle? 

Boot a Live CD, mount your "/" partition and restore the permissions. 

[list=1]
[*]list the partitions:
```
sudo fdisk -l
```
[*]create a mount point:
```
sudo mkdir /media/root
```
[*]mount the partition:
```
sudo mount -o defaults /dev/sd**XY** /media/root
```
[*]restore the permissions:
```
sudo chmod 755 /media/root
```
[*]reboot
[/list]
If you need more help with this, post the output of 1.

> Will Larry King wear suspenders this week?
Yes, of course. :)

---

### Post by cyberfin on 2009-01-20
Thank you sisco311. Disaster has been averted. Turns out that I had only managed to change the read permission of / therefore the first command you suggested worked like a charm.

For all posters out there that suggest to reinstall as soon as they see the numbers 777: read up or shut up. And read the sticky of this section: [>> Telling people to reinstall for every issue is not acceptable. <<]("http://ubuntuforums.org/showthread.php?t=1010875")   I saved an awful lot of time by asking the right questions and not rushing to the solution. I'm no linux expert but thankfully I had the right feeling about this one.

I hope this thread will help someone in the future.

Thanks to everyone.

---

### Post by drubin on 2009-01-21
> **cyberfin said:**
> For all posters out there that suggest to reinstall as soon as they see the numbers 777: read up or shut up. And read the sticky of this section: [>> Telling people to reinstall for every issue is not acceptable. <<]("http://ubuntuforums.org/showthread.php?t=1010875")   I saved an awful lot of time by asking the right questions and not rushing to the solution. I'm no linux expert but thankfully I had the right feeling about this one.

There was an announcement posted by jdong - ATTENTION ALL USERS: Malicious Commands . It has since expired but it stated to not run commands that you do not know exactly what they will do.

As I suggested to take the PC offline before making any decisions. or re-installing.

I am glad I was wrong. but this should serve as a reminder/warning to all others that run commands with out fully understanding what they do.

---

### Post by cyberfin on 2009-01-21
To justify myself: as stated I was tired and did make a mistake. However, to expect that a linux intermediate user (let's call them normal users) is supposed to know exactly what they execute in the terminal is not viable, mainly because irc, these forums and many other pages give lists of commands, usually to solve problems, that the users will go and execute blindfolded. They trust these commands because they do not understand enough of the problem to solve it themselves and have been advised to do so by a person.

To justify your answer: Linux users that open up a terminal should indeed know a short list of the no-no commands. I know what the chmod 777 command does in principle and avoid it like the plague, however in this case it was supposed to be run for an external HD. Again, it was my mistake. I should have been more careful.

A more neutral comment: Independently of carelessness of users or help-posters (whether it was for executing a command without thinking twice, or not reading the full post, analysing it carefully and then giving advice), I believe that the forums are a great resource for information and help. If this experience has taught me anything (and not the hard way, thankfully, this time) it is that I can wait and have a bit more patience and seek second opinions when it comes to deciding on an answer to solve the problem... and not execute sudo chmod 777 in root, of course.

Thank you all.

---

