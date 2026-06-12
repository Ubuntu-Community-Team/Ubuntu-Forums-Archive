---
title: "How can I remove mounted volumes from left panel of nautilus?"
date: 2008-03-13
forum: Desktop Environments
---

### Post by c0d3h4ck on 2008-03-13
I have several hard disks. They are described in fstab, so they are mounted at boot time. But, they are always shown in left panel of nautilus. I won't  that they are display. I attached the screenshot showing my problem.

Are there are the way to solve my problem? I have search that not only in Google but also in here. But, I can't obtain appropriate answers.

---

### Post by BlowflyBob on 2008-03-13
Could you post your fstab contents?

I would think that they aren't being mounted correctly, or that the location they are mounted has something to do with it how Nautilus displays them. (The latter being a wild guess :D)

---

### Post by c0d3h4ck on 2008-03-13
fstab of my linux box is following

> # <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=5d8c08c6-f59b-453d-989d-6f5f9eef9199 /               xfs     noatime         0       1
# /dev/sda1
UUID=88793fd0-d461-4a29-9587-12ac8cbad4b6 /boot           ext3    noatime         0       2
# /dev/sda4
UUID=cbabc06b-4420-4f66-a966-97ea58e1beec /home           xfs     noatime         0       2
# /dev/sda2
UUID=666c6412-13bf-4c66-bc23-3e0738d7cfe4 none            swap    sw              0       0

# Torrent
UUID=d1a2768a-4872-45b8-ac0c-5fec3a538f8f /home/c0d3h4ck/Desktop/Multimedia/Torrent xfs noatime         0       2

# Temporary
UUID=e7443632-a099-4486-8025-dd41de8a7c3d /home/c0d3h4ck/Desktop/Multimedia/Temporary xfs noatime         0       2

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

Additionally, my mount information is following
> c0d3h4ck@code:~$ mount
/dev/sda3 on / type xfs (rw,noatime)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-12-generic/volatile type tmpfs (rw)
/dev/sda1 on /boot type ext3 (rw,noatime)
/dev/sda4 on /home type xfs (rw,noatime)
/dev/sdb1 on /home/c0d3h4ck/Desktop/Multimedia/Torrent type xfs (rw,noatime)
/dev/sdc1 on /home/c0d3h4ck/Desktop/Multimedia/Temporary type xfs (rw,noatime)
securityfs on /sys/kernel/security type securityfs (rw)
c0d3h4ck@code:~$ 


Thank you for your reply.

---

### Post by Shazaam on 2008-03-13
Go to Applications>System Tools>Configuration Editor (or gconf-editor in terminal). Then go to apps>nautilus>tree. Is "show_only_directories" checked?

---

### Post by c0d3h4ck on 2008-03-13
First all, thank you for reply. But, your answer is not appropriate because my problem occurs in place of side panel of nautilus. To the best of my knowledge, your answer is only concerned with tree of side panel.

---

