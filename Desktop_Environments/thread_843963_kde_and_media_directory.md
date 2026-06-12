---
title: "kde and /media directory"
date: 2008-06-28
forum: Desktop Environments
---

### Post by mitya on 2008-06-28
Good day, everybody.

I've got a strange problem in KDE 3.5.9.

I have several directories in /media:
/media/cdrom (and cdrom0)
/media/*windows*
/media/*storage*

*windows* is /dev/sda1 partition, which is mounted automatically while boot.
*storage* is a very large directory for music, films etc.

Both *windows* and *storage* were displayed in konqueror or dolphin when typing in *system:/media/* in address bar.

Then I deleted *storage* partition and made a new one using LVM, so now it is */dev/vg/storage* mounted automatically in */media/storage*.

But now only *windows* is displayed in *system:/media/*. *storage* has disappeared.

I tried to remount */media/storage*, also tried to edit *~/.kde/share/config/mediamanagerrc*, but nothing helps.

I updated recently from gutsy to hardy, but problem persists.
When I delete *~/.kde/share/config/mediamanagerrc*, the new one is created by KDE, but it contains only this:

[FONT="Courier New"][UserLabels]
/org/freedesktop/Hal/devices/volume_uuid_78B6_8BCB=windows[/FONT]

As you see, nothing according */media/storage* is there.

Here is my fstab:

[FONT="Courier New"]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/sda2
/dev/sda2 / reiserfs nouser,notail,atime,auto,rw,dev,exec,suid 0 1
# /dev/sda1
/dev/sda1 /media/windows vfat defaults,utf8,umask=007,uid=0,gid=46,auto,rw,nouser 0 0
# /dev/sda5
/dev/scd0 /media/cdrom0 auto user,atime,noauto,rw,nodev,exec,suid 0 0

/dev/vg/storage /media/storage reiserfs nouser,defaults,noatime,auto,rw,nodev,noexec,suid 0 2[/FONT]

I think there is some problem with KDE (kioslaves?) and HAL.

Any ideas?
Thanks.

---

