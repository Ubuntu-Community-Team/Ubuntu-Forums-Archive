---
title: "Virtual CDROM Mounting Issues/Wine Issue"
date: 2006-06-18
forum: Desktop Environments
---

### Post by rjcube on 2006-06-18
I was trying to mount a .iso and I used this command:

```
$mount -o loop <ISO directory> /media/cdrom
```

Now I know how to do it correctly and that the /media/cdrom was my mistake, but now when i go to my desktop there is the cdrom0 volume, I right click it and click on unmount volume and an error message comes up saying:

> Unable to unmount the selected volume.

Umount: it seems /media/cdrom0 is mounted multiple times

How can I unmount This volume?


And now for the wine Issue, I try to run a .exe from the terminal but it brings up an error message:

```
rjcube@rjcube-desktop:~$ wine /mnt/vcd1/install.exe
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/home/rjcube', starting in the Windows directory.
wine: cannot find '/mnt/vcd1/install.exe'

```

How can I get this file running?

Thank you in advance for any help.

---

### Post by mlind on 2006-06-18
Your cdrom is was probably already mounted on /media/cdrom. You should create
different mount point for "virtual cd", for example /mnt/image or /media/image
and mount it there. I think you have to use -f parameter to umount it now.

Or just umount /media/cdrom before mounting loopback device to that mount point.

For wine issue, maybe *winecfg* could help.

---

### Post by rjcube on 2006-06-18
[QUOTE=mlind]Your cdrom is was probably already mounted on /media/cdrom. You should create
different mount point for "virtual cd", for example /mnt/image or /media/image
and mount it there. I think you have to use -f parameter to umount it now.

Or just umount /media/cdrom before mounting loopback device to that mount point.

For wine issue, maybe *winecfg* could help.[/QUOTE]


A different mount point would just be a directory right?

and how do I use -f parameter?

and I have no idea at all what I would need to change in winecfg

---

### Post by mlind on 2006-06-18
[QUOTE=rjcube]A different mount point would just be a directory right?

and how do I use -f parameter?

and I have no idea at all what I would need to change in winecfg[/QUOTE]

Yeah, just a empty directory. 

/etc/mtab file contains currectly mounted partitions. See if cdrom disappears from
there after using force.
```

sudo umount -f /dev/cdrom

```

I dunno about winecfg either, it was just a thought..

---

### Post by rjcube on 2006-06-18
[QUOTE=mlind]Yeah, just a empty directory. 

/etc/mtab file contains currectly mounted partitions. See if cdrom disappears from
there after using force.
```

sudo umount -f /dev/cdrom

```

I dunno about winecfg either, it was just a thought..[/QUOTE]

That worked perfectly, thanks alot.

Still gotta figure out the wine problem tho.

---

