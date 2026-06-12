---
title: "no password asked when mounting NTFS partitions"
date: 2010-06-11
forum: Desktop Environments
---

### Post by AM_SOS on 2010-06-11
hello,
noticed something that looks a little strange. installed and began using 10.04 yesterday and noticed that ubuntu does not query me for the password when i mount any of the 3 NTFS windows XP partitions.
all the other versions of ubuntu that i used in the past always required the password. aren't operating systems supposed to be growing more security conscious ? or is this some kind of bug with the installation ?
thanks !

---

### Post by restorator on 2010-06-11
As far as I know, you do not need a password when mounting a *partition*, but you do when mounting a *network share*. Is that what you were referring to?

---

### Post by Morbius1 on 2010-06-11
AM_SOS, you are correct. But it's not a bug it's a feature. After 170000  posts from people complaining about all the %@#! password prompts, Ubuntu apparently just let's it rip. 

So prior to 10.04 you needed to supply your sudo password to access the partition if it was not defined in /etc/fstab. Now you don't. I agree with your assessment about security. The only way out is to mount it in fstab and restrict permissions.

---

### Post by AM_SOS on 2010-06-11
no, no. i was talking about mounting NTFS windows partitions.

see i have 3 partitions on XP - the usual C, D, E. i have installed 10.04 as dual boot and had used the manual installer for this.

i have followed the same practice in the past with 9.10 and many earlier versions.

every time i wanted to access the C, D or E drives of XP from within ubuntu, i would click on " Places " in the main menu / start button, and would immediately be prompted for a password.

it is for the first time with 10.04 that i notice that it is not asking me for the password.

hence, i was wondering if this could be a security issue / bug due to an improper installation. although of course 10.04 is running normally.

thanks !

---

### Post by AM_SOS on 2010-06-11
thanks for the clarification Morbius 1 ! frankly, i liked the password protection features of ubuntu which were minimal at best, and required only for key processes. so while i hated the UAC in vista and switched it off at the first opportunity, i was pretty much ok with ubuntu prompting me for PW's once in a while. i think ubuntu's general password protection was well implemented.
maybe they could have given us an option. or better still increased the time interval associated with the " elevated privileges " key shaped icon that comes up on the panel.

as an aside do you think its safe to transfer much data from within ubuntu to the windows partitions ? i do not have the secuity issue in mind as much as the possibility of data corruption.
so far i have tended to be careful and have mounted the windows partitions from within ubuntu to read files only.

thanks !

---

### Post by Morbius1 on 2010-06-11
You are definitely asking the wrong person. I am very old school when it comes to this sort of thing. I allow write access to other NTSF partitions but never the Windows OS partition. Windows is a delicate creature and best left as read only. Clearly this is just my personal preference.

---

### Post by sisco311 on 2010-06-11
> **AM_SOS said:**
> thanks for the clarification Morbius 1 ! frankly, i liked the password protection features of ubuntu which were minimal at best, and required only for key processes. so while i hated the UAC in vista and switched it off at the first opportunity, i was pretty much ok with ubuntu prompting me for PW's once in a while. i think ubuntu's general password protection was well implemented.


I don't know much about Vista's UAC, but policykit and sudo are not only well implemented but highly configurable tools. ;)

If you want to (re-)enable the password authentication for mounting/unmounting/checking internal partitions, then edit the com.ubuntu.desktop.pkla file:
```
gksu gedit  /var/lib/polkit-1/localauthority/10-vendor.d/com.ubuntu.desktop.pkla
```
and comment out the section which allows admin users to mount/unmount/check partitions without a password:
```
**#**[Mounting, checking, etc. of internal drives]
**#**Identity=unix-group:admin
**#**Action=org.freedesktop.udisks.filesystem-*;org.freedesktop.udisks.drive-ata-smart*
**#**ResultActive=yes

[Change CPU Frequency scaling]
Identity=unix-group:admin
Action=org.gnome.cpufreqselector
ResultActive=yes

[Setting the clock]
Identity=unix-group:admin
Action=org.gnome.clockapplet.mechanism.*
ResultActive=yes

```

If you want to enable password authentication for external partitions as well, then instead of commenting out the section replace the **ResultActive=yes** by **ResultActive=auth_admin_keep**.

policykit is under development, it doesn't include a GUI configuration tool for the time being.

---

### Post by doas777 on 2010-06-11
JOC, where is the drive mounted to? they may have changed it to mount in userspace (in your profile, probably at ~/.gvfs). since userspace mounting doesn't use the 'mount' command, or attempt to touch any mount points that you don;t own, it shouldn't need sudo. the old default involved creating and mounting to a new directory in /media (root:root) named after the label of the disk being mounted (or DISK# if absent).

---

