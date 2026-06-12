---
title: "booting time..."
date: 2005-06-21
forum: Desktop Environments
---

### Post by kimes on 2005-06-21
My booting time is getting slower than before so I guess I gotta take some daemons which is started at boot time out.
here is my list.. but I have no idea which is which..

```

lrwxrwxrwx  1 root root 18 2005-06-17 03:41 K08vmware -> /etc/init.d/vmware
lrwxrwxrwx  1 root root 17 2005-05-20 15:45 K11anacron -> ../init.d/anacron
lrwxrwxrwx  1 root root 17 2005-05-20 15:45 S05vbesave -> ../init.d/vbesave
lrwxrwxrwx  1 root root 18 2005-05-20 08:11 S10sysklogd -> ../init.d/sysklogd
lrwxrwxrwx  1 root root 15 2005-05-20 08:11 S11klogd -> ../init.d/klogd
lrwxrwxrwx  1 root root 14 2005-05-20 08:11 S12alsa -> ../init.d/alsa
lrwxrwxrwx  1 root root 13 2005-05-20 15:48 S13gdm -> ../init.d/gdm
lrwxrwxrwx  1 root root 13 2005-05-20 08:11 S14ppp -> ../init.d/ppp
lrwxrwxrwx  1 root root 16 2005-05-20 15:46 S19cupsys -> ../init.d/cupsys
lrwxrwxrwx  1 root root 15 2005-05-20 15:45 S20acpid -> ../init.d/acpid
lrwxrwxrwx  1 root root 14 2005-05-20 15:45 S20apmd -> ../init.d/apmd
lrwxrwxrwx  1 root root 16 2005-05-20 15:45 S20dbus-1 -> ../init.d/dbus-1
lrwxrwxrwx  1 root root 15 2005-05-20 08:10 S20inetd -> ../init.d/inetd
lrwxrwxrwx  1 root root 17 2005-05-20 08:10 S20makedev -> ../init.d/makedev
lrwxrwxrwx  1 root root 15 2005-06-05 20:49 S20mysql -> ../init.d/mysql
lrwxrwxrwx  1 root root 17 2005-05-20 08:11 S20postfix -> ../init.d/postfix
lrwxrwxrwx  1 root root 19 2005-05-20 15:47 S20powernowd -> ../init.d/powernowd
lrwxrwxrwx  1 root root 15 2005-05-20 08:10 S20rsync -> ../init.d/rsync
lrwxrwxrwx  1 root root 15 2005-05-22 15:32 S20samba -> ../init.d/samba
lrwxrwxrwx  1 root root 15 2005-05-20 08:10 S25mdadm -> ../init.d/mdadm
lrwxrwxrwx  1 root root 17 2005-05-20 15:45 S89anacron -> ../init.d/anacron
lrwxrwxrwx  1 root root 13 2005-05-20 08:11 S89atd -> ../init.d/atd
lrwxrwxrwx  1 root root 14 2005-05-20 08:10 S89cron -> ../init.d/cron
lrwxrwxrwx  1 root root 18 2005-06-17 03:41 S90vmware -> /etc/init.d/vmware
lrwxrwxrwx  1 root root 16 2005-05-21 21:03 S91apache -> ../init.d/apache
lrwxrwxrwx  1 root root 17 2005-05-21 19:31 S91apache2 -> ../init.d/apache2
lrwxrwxrwx  1 root root 22 2005-05-20 15:45 S99acpi-support -> ../init.d/acpi-support
lrwxrwxrwx  1 root root 19 2005-05-20 15:46 S99fetchmail -> ../init.d/fetchmail
lrwxrwxrwx  1 root root 19 2005-05-20 08:10 S99rmnologin -> ../init.d/rmnologin
lrwxrwxrwx  1 root root 23 2005-05-20 08:10 S99stop-bootlogd -> ../init.d/stop-bootlogd

```

I just want you to tell me which is critical I mean 'should not be removed.' or which can be removed.. I'm sure I can remove mysql and apache but what about else?

---

### Post by blind0wl on 2005-06-21
Well its really up to you what you need and dont, most of the services youve listed are defaults, except for the obvious vmware and apaches.  Instead of removing from your rc.d folders, Id recommend:

```
sudo apt-get install rcconf
```

Allows you to disable and enable boot time services, you can even try playing with some of the obvious ones and see if they make a substantial difference to boot time.

HTH

Blindy

---

