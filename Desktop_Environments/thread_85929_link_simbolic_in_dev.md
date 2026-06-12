---
title: "link simbolic in /dev"
date: 2005-11-03
forum: Desktop Environments
---

### Post by pminetti on 2005-11-03
Hi, how can I do to put a simbolic link (ln -s) en /dev.
If I do (ln -s), so when I restart the computer there is no link in /dev

ln -s /dev/hdd cdrom


thanks

---

### Post by Xian on 2005-11-03
You need to first be certain you are in /dev, or at least be sure to use the path in that command. For all I can tell from what you posted you just made a symlink in your home directory.

```
$ cd /dev
$ ln -s /dev/hdd cdrom
```

---

### Post by felix_stegerman on 2005-11-03
/dev is managed by udev. All devices and symlinks are created when needed.
To manually add symlinks, you need to modify your udev rules.
Since I'm currently on a Debian Box, I'll need to know what you /etc/udev dir
looks like. Then I can tell you how to add local rules, and what you probably
want to add.

e.g. post the result of ls -laR /etc/udev


Felix

---

### Post by pminetti on 2005-11-03
well i think it's more easy to write in something like rc.local, but I don't find in Ubuntu rc.local
all I want is a simbolic link en /dev because I have problems with some programs, they need /dev/cdrom and ubuntu have /dev/hdd

so in /dev i do ln -s dev/hdd cdrom

but when i restart there is no more link

well you ask and here it is 

thanks

pablo@zeus:~ $ ls -laR /etc/udev
/etc/udev:
total 80
drwxr-xr-x    5 root root 4096 2005-10-14 18:58 .
drwxr-xr-x  113 root root 8192 2005-11-03 21:47 ..
-rw-r--r--    1 root root   68 2005-09-29 11:41 alsa-utils.rules
-rw-r--r--    1 root root  691 2005-09-24 13:41 cd-aliases.rules
-rw-r--r--    1 root root  786 2005-09-24 13:41 cdsymlinks.conf
-rw-r--r--    1 root root  949 2005-09-24 13:41 compat-full.rules
-rw-r--r--    1 root root  965 2005-09-24 13:41 compat.rules
-rw-r--r--    1 root root 4872 2005-09-24 13:41 devfs.rules
-rw-r--r--    1 root root  307 2005-09-24 13:41 hotplugd.rules
-rw-r--r--    1 root root  416 2005-09-24 13:41 links.conf
drwxr-xr-x    2 root root 4096 2005-10-05 02:40 permissions.d
-rw-r--r--    1 root root 2776 2005-09-24 13:41 permissions.rules
drwxr-xr-x    2 root root 4096 2005-10-14 18:58 rules.d
-rw-r--r--    1 root root  246 2005-09-24 13:41 run.rules
drwxr-xr-x    2 root root 4096 2005-10-14 18:54 scripts
-rw-r--r--    1 root root  338 2005-09-24 13:41 simple-cd-aliases.rules
-rw-r--r--    1 root root  368 2005-09-24 13:41 udev.conf
-rw-r--r--    1 root root 3077 2005-09-24 13:41 udev.rules

/etc/udev/permissions.d:
total 12
drwxr-xr-x  2 root root 4096 2005-10-05 02:40 .
drwxr-xr-x  5 root root 4096 2005-10-14 18:58 ..
-rw-r--r--  1 root root 2797 2005-03-29 09:57 udev.permissions

/etc/udev/rules.d:
total 8
drwxr-xr-x  2 root root 4096 2005-10-14 18:58 .
drwxr-xr-x  5 root root 4096 2005-10-14 18:58 ..
lrwxrwxrwx  1 root root   20 2005-10-14 18:21 020_permissions.rules -> ../permissions.rules
lrwxrwxrwx  1 root root   13 2005-10-01 17:32 udev.rules -> ../udev.rules
lrwxrwxrwx  1 root root   12 2005-10-14 18:21 z50_run.rules -> ../run.rules
lrwxrwxrwx  1 root root   19 2005-10-14 18:58 z60_alsa-utils.rules -> ../alsa-utils.rules
lrwxrwxrwx  1 root root   17 2005-10-14 18:21 z70_hotplugd.rules -> ../hotplugd.rules

/etc/udev/scripts:
total 44
drwxr-xr-x  2 root root 4096 2005-10-14 18:54 .
drwxr-xr-x  5 root root 4096 2005-10-14 18:58 ..
-rwxr-xr-x  1 root root 7204 2005-09-24 13:41 cdsymlinks.sh
-rwxr-xr-x  1 root root   97 2005-03-29 09:57 dvb.sh
-rwxr-xr-x  1 root root 1259 2005-09-24 13:41 ide-devfs.sh
-rwxr-xr-x  1 root root  264 2005-09-24 13:41 ide-model.sh
-rwxr-xr-x  1 root root  605 2005-03-29 09:57 inputdev.sh
-rwxr-xr-x  1 root root 1168 2005-03-29 09:57 raid-devfs.sh
-rwxr-xr-x  1 root root 1047 2005-09-24 13:41 removable.sh
-rwxr-xr-x  1 root root 1499 2005-09-24 13:41 scsi-devfs.sh

---

### Post by felix_stegerman on 2005-11-03
OK. You could indeed use a startup script. But local udev rules are nicer.
I also use a local udev rule to create a /dev/ipod symlink for my iPod ;-)

Here's what you should probably do:
# cd /etc/udev
# sudo <your_editor> local.rules
add this line:
BUS="ide", KERNEL="hdd", SYMLINK="cdrom"
# cd rules.d
# sudo ln -s ../local.rules 100-local.rules

I'm not sure whether you can just restart udev (the one in Ubuntu anyway),
so you may want to reboot, or you could try
# sudo /etc/init.d/udev restart

If you want to add more symlinks, use SYMLINK="cdrom cdrw dvd" etc.


Felix

---

### Post by pminetti on 2005-11-04
Great! it works very very well
thanks Felix C. Stegerman

Pablo Minetti

---

