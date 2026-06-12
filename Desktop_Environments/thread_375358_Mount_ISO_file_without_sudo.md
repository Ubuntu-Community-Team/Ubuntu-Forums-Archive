---
title: "Mount ISO file without sudo"
date: 2007-03-03
forum: Desktop Environments
---

### Post by Wasted on 2007-03-03
I want to mount any iso file to a specific location without requiring root, I eventually want to put this into a script, and have it come up in the nautilus right-click menu. I have looked into modifying /etc/fstab or using the automounter, but I can't get any of them to work with an arbitrary iso, they all need the iso's to be hardcoded into the config files.

Of course, the alternative is just to use sudo whenever mounting the iso file, but it just gets annoying to have to type in my root password every time I want to mount an iso. It's little annoyances like this which make me want to go back to Windows for my desktops.

Any help on the issue would be most appreciated.

---

### Post by Azakus on 2007-03-03
Well, you can make it so you don't have to use sudo, but it would require you to become the root as your user, which is generally not advisable. I would advise making an fstab entry for a particularly named iso, then renaming whatever iso you need to that name (such as "loadthisiso.iso" or something) and have it always in a specific spot (say ~/iso/) and just switch which one is named loadthisiso when needed.
Here's an example of the fstab entry
```
~/iso/loadthiso.iso /mnt/X iso9660 ro,loop,auto 0 0
```

P.S. Windows Vista now has a similar setting as sudo called UAC, which behaves in nearly the same fashion. They also advise not to be the root (or admin) and to just be a user.

---

### Post by Wasted on 2007-03-03
Thanks Azakus, I tried a variant of your idea and it works fine. It's a bit sloppy of a solution but it works just as I want it to.

What I did was add a line to my /etc/fstab as follows:
```
/tmp/isolink     /media/iso    udf,iso9660    ro,user,loop,noauto    0   0
```

Then I created a script that does the following:
```

#!/bin/sh
umount /media/iso
ln -sf $1 /tmp/isolink
mount /media/iso
```
And told nautilus to open .iso and .img files with this script

However, when i try to unmount the volume through nautilus I get an error saying /dev/loop0 is not mounted. But I can still unmount a volume by executing "umount /media/iso" from a terminal.

---

### Post by scxtt on 2007-03-03
you may not need "loop" in the options if you're not specifying a loop device ...

change "ro,user,loop,noauto" to "ro,user,noauto" -- or specify a loop device, the man page for mount should help ...

---

### Post by Wasted on 2007-03-03
When I remove the loop option in /etc/fstab mount fails.
```
mount: /tmp/isolink is not a block device (maybe try `-o loop'?)
```

---

### Post by Azakus on 2007-03-03
I found software that does EXACTLY what you want. It is a CD drive emulator for Linux that loads an iso, cue, bin, or nrg file as a cdrom device without the need for a password.
[http://cdemu.sourceforge.net/](http://cdemu.sourceforge.net/)

---

