---
title: "Mounting an iso image over a samba share"
date: 2006-10-01
forum: Desktop Environments
---

### Post by bestiarosa on 2006-10-01
Hi,
I have access to a Windows machines through a Samba network and I'd like to mount on my Ubuntu machine an iso file present on that Windows computer without having to copy the file into my hard-disk.
However, I don't think Nautilus supports mounting iso files over a network so I'll have to do it manually. I've tried:
```
sudo mount smb://windowsmachine/directory/ /mnt/cdrom0 -t iso9660 -o loop
```
But this doesn't work as it can't find the file. Does anybody have an idea?

Thanks!

---

### Post by kidders on 2006-10-01
Hi there,

If you want to access something over samba, you have to mount the share. **sudo mount smb://windowsmachine/directory/ /mnt/cdrom0 -t iso9660 -o loop** tries to claim that the samba share is in ISO9660 format, which is obviously false.

Try something like this:

```

sudo mount -t smbfs //windowsmachine/directory /mnt/windows
sudo mount -o loop /mnt/windows/cdimage.iso /mnt/loop

```

Your ISO exists inside another filesystem, so (just as if you had copied it to your own computer) you can't access it without mounting the filesystem that contains it first.

Hope that helps.

---

### Post by bestiarosa on 2006-10-01
Thanks. The Windows machine is shut down right now so I can't try but I'll definitely let you know as soon as I can.
I seem to remember there was a GUI for doing that kind of stuff when I used SimplyMepis or Mandrake. Do you think there is something like that in Ubuntu?

---

### Post by kidders on 2006-10-01
Yep, I'm sure whatever you did in Mepis/Mandriva will work in Ubuntu too ... all Linuxes support the same software :-)

---

