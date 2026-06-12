---
title: "File Browser shows unmounted partitions"
date: 2007-05-13
forum: Desktop Environments
---

### Post by sradhakrishna on 2007-05-13
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/114359](https://bugs.launchpad.net/ubuntu/+bug/114359) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi,

File Browser in Ubuntu 7.04 is showing unmounted partitions.

My setup details:
i386 - Two hard drives - /sda1 and /sdb1
Windows on /sda1 - there are other partitions as well on this drive
Ubuntu on /sdb1 - mount information as follows:

rks@rks-home:~$ mount
/dev/sdb1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw)
/dev/sdb3 on /media/Store type vfat (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
rks@rks-home:~$

As u can see, none of the partitions on windows drive are present in the mounted lists.
 /etc/fstab has these entries:
proc /proc proc defaults 0 0
/dev/sdb1 / ext3 defaults,errors=remount-ro 0 1
/dev/sdb2 none swap sw 0 0
/dev/sdb3 /media/Store vfat defaults 0 0
As can be seen, no entries related to /sda1 in /etc/fstab too. And there's no entry related to the CD Drive as well.

When I open File Browser however, I see the following drives:
CD-RW/DVD-ROM Drive
52.2 GB Volume
54.0 GB Volume
My Store
Work1
FileSystem.

The attachments here are screenshots of the FileBrowser

Note: The Tree View seems to be ok, but the places view and the File upload dialog show the drives mentioned above.

As can be seen, none of these, except FileSystem are entries in /etc/fstab. They are all Windows Partitions on /sda1. How are they getting loaded??

Is there any other configuration file that i need to modify apart from /etc/fstab??

Please let me know.

Regards,
Radha

---

### Post by kidders on 2007-05-14
Hi there,

I've never regarded this behaviour as a bug ... it seems perfectly natural. I'm not sure Gnome is meant to behave like OSX.

It'd be interesting to get a few other posters' opinions.

[COLOR=Silver][[SIZE=1]*[UAResolved]*[/SIZE]]("http://ubuntuforums.org/showthread.php?t=377083")[/COLOR]

---

### Post by Marlo_nl on 2007-08-18
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/114359](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/114359) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi, please see my personal opinion below.


By reading [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/114359](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/114359)  I understand that the behavior of the Nautilus File Browser is not a bug but desired behavior.

Issue here might be that the desired behavior of the application programmer and of the user of the application is not in line.

I would prefer that the "Places" pane in the File Browser would not show the unmounted partitions, at least not by default.

The application programmer 's decided to make unmounted partitions visible in the "Places" pane is to give the user the possibility to mount the unmounted partitions simply by clicking them.

In my opinion it would be better to add an option to File Browser -> Edit -> Preferences in which the user can select to make the unmounted partitions visible in the "Places" pane or not. I would even argue that the "default" setting should be not visible.

Reason why I think this would be a better approach is because people who are not (yet) experts in Linux/Ubuntu but who are "just" using Ubuntu as OS will get confused because of the unmounted partitions in the "Places" pane.

I'm promoting Ubuntu as alternative OS to my acquaintances. To promote Ubuntu it typically will be, and even needs to be, used besides the more common OS. Hence, the possibility of hiding partitions (prevent partitions to automount by editing /etc/fstab) within Ubuntu is rather important in this case. 
It would also be preferred that these unmounted partitions would  "simply" not be visible elsewhere within Ubuntu. 
Hence, also not within the File Browser (by default) 

Regards, Marlo

---

### Post by Zalbor on 2007-08-18
This is perrfectly normal, and good too. They're there so you can easily mount them with a double-click.
As far as I know, the only way to make a partition not appear there is to put an entry for it in /etc/fstab, and make the mount point NOT be under /media.

---

### Post by Marlo_nl on 2007-08-29
Zalbor,

In my opinion, what is perfectly normal and good too, is a matter of taste.

I was not thinking about changing the behavior of the File Browser such that it is no longer possible to see unmounted partitions (and to mount by a simple double-click). 

I was thinking about adding an option to File Browser such that I can choose to hide (or make visible) these unmounted partitions.

In other words:
In some cases and for the more experienced users of Ubuntu it is good to be able to mount by a simple double-click. 
In other cases, e.g. for less experienced users, it might be better to hide unmounted partitions so they cannot be mounted by this simple double-click.

By the way, thanks for your remark "make the mount point NOT under media". Maybe this can help me to get File Browser behavior which is good (for specific situations).

Regards, Marlo

---

### Post by kidders on 2007-08-29
> **Marlo_nl said:**
> In other words:
In some cases and for the more experienced users of Ubuntu it is good to be able to mount by a simple double-click. 
In other cases, e.g. for less experienced users, it might be better to hide unmounted partitions so they cannot be mounted by this simple double-click.Odd... I would've thought these should be the other way around.

In any case, some graphical environments offer this level of configurability, and some don't. If Gnome/Nautilus bother you, you should try something else. I suppose you could always submit a feature request to Nautilus' maintainers.

---

### Post by manro on 2007-11-24
So, is there a way to hide this unmounted partitions from the places panel?

Regards,
Manro

---

