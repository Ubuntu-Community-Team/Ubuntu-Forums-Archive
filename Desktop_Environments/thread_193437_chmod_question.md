---
title: "chmod question"
date: 2006-06-10
forum: Desktop Environments
---

### Post by jrd on 2006-06-10
After reinstalling kubuntu the other day (for reasons we wont talk about), I tried to access my ntfs drive and I got a "permission denied" error. so I looked at the permissions and only root had access. So I thought no big deal I'll just change the permissions, So I cd to were the drive is mounted and typ:"sudo chmod -v a=r hda1" then it tells me It couldn't change it. I'm using sudo so how is this possible? I even tried the chown thing but it didn't work either(same error). So finally I decide to try the gui way, so I went to " Disk and File Systems" as root and changed owner to me and let root have the group. So my question is...Why didn't it change when I used the non gui way?

Someone please explain, thanks

---

### Post by sparhawk on 2006-06-10
I am pretty sure that you cannot change the permissions for an NTFS volume in linux. You are restricted to Read only. Try this to mount the volume with read only.

[COLOR="Red"]sudo mkdir /media/windows
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab[/COLOR]

add this to the end of the fstab file and save the file

[COLOR="Red"]/dev/hda1    /media/windows ntfs  nls=utf8,umask=0222 0    0[/COLOR]

That will mount it on boot.

If you want to mount it now just enter

[COLOR="Red"]sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222[/COLOR]

---

### Post by jazzmuzik on 2006-06-10
[QUOTE=sparhawk]If you want to mount it now just enter...[/QUOTE]

Once you add the line to /etc/fstab you can mount and unmount the device without specifying the mount point. It gets the mount point from fstab anyway:

```
sudo umount /dev/hda1
sudo mount /dev/hda1
```

---

### Post by Sutekh on 2006-06-10
[quote=jazzmuzik]Once you add the line to /etc/fstab you can mount and unmount the device without specifying the mount point. It gets the mount point from fstab anyway:

```
sudo umount /dev/hda1
sudo mount /dev/hda1
```[/quote]
And vice-versa.  A partition can be mounted by using the mount folder and the /etc/fstab provides the device location.
```
sudo umount /media/windows
sudo mount /media/windows
```

---

### Post by jazzmuzik on 2006-06-10
> And vice-versa

Exactly.

---

