---
title: "No boot sector on internal hard drive"
date: 2008-09-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by NoPoChris on 2008-09-24
Dell Inspiron 1520


I wanted to reformat my iPod so that I could use it with Ubuntu (it is Mac formatted). So I did some research and found [these instructions]("http://www.gnu.org/software/gnupod/gnupod.html#SEC6").

I backed up the firmware:
```
dd if=/dev/sda2 of=backup_firmware
```

And then went to the next step:
```
dd if=/dev/zero of=/dev/sda bs=1M count=10
rmmod sbp2 && insmod sbp2
```

Then got to this:
```
pc-fdisk /dev/sda [start fdisk]
```

After that I got distracted by other things not computer related and forgot about what I was doing. So when I came back to the computer I closed everything and shutdown. Now when I try to boot up I get this:

```
No boot sector on internal hard drive

No bootable devices--strike F1 to retry boot, F2 for setup utility
  Press F5 to run onboard dianostics.
_
```

F1 repeats the error message
F2 sends me to the BIOS setup menu
F5 runs a diagnostic check, but doesn't check the hard drive

If anybody knows a way to fix this problem, please help. I put in the Ubuntu 7.10 live CD but wasn't quite sure what to do from there, of if there even was anything I could do (I looked around in the home folder just to see if I could find any of my files but had no luck). I also tried booting with the iPod plugged in but got the same error.

Thanks

---

### Post by NoPoChris on 2008-09-25
help?

---

### Post by natehall on 2008-09-26
I'd suggest Puppy linux. ([www.puppylinux.org](www.puppylinux.org)). It's designed to run from a live cd so you can check your partions and then fix them with Gparted. By the way its a great little distro for old pcs.

---

### Post by caljohnsmith on 2008-09-26
From that tutorial you followed, they say:
> We assume your iPod at /dev/sda. 
Did you check to see if that was indeed your Ipod? Because usually sda is your internal HDD. If that is true then you unfortunately deleted your HDD. With your Ipod plugged in, how about posting:
```
sudo fdisk -lu
```
Then we can get an idea of what happened.

---

