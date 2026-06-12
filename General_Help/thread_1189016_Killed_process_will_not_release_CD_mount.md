---
title: "Killed process will not release CD mount??"
date: 2009-06-16
forum: General Help
---

### Post by ARhere on 2009-06-16
I am stumped on this one!

I was trying to copy data from an old DVD to my drive using "cp" and "diff".  A couple of times the diff was taking too long and I had to do something else so I canceled the action using "CTRL+Z".

I am trying to eject the DVD now but get an error in gnome saying the device cannot be unmounted because it is busy.  Checking "System Monitor" shows my diff commands as stopped, but still accessing the drives so I killed them; but the drive still will not eject.
```
$ sudo umount /media/cdrom0
umount: /media/cdrom0: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
[1]   Killed                  diff -r /media/cdrom0/ Videos/300/
[2]   Killed                  man cp
[5]-  Killed                  diff -yrs /media/cdrom0/ Videos/300/
[6]+  Killed                  diff -yrs /media/cdrom0/ Videos/300/
```

If a process is killed, how can it still be making the drive busy?
-AR

(P.S.: I know I could just restart gnome or force the unmount, but I am trying to understand what is going on and not use the crowbar solution. :-D)

---

### Post by geirha on 2009-06-16
Does this command show anything?
```
sudo fuser -cv /media/cdrom0/
```

It should list all programs currently using the filesystem mounted on /media/cdrom0.

---

### Post by sdennie on 2009-06-16
See if this produces any output:

```

lsof | grep cdrom

```

Also, make sure you don't have any terminals opened that are cd'd into /media/cdrom.  That's a pretty common cause of not being able to eject.

---

