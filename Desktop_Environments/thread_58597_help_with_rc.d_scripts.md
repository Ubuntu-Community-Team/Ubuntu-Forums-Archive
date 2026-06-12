---
title: "help with rc.d scripts"
date: 2005-08-20
forum: Desktop Environments
---

### Post by engos on 2005-08-20
while trying to customise my rc scripts, i made a mistake and now the system cant start :/

please, type this:

ls -lah /etc/rc0.d /etc/rc1.d /etc/rc2.d /etc/rc3.d /etc/rc4.d /etc/rc5.d etc/rc6.d /etc/rcS.d

and paste the result here, then i can restore my links,
thanks []s

---

### Post by GeneralZod on 2005-08-21
Here's mine:

```

ls: etc/rc6.d: No such file or directory
/etc/rc0.d:
total 8.0K
drwxr-xr-x    2 root root 4.0K 2005-08-12 19:06 .
drwxr-xr-x  109 root root 4.0K 2005-08-21 10:14 ..
lrwxrwxrwx    1 root root   13 2005-07-17 20:33 K01kdm -> ../init.d/kdm
lrwxrwxrwx    1 root root   18 2005-08-12 19:06 K01splashyZ -> ../init.d/splashyZ
lrwxrwxrwx    1 root root   19 2005-08-12 19:06 K10splashy10 -> ../init.d/splashy10
lrwxrwxrwx    1 root root   14 2005-07-17 20:33 K11cron -> ../init.d/cron
lrwxrwxrwx    1 root root   19 2005-07-17 20:33 K15fetchmail -> ../init.d/fetchmail
lrwxrwxrwx    1 root root   16 2005-07-17 20:33 K19cupsys -> ../init.d/cupsys
lrwxrwxrwx    1 root root   15 2005-07-17 20:33 K20acpid -> ../init.d/acpid
lrwxrwxrwx    1 root root   22 2005-07-17 20:33 K20acpi-support -> ../init.d/acpi-support
lrwxrwxrwx    1 root root   14 2005-07-17 20:33 K20alsa -> ../init.d/alsa
lrwxrwxrwx    1 root root   14 2005-07-17 20:33 K20apmd -> ../init.d/apmd
lrwxrwxrwx    1 root root   16 2005-07-17 20:33 K20dbus-1 -> ../init.d/dbus-1
lrwxrwxrwx    1 root root   15 2005-07-17 20:33 K20inetd -> ../init.d/inetd
lrwxrwxrwx    1 root root   17 2005-07-17 20:33 K20makedev -> ../init.d/makedev
lrwxrwxrwx    1 root root   20 2005-07-17 20:33 K20nvidia-glx -> ../init.d/nvidia-glx
lrwxrwxrwx    1 root root   17 2005-07-17 20:33 K20postfix -> ../init.d/postfix
lrwxrwxrwx    1 root root   19 2005-07-17 20:33 K20powernowd -> ../init.d/powernowd
lrwxrwxrwx    1 root root   15 2005-07-17 20:33 K20rsync -> ../init.d/rsync
lrwxrwxrwx    1 root root   19 2005-08-12 19:06 K20splashy20 -> ../init.d/splashy20
lrwxrwxrwx    1 root root   20 2005-07-17 20:33 K25hwclock.sh -> ../init.d/hwclock.sh
lrwxrwxrwx    1 root root   15 2005-07-17 20:33 K25mdadm -> ../init.d/mdadm
lrwxrwxrwx    1 root root   19 2005-08-12 19:06 K30splashy30 -> ../init.d/splashy30
lrwxrwxrwx    1 root root   19 2005-08-12 19:06 K40splashy40 -> ../init.d/splashy40
lrwxrwxrwx    1 root root   19 2005-08-12 19:06 K50splashy50 -> ../init.d/splashy50
lrwxrwxrwx    1 root root   19 2005-08-12 19:06 K60splashy60 -> ../init.d/splashy60
lrwxrwxrwx    1 root root   19 2005-08-12 19:06 K70splashy70 -> ../init.d/splashy70
lrwxrwxrwx    1 root root   21 2005-07-26 17:56 K74bluez-utils -> ../init.d/bluez-utils
lrwxrwxrwx    1 root root   16 2005-07-17 20:33 K75hdparm -> ../init.d/hdparm
lrwxrwxrwx    1 root root   19 2005-07-17 20:33 K76readahead -> ../init.d/readahead
lrwxrwxrwx    1 root root   13 2005-07-17 20:33 K86ppp -> ../init.d/ppp
lrwxrwxrwx    1 root root   13 2005-07-17 20:33 K89atd -> ../init.d/atd
lrwxrwxrwx    1 root root   17 2005-07-17 20:33 K89hotplug -> ../init.d/hotplug
lrwxrwxrwx    1 root root   15 2005-07-17 20:33 K89klogd -> ../init.d/klogd
lrwxrwxrwx    1 root root   18 2005-07-17 20:33 K90sysklogd -> ../init.d/sysklogd
lrwxrwxrwx    1 root root   18 2005-07-17 20:33 S20sendsigs -> ../init.d/sendsigs
lrwxrwxrwx    1 root root   17 2005-07-17 20:33 S30urandom -> ../init.d/urandom
lrwxrwxrwx    1 root root   22 2005-07-17 20:33 S31umountnfs.sh -> ../init.d/umountnfs.sh
lrwxrwxrwx    1 root root   20 2005-07-17 20:33 S35networking -> ../init.d/networking
lrwxrwxrwx    1 root root   18 2005-07-17 20:33 S36ifupdown -> ../init.d/ifupdown
lrwxrwxrwx    1 root root   18 2005-07-17 20:33 S40umountfs -> ../init.d/umountfs
lrwxrwxrwx    1 root root   14 2005-07-17 20:33 S49evms -> ../init.d/evms
lrwxrwxrwx    1 root root   13 2005-07-17 20:33 S50lvm -> ../init.d/lvm
lrwxrwxrwx    1 root root   20 2005-07-17 20:33 S50mdadm-raid -> ../init.d/mdadm-raid
lrwxrwxrwx    1 root root   18 2005-08-12 19:06 S89splashyZ -> ../init.d/splashyZ
lrwxrwxrwx    1 root root   14 2005-07-17 20:33 S90halt -> ../init.d/halt

/etc/rc1.d:
total 8.0K
drwxr-xr-x    2 root root 4.0K 2005-07-31 17:19 .
drwxr-xr-x  109 root root 4.0K 2005-08-21 10:14 ..
lrwxrwxrwx    1 root root   13 2005-07-17 20:33 K01kdm -> ../init.d/kdm
lrwxrwxrwx    1 root root   14 2005-07-17 20:33 K11cron -> ../init.d/cron
lrwxrwxrwx    1 root root   19 2005-07-17 20:33 K15fetchmail -> ../init.d/fetchmail
lrwxrwxrwx    1 root root   16 2005-07-17 20:33 K19cupsys -> ../init.d/cupsys
lrwxrwxrwx    1 root root   15 2005-07-17 20:33 K20acpid -> ../init.d/acpid
lrwxrwxrwx    1 root root   22 2005-07-17 20:33 K20acpi-support -> ../init.d/acpi-support
lrwxrwxrwx    1 root root   14 2005-07-17 20:33 K20alsa -> ../init.d/alsa
lrwxrwxrwx    1 root root   14 2005-07-17 20:33 K20apmd -> ../init.d/apmd
lrwxrwxrwx    1 root root   16 2005-07-17 20:33 K20dbus-1 -> ../init.d/dbus-1
lrwxrwxrwx    1 root root   15 2005-07-17 20:33 K20inetd -> ../init.d/inetd
lrwxrwxrwx    1 root root   17 2005-07-17 20:33 K20makedev -> ../init.d/makedev
lrwxrwxrwx    1 root root   20 2005-07-17 20:33 K20nvidia-glx -> ../init.d/nvidia-glx
lrwxrwxrwx    1 root root   17 2005-07-17 20:33 K20postfix -> ../init.d/postfix
lrwxrwxrwx    1 root root   19 2005-07-17 20:33 K20powernowd -> ../init.d/powernowd
lrwxrwxrwx    1 root root   15 2005-07-17 20:33 K20rsync -> ../init.d/rsync
lrwxrwxrwx    1 root root   15 2005-07-17 20:33 K25mdadm -> ../init.d/mdadm
lrwxrwxrwx    1 root root   21 2005-07-26 17:56 K74bluez-utils -> ../init.d/bluez-utils
lrwxrwxrwx    1 root root   13 2005-07-17 20:33 K86ppp -> ../init.d/ppp
lrwxrwxrwx    1 root root   13 2005-07-17 20:33 K89atd -> ../init.d/atd
lrwxrwxrwx    1 root root   15 2005-07-17 20:33 K89klogd -> ../init.d/klogd
lrwxrwxrwx    1 root root   18 2005-07-17 20:33 K90sysklogd -> ../init.d/sysklogd
lrwxrwxrwx    1 root root   16 2005-07-17 20:33 S20single -> ../init.d/single

/etc/rc2.d:
total 8.0K
drwxr-xr-x    2 root root 4.0K 2005-08-12 19:06 .
drwxr-xr-x  109 root root 4.0K 2005-08-21 10:14 ..
lrwxrwxrwx    1 root root   17 2005-07-17 20:33 K11anacron -> ../init.d/anacron
lrwxrwxrwx    1 root root   17 2005-07-17 20:33 S05vbesave -> ../init.d/vbesave
lrwxrwxrwx    1 root root   18 2005-07-17 20:33 S10sysklogd -> ../init.d/sysklogd
lrwxrwxrwx    1 root root   15 2005-07-17 20:33 S11klogd -> ../init.d/klogd
lrwxrwxrwx    1 root root   14 2005-07-17 20:33 S12alsa -> ../init.d/alsa
lrwxrwxrwx    1 root root   13 2005-07-17 20:33 S14ppp -> ../init.d/ppp
lrwxrwxrwx    1 root root   16 2005-07-17 20:33 S19cupsys -> ../init.d/cupsys
lrwxrwxrwx    1 root root   15 2005-07-17 20:33 S20acpid -> ../init.d/acpid
lrwxrwxrwx    1 root root   14 2005-07-17 20:33 S20apmd -> ../init.d/apmd
lrwxrwxrwx    1 root root   16 2005-07-17 20:33 S20dbus-1 -> ../init.d/dbus-1
lrwxrwxrwx    1 root root   15 2005-07-17 20:33 S20inetd -> ../init.d/inetd
lrwxrwxrwx    1 root root   17 2005-07-17 20:33 S20makedev -> ../init.d/makedev
lrwxrwxrwx    1 root root   20 2005-07-17 20:33 S20nvidia-glx -> ../init.d/nvidia-glx
lrwxrwxrwx    1 root root   17 2005-07-17 20:33 S20postfix -> ../init.d/postfix
lrwxrwxrwx    1 root root   19 2005-07-17 20:33 S20powernowd -> ../init.d/powernowd
lrwxrwxrwx    1 root root   15 2005-07-17 20:33 S20rsync -> ../init.d/rsync
lrwxrwxrwx    1 root root   13 2005-07-17 20:33 S21kdm -> ../init.d/kdm
lrwxrwxrwx    1 root root   21 2005-07-26 17:56 S25bluez-utils -> ../init.d/bluez-utils
lrwxrwxrwx    1 root root   15 2005-07-17 20:33 S25mdadm -> ../init.d/mdadm
lrwxrwxrwx    1 root root   17 2005-07-17 20:33 S89anacron -> ../init.d/anacron
lrwxrwxrwx    1 root root   13 2005-07-17 20:33 S89atd -> ../init.d/atd
lrwxrwxrwx    1 root root   14 2005-07-17 20:33 S89cron -> ../init.d/cron
lrwxrwxrwx    1 root root   22 2005-07-17 20:33 S99acpi-support -> ../init.d/acpi-support
lrwxrwxrwx    1 root root   19 2005-07-17 20:33 S99fetchmail -> ../init.d/fetchmail
lrwxrwxrwx    1 root root   19 2005-07-17 20:33 S99rmnologin -> ../init.d/rmnologin
lrwxrwxrwx    1 root root   18 2005-08-12 19:06 S99splashyZ -> ../init.d/splashyZ
lrwxrwxrwx    1 root root   23 2005-07-17 20:33 S99stop-bootlogd -> ../init.d/stop-bootlogd

/etc/rc3.d:
total 8.0K
drwxr-xr-x    2 root root 4.0K 2005-08-12 19:06 .
drwxr-xr-x  109 root root 4.0K 2005-08-21 10:14 ..
lrwxrwxrwx    1 root root   17 2005-07-17 20:33 K11anacron -> ../init.d/anacron
lrwxrwxrwx    1 root root   17 2005-07-17 20:33 S05vbesave -> ../init.d/vbesave
lrwxrwxrwx    1 root root   18 2005-07-17 20:33 S10sysklogd -> ../init.d/sysklogd
lrwxrwxrwx    1 root root   15 2005-07-17 20:33 S11klogd -> ../init.d/klogd
lrwxrwxrwx    1 root root   14 2005-07-17 20:33 S12alsa -> ../init.d/alsa
lrwxrwxrwx    1 root root   13 2005-07-17 20:33 S14ppp -> ../init.d/ppp
lrwxrwxrwx    1 root root   16 2005-07-17 20:33 S19cupsys -> ../init.d/cupsys
lrwxrwxrwx    1 root root   15 2005-07-17 20:33 S20acpid -> ../init.d/acpid
lrwxrwxrwx    1 root root   14 2005-07-17 20:33 S20apmd -> ../init.d/apmd
lrwxrwxrwx    1 root root   16 2005-07-17 20:33 S20dbus-1 -> ../init.d/dbus-1
lrwxrwxrwx    1 root root   15 2005-07-17 20:33 S20inetd -> ../init.d/inetd
lrwxrwxrwx    1 root root   17 2005-07-17 20:33 S20makedev -> ../init.d/makedev
lrwxrwxrwx    1 root root   20 2005-07-17 20:33 S20nvidia-glx -> ../init.d/nvidia-glx
lrwxrwxrwx    1 root root   17 2005-07-17 20:33 S20postfix -> ../init.d/postfix
lrwxrwxrwx    1 root root   19 2005-07-17 20:33 S20powernowd -> ../init.d/powernowd
lrwxrwxrwx    1 root root   15 2005-07-17 20:33 S20rsync -> ../init.d/rsync
lrwxrwxrwx    1 root root   13 2005-07-17 20:33 S21kdm -> ../init.d/kdm
lrwxrwxrwx    1 root root   21 2005-07-26 17:56 S25bluez-utils -> ../init.d/bluez-utils
lrwxrwxrwx    1 root root   15 2005-07-17 20:33 S25mdadm -> ../init.d/mdadm
lrwxrwxrwx    1 root root   17 2005-07-17 20:33 S89anacron -> ../init.d/anacron
lrwxrwxrwx    1 root root   13 2005-07-17 20:33 S89atd -> ../init.d/atd
lrwxrwxrwx    1 root root   14 2005-07-17 20:33 S89cron -> ../init.d/cron
lrwxrwxrwx    1 root root   22 2005-07-17 20:33 S99acpi-support -> ../init.d/acpi-support
lrwxrwxrwx    1 root root   19 2005-07-17 20:33 S99fetchmail -> ../init.d/fetchmail
lrwxrwxrwx    1 root root   19 2005-07-17 20:33 S99rmnologin -> ../init.d/rmnologin
lrwxrwxrwx    1 root root   18 2005-08-12 19:06 S99splashyZ -> ../init.d/splashyZ
lrwxrwxrwx    1 root root   23 2005-07-17 20:33 S99stop-bootlogd -> ../init.d/stop-bootlogd

/etc/rc4.d:
total 8.0K
drwxr-xr-x    2 root root 4.0K 2005-08-12 19:06 .
drwxr-xr-x  109 root root 4.0K 2005-08-21 10:14 ..
lrwxrwxrwx    1 root root   17 2005-07-17 20:33 K11anacron -> ../init.d/anacron
lrwxrwxrwx    1 root root   17 2005-07-17 20:33 S05vbesave -> ../init.d/vbesave
lrwxrwxrwx    1 root root   18 2005-07-17 20:33 S10sysklogd -> ../init.d/sysklogd
lrwxrwxrwx    1 root root   15 2005-07-17 20:33 S11klogd -> ../init.d/klogd
lrwxrwxrwx    1 root root   14 2005-07-17 20:33 S12alsa -> ../init.d/alsa
lrwxrwxrwx    1 root root   13 2005-07-17 20:33 S14ppp -> ../init.d/ppp
lrwxrwxrwx    1 root root   16 2005-07-17 20:33 S19cupsys -> ../init.d/cupsys
lrwxrwxrwx    1 root root   15 2005-07-17 20:33 S20acpid -> ../init.d/acpid
lrwxrwxrwx    1 root root   14 2005-07-17 20:33 S20apmd -> ../init.d/apmd
lrwxrwxrwx    1 root root   16 2005-07-17 20:33 S20dbus-1 -> ../init.d/dbus-1
lrwxrwxrwx    1 root root   15 2005-07-17 20:33 S20inetd -> ../init.d/inetd
lrwxrwxrwx    1 root root   17 2005-07-17 20:33 S20makedev -> ../init.d/makedev
lrwxrwxrwx    1 root root   20 2005-07-17 20:33 S20nvidia-glx -> ../init.d/nvidia-glx
lrwxrwxrwx    1 root root   17 2005-07-17 20:33 S20postfix -> ../init.d/postfix
lrwxrwxrwx    1 root root   19 2005-07-17 20:33 S20powernowd -> ../init.d/powernowd
lrwxrwxrwx    1 root root   15 2005-07-17 20:33 S20rsync -> ../init.d/rsync
lrwxrwxrwx    1 root root   13 2005-07-17 20:33 S21kdm -> ../init.d/kdm
lrwxrwxrwx    1 root root   21 2005-07-26 17:56 S25bluez-utils -> ../init.d/bluez-utils
lrwxrwxrwx    1 root root   15 2005-07-17 20:33 S25mdadm -> ../init.d/mdadm
lrwxrwxrwx    1 root root   17 2005-07-17 20:33 S89anacron -> ../init.d/anacron
lrwxrwxrwx    1 root root   13 2005-07-17 20:33 S89atd -> ../init.d/atd
lrwxrwxrwx    1 root root   14 2005-07-17 20:33 S89cron -> ../init.d/cron
lrwxrwxrwx    1 root root   22 2005-07-17 20:33 S99acpi-support -> ../init.d/acpi-support
lrwxrwxrwx    1 root root   19 2005-07-17 20:33 S99fetchmail -> ../init.d/fetchmail
lrwxrwxrwx    1 root root   19 2005-07-17 20:33 S99rmnologin -> ../init.d/rmnologin
lrwxrwxrwx    1 root root   18 2005-08-12 19:06 S99splashyZ -> ../init.d/splashyZ
lrwxrwxrwx    1 root root   23 2005-07-17 20:33 S99stop-bootlogd -> ../init.d/stop-bootlogd

/etc/rc5.d:
total 8.0K
drwxr-xr-x    2 root root 4.0K 2005-08-12 19:06 .
drwxr-xr-x  109 root root 4.0K 2005-08-21 10:14 ..
lrwxrwxrwx    1 root root   17 2005-07-17 20:33 K11anacron -> ../init.d/anacron
lrwxrwxrwx    1 root root   17 2005-07-17 20:33 S05vbesave -> ../init.d/vbesave
lrwxrwxrwx    1 root root   18 2005-07-17 20:33 S10sysklogd -> ../init.d/sysklogd
lrwxrwxrwx    1 root root   15 2005-07-17 20:33 S11klogd -> ../init.d/klogd
lrwxrwxrwx    1 root root   14 2005-07-17 20:33 S12alsa -> ../init.d/alsa
lrwxrwxrwx    1 root root   13 2005-07-17 20:33 S14ppp -> ../init.d/ppp
lrwxrwxrwx    1 root root   16 2005-07-17 20:33 S19cupsys -> ../init.d/cupsys
lrwxrwxrwx    1 root root   15 2005-07-17 20:33 S20acpid -> ../init.d/acpid
lrwxrwxrwx    1 root root   14 2005-07-17 20:33 S20apmd -> ../init.d/apmd
lrwxrwxrwx    1 root root   16 2005-07-17 20:33 S20dbus-1 -> ../init.d/dbus-1
lrwxrwxrwx    1 root root   15 2005-07-17 20:33 S20inetd -> ../init.d/inetd
lrwxrwxrwx    1 root root   17 2005-07-17 20:33 S20makedev -> ../init.d/makedev
lrwxrwxrwx    1 root root   20 2005-07-17 20:33 S20nvidia-glx -> ../init.d/nvidia-glx
lrwxrwxrwx    1 root root   17 2005-07-17 20:33 S20postfix -> ../init.d/postfix
lrwxrwxrwx    1 root root   19 2005-07-17 20:33 S20powernowd -> ../init.d/powernowd
lrwxrwxrwx    1 root root   15 2005-07-17 20:33 S20rsync -> ../init.d/rsync
lrwxrwxrwx    1 root root   13 2005-07-17 20:33 S21kdm -> ../init.d/kdm
lrwxrwxrwx    1 root root   21 2005-07-26 17:56 S25bluez-utils -> ../init.d/bluez-utils
lrwxrwxrwx    1 root root   15 2005-07-17 20:33 S25mdadm -> ../init.d/mdadm
lrwxrwxrwx    1 root root   17 2005-07-17 20:33 S89anacron -> ../init.d/anacron
lrwxrwxrwx    1 root root   13 2005-07-17 20:33 S89atd -> ../init.d/atd
lrwxrwxrwx    1 root root   14 2005-07-17 20:33 S89cron -> ../init.d/cron
lrwxrwxrwx    1 root root   22 2005-07-17 20:33 S99acpi-support -> ../init.d/acpi-support
lrwxrwxrwx    1 root root   19 2005-07-17 20:33 S99fetchmail -> ../init.d/fetchmail
lrwxrwxrwx    1 root root   19 2005-07-17 20:33 S99rmnologin -> ../init.d/rmnologin
lrwxrwxrwx    1 root root   18 2005-08-12 19:06 S99splashyZ -> ../init.d/splashyZ
lrwxrwxrwx    1 root root   23 2005-07-17 20:33 S99stop-bootlogd -> ../init.d/stop-bootlogd

/etc/rcS.d:
total 12K
drwxr-xr-x    2 root root 4.0K 2005-08-12 19:06 .
drwxr-xr-x  109 root root 4.0K 2005-08-21 10:14 ..
-rw-r--r--    1 root root  701 2005-01-07 18:35 README
lrwxrwxrwx    1 root root   17 2005-08-12 19:06 S01splashy -> ../init.d/splashy
lrwxrwxrwx    1 root root   21 2005-07-17 20:33 S02mountvirtfs -> ../init.d/mountvirtfs
lrwxrwxrwx    1 root root   14 2005-07-17 20:33 S04udev -> ../init.d/udev
lrwxrwxrwx    1 root root   18 2005-07-17 20:33 S05bootlogd -> ../init.d/bootlogd
lrwxrwxrwx    1 root root   25 2005-07-17 20:33 S05initrd-tools.sh -> ../init.d/initrd-tools.sh
lrwxrwxrwx    1 root root   19 2005-07-17 20:33 S05keymap.sh -> ../init.d/keymap.sh
lrwxrwxrwx    1 root root   16 2005-07-17 20:33 S07hdparm -> ../init.d/hdparm
lrwxrwxrwx    1 root root   22 2005-07-17 20:33 S10checkroot.sh -> ../init.d/checkroot.sh
lrwxrwxrwx    1 root root   19 2005-08-12 19:06 S10splashy10 -> ../init.d/splashy10
lrwxrwxrwx    1 root root   25 2005-07-17 20:33 S18hwclockfirst.sh -> ../init.d/hwclockfirst.sh
lrwxrwxrwx    1 root root   24 2005-07-17 20:33 S18ifupdown-clean -> ../init.d/ifupdown-clean
lrwxrwxrwx    1 root root   27 2005-07-17 20:33 S20module-init-tools -> ../init.d/module-init-tools
lrwxrwxrwx    1 root root   19 2005-08-12 19:06 S20splashy20 -> ../init.d/splashy20
lrwxrwxrwx    1 root root   26 2005-07-17 20:33 S25libdevmapper1.00 -> ../init.d/libdevmapper1.00
lrwxrwxrwx    1 root root   20 2005-07-17 20:33 S25mdadm-raid -> ../init.d/mdadm-raid
lrwxrwxrwx    1 root root   13 2005-07-17 20:33 S26lvm -> ../init.d/lvm
lrwxrwxrwx    1 root root   14 2005-07-17 20:33 S27evms -> ../init.d/evms
lrwxrwxrwx    1 root root   20 2005-07-17 20:33 S30checkfs.sh -> ../init.d/checkfs.sh
lrwxrwxrwx    1 root root   19 2005-07-17 20:33 S30procps.sh -> ../init.d/procps.sh
lrwxrwxrwx    1 root root   19 2005-08-12 19:06 S30splashy30 -> ../init.d/splashy30
lrwxrwxrwx    1 root root   21 2005-07-17 20:33 S35mountall.sh -> ../init.d/mountall.sh
lrwxrwxrwx    1 root root   21 2005-07-17 20:33 S36mountvirtfs -> ../init.d/mountvirtfs
lrwxrwxrwx    1 root root   19 2005-07-17 20:33 S36udev-mtab -> ../init.d/udev-mtab
lrwxrwxrwx    1 root root   18 2005-07-17 20:33 S38pppd-dns -> ../init.d/pppd-dns
lrwxrwxrwx    1 root root   19 2005-07-17 20:33 S39dns-clean -> ../init.d/dns-clean
lrwxrwxrwx    1 root root   18 2005-07-17 20:33 S39ifupdown -> ../init.d/ifupdown
lrwxrwxrwx    1 root root   19 2005-07-17 20:33 S39readahead -> ../init.d/readahead
lrwxrwxrwx    1 root root   21 2005-07-17 20:33 S40hostname.sh -> ../init.d/hostname.sh
lrwxrwxrwx    1 root root   17 2005-07-17 20:33 S40hotplug -> ../init.d/hotplug
lrwxrwxrwx    1 root root   20 2005-07-17 20:33 S40networking -> ../init.d/networking
lrwxrwxrwx    1 root root   19 2005-08-12 19:06 S40splashy40 -> ../init.d/splashy40
lrwxrwxrwx    1 root root   21 2005-07-17 20:33 S45mountnfs.sh -> ../init.d/mountnfs.sh
lrwxrwxrwx    1 root root   27 2005-07-17 20:33 S48console-screen.sh -> ../init.d/console-screen.sh
lrwxrwxrwx    1 root root   20 2005-07-17 20:33 S50hwclock.sh -> ../init.d/hwclock.sh
lrwxrwxrwx    1 root root   19 2005-08-12 19:06 S50splashy50 -> ../init.d/splashy50
lrwxrwxrwx    1 root root   17 2005-07-17 20:33 S51ntpdate -> ../init.d/ntpdate
lrwxrwxrwx    1 root root   21 2005-07-17 20:33 S55bootmisc.sh -> ../init.d/bootmisc.sh
lrwxrwxrwx    1 root root   17 2005-07-17 20:33 S55urandom -> ../init.d/urandom
lrwxrwxrwx    1 root root   19 2005-08-12 19:06 S60splashy60 -> ../init.d/splashy60
lrwxrwxrwx    1 root root   24 2005-07-17 20:33 S70screen-cleanup -> ../init.d/screen-cleanup
lrwxrwxrwx    1 root root   19 2005-08-12 19:06 S70splashy70 -> ../init.d/splashy70
lrwxrwxrwx    1 root root   21 2005-07-17 20:33 S70xorg-common -> ../init.d/xorg-common
lrwxrwxrwx    1 root root   14 2005-07-17 20:33 S75sudo -> ../init.d/sudo  

```

---

