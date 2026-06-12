---
title: "Nessus not starting at startup...am I missing something?"
date: 2006-08-30
forum: Desktop Environments
---

### Post by Mia_tech on 2006-08-30
Hi guys....I'm trying to get Nessus starting when ubuntu star, but no success, I have to use the nessusd command to start it and be able to connect , I checked the /etc/rc2.d/ folder and nessus is listed to start at bootup, here is a copy of rc2.d.
============================================================================
jorge@ubuntu-box:/etc/rc2.d$ ls
S05vbesave          S14ppp            S20festival      S20nvidia-kernel  S21mysql-ndb    S90binfmt-support
S10acpid            S18hplip          S20hotkey-setup  S20powernowd      S25bluez-utils  S98usplash
S10powernowd.early  S19cupsys         S20laptop-mode   S20rsync          S25mdadm        S99acpi-support
S10sysklogd         S19mysql-ndb-mgm  S20makedev       S20samba          S89anacron      S99rc.local
S11klogd            S20apmd           S20mysql         S20snort          S89atd          S99rmnologin
S13gdm              S20dbus           S20nessusd       S20ssh            S89cron         S99stop-readahead
==========================================================================
as you can see nessus is listed as S20nessusd, any ideas....
Thanks

---

