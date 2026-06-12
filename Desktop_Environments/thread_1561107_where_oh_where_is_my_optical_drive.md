---
title: "where oh where is my optical drive?"
date: 2010-08-25
forum: Desktop Environments
---

### Post by NewDisciple on 2010-08-25
[B]Nothing on my system sees my optical drive. K3b doesn't see it, wodim doesn't see it, also nothing when I run the following commands from the terminal:  dmesg | tail , cd /dev ls. There is nothing in the /dev directory, nothing in media or mount. I also put a cd in it.
I haven't used it since I installed Lucid. Is this an item that requires a udev config edit? I looked at [https://wiki.ubuntu.com/X/Config/Input]("https://wiki.ubuntu.com/X/Config/Input") however I had trouble understanding it and I didn't see an example for optical drives anyway. I don't think you could do anything without a location or name anyhow.
Why did Ubuntu quit using hal?[/B]

---

### Post by jtarin on 2010-08-25
Are ther any entries in your /etc/fstab that refer to mounting an optical drive. Post it here.

---

### Post by NewDisciple on 2010-08-26
Nothing there, here it is:
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=1309d4fb-535f-450d-a9f7-728202ee4ac4 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda2 during installation
UUID=f1cfe868-1d8c-454d-ab1e-688984b50e77 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=57906808-71a9-436d-a1d1-9abbc750e7dc none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by jtarin on 2010-08-26
Do you have a floppy drive? No? Then comment it out. ```
#/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
```Runt this command in the terminal and post the results. ```
eject -n
```if there is no output try adding sudo.

---

### Post by NewDisciple on 2010-08-26
I ran eject -n yesterday with no results. Ran it again today and got:
 ~$ eject -n 
eject: device is `/dev/sr0' 

However when I manually checked /dev I was unable to locate sr0.

---

### Post by NewDisciple on 2010-08-26
It is now showing up when I cd /dev and run ls. However wodim does not see any devices nor does kb3. Also tried an audio cd but it apparently was not seen either.

---

### Post by NewDisciple on 2010-08-26
I did two things. Made an entry into /etc/fstab then I shut my computer down and checked the Sata cables. Fired it back up and now I have my cdrom back. Don't know which action helped, I'm just glad that it works.

---

