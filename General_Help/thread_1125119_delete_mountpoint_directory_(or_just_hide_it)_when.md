---
title: "delete mountpoint directory (or just hide it) when not in use"
date: 2009-04-14
forum: General Help
---

### Post by KerryLB on 2009-04-14
I need some expert help again...

I've created a directory called 'mounts' in the root directory. Inside this directory, I've created separate directories for each of my partitions on my external drives, memory sticks, etc. Each of these directories under the 'mounts' directory is 'pointed' to as a mountpoint in fstab.

Not all of these partitions are mounted all the time, and to keep things a bit 'neater' I'd like to know if there's some way I can tell Ubuntu to automatically create these directories when their partitions are mounted, and then delete them again when the partitions are unmounted.

If that's not possible, can I tell it instead to just hide the directories when they have nothing mounted underneath them?

Thanks in advance for your help!

---

### Post by dcstar on 2009-04-14
> **KerryLB said:**
> I need some expert help again...

I've created a directory called 'mounts' in the root directory. Inside this directory, I've created separate directories for each of my partitions on my external drives, memory sticks, etc. Each of these directories under the 'mounts' directory is 'pointed' to as a mountpoint in fstab.

Not all of these partitions are mounted all the time, and to keep things a bit 'neater' I'd like to know if there's some way I can tell Ubuntu to automatically create these directories when their partitions are mounted, and then delete them again when the partitions are unmounted.

If that's not possible, can I tell it instead to just hide the directories when they have nothing mounted underneath them?


No.

---

### Post by KerryLB on 2009-04-14
I worked out a way of doing this using udev. PLEASE somebody tell me if what I'm doing here is going to result in me losing data somewhere along the line. 
I tested this on a memory stick and it seems to be working ok.

1. created two shell scripts:

[add-dir.sh]
mkdir /home/kerry/Transcend

[rem-dir.sh]
rmdir /home/kerry/Transcend


2. added two rules to /etc/udev/rules.d/10-local.rules:

SUBSYSTEM=="block", SUBSYSTEMS=="usb", ATTRS{manufacturer}=="JetFlash", ATTRS{product}=="Mass Storage Device", ATTRS{serial}=="7XOWT48N", ACTION=="add", RUN+="/bin/sh /home/kerry/scripts/add-dir.sh"

SUBSYSTEM=="block", SUBSYSTEMS=="usb", ATTRS{manufacturer}=="JetFlash", ATTRS{product}=="Mass Storage Device", ATTRS{serial}=="7XOWT48N", ACTION=="remove", RUN+="/bin/sh /home/kerry/scripts/rem-dir.sh"


3. set the mount options in /etc/fstab:
/dev/kb-transcend1	/home/kerry/Transcend	auto	auto,user,exec,rw


The remove rule was being ignored at first, but after some googling I got it to work by running "udevadm monitor" in the background.

---

### Post by dmizer on 2009-04-14
That looks pretty scary.

If the drive unmount fails, and remains mounted, you delete everything.

Rather than mounting in /home/kerry/Transcend, you should mount in /media. That way your home directory isn't filled with mountpoints. By mounting in media you also get handy desktop links.

---

### Post by KerryLB on 2009-04-15
> **dmizer said:**
> If the drive unmount fails, and remains mounted, you delete everything.

Am I correct in thinking that the udev 'remove' rule is only run when the drive is physically removed? So the files aren't physically there to be accidentally deleted when the rule runs... (Correct me if I'm missing something!)

But just in case, I've changed the 'remove' script a bit:

[rem-dir.sh]:
```
[ "$(ls -A /home/kerry/Transcend)" ] && \
# if NOT empty
: || \
# if empty:
sudo rmdir /home/kerry/Transcend
```

---

