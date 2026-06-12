---
title: "Can't mount floppy disk"
date: 2009-01-29
forum: General Help
---

### Post by bluefox815 on 2009-01-29
Hello.  I want to mount a floppy disk on my system, but I can't even begin to find the drive.

I tried "sudo mount /dev/fd0" and the command says that it could not find the device.  So I tried adding the following line to my /etc/fstab file.
"/dev/fd0	/floppy	auto	noauto,sync	0	0"

When I run the mount command again, I get this error:
"mount: mount point /floppy does not exist"

I thought this might be because there was not a 'floppy' folder in media, so I created the folder, but there was no change.

I don't know the formatting of the floppy, although I know it's a version of FAT, most likely FAT 16.

How can I mount this floppy?  I am ok with formatting it, I don't have any important data on it.

---

### Post by ieee488 on 2009-01-29
You don't see it in Places?

---

### Post by bluefox815 on 2009-01-29
No, I don't see it in Places, Computer, /media, anywhere.  It is not mounted and I have no idea how to mount it because I don't know what it's called (i.e. /dev/sda would be my HDD).

---

### Post by bluefox815 on 2009-01-29
Is there anyone who knows how I might fix this problem?

---

### Post by Slim Odds on 2009-01-29
> **bluefox815 said:**
> Is there anyone who knows how I might fix this problem?

A) Do you have a floppy drive?   ;)
B) Are all the cables plugged in properly?
C) Is it enable in your BIOS?
D) What the heck do you need a floppy for these days? (sorry, I couldn't resist).

---

### Post by bluefox815 on 2009-01-29
Well...

1)  I have a floppy drive and several floppy disks.

2)  All cables are plugged in properly, worked fine when I had Windows XP.

3)  I am unsure whether or not it is enabled in the BIOS.  The only two things that I have changed in the BIOS are the boot order, and how the BIOS controls my sound card (I will be looking more into that after I post this).

4)  I have decided to attempt making my own OS (yes, I'm aware of how difficult this can be) so that I can get a better understanding of the computer system on a low level.  I also like challenges.


EDIT:  The Floppy drive is enabled in the BIOS.

---

### Post by bluefox815 on 2009-01-30
Granted, the computer is pretty old.  When I put the disk in the floppy drive, the light on the drive doesn't blink at all, like it used to.  Could this be because of a dead drive, or does the light just blink when there is disk I/O?

---

### Post by shazbut on 2009-01-30
If you're on 8.10, I hit the same bug today.  Got my answer from here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/255651]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/255651")
The floppy module is not loaded by default.  To load for this session only do:
```
sudo modprobe floppy
```
To fix for all sessions you'll need to add ```
floppy
``` to the end of /etc/modules file.

---

### Post by bluefox815 on 2009-01-30
Thank you for your answer.  Yes, I am using Ubuntu version 8.10, and after I entered that command, my floppy drive kicked to life when I tried to mount it, as it didn't before.

However, I still get the same "mount: mount point /floppy does not exist" error.

EDIT:  The error occurred because the folder /floppy didn't exist while /media/floppy did.  I fixed this in fstab, but now I get this error:

```

mount: you must specify the filesystem type

```

I read that to do this, I type "mount -t *filesystem* /dev/fd0", but this only brings up the help documentation for mount (mount --help).

I can see the -t option in the help output, but the following command which I tried didn't work.

```

sudo mount -t fat /dev/fd0

```

---

### Post by shazbut on 2009-01-30
Try
```
sudo mount -t msdos /dev/fd0 /media/floppy
```

---

### Post by bluefox815 on 2009-01-30
I tried the command you suggested, and I got the following output:

```

mount: /dev/fd0: can't read superblock

```

---

### Post by Slim Odds on 2009-01-30
> **bluefox815 said:**
> I tried the command you suggested, and I got the following output:

```

mount: /dev/fd0: can't read superblock

```

When is the last time that floppy was used?

Floppy discs are notorious for their flakiness. Especially if they haven't been used for a long time.

Sounds likes a bad disc to me.

---

