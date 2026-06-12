---
title: "Can no longer boot! (please help)"
date: 2009-02-19
forum: General Help
---

### Post by insilico on 2009-02-19
Okay, so I woke up this morning, turned on the Ubuntu 8.10 PC, and for reasons I can't explain, it won't let me boot.

I get to the main loading bar screen when all of a sudden, I'm brought to the terminal saying something along the lines of "unable to mount" (I'm guessing it means the main HDD) followed by something that tells me it cannot find /sbin/innit.

Afterwards there are a few more things about "innit".

I know this may sound vague, but can anyone tell me what the problem might be?

(PS: I'm typing this from a Live session)

---

### Post by taurus on 2009-02-19
Mount the root filesystem, /, from the LiveCD and exam /boot/grub/menu.lst & /etc/fstab to see the UUID for root filesystem is still the same.

---

### Post by insilico on 2009-02-19
When I try to mount my main HDD (my other HDD works) I get "Cannot mount volume"
DETAILS:
mount: wrong fs type, bad option, bad superblock on /dev/sda1, missing codepage or helper program, or other error In some cases useful info is found in syslog - try dmesg |tail or so

It might be worth noting that I did install my new HDD not too long ago, but I had rebooted a few times whilst I was using the new HDD and it worked fine.

---

### Post by taurus on 2009-02-19
So / is located on /dev/sda1.

```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/sda1 /media/ubuntu
df -h
```

---

### Post by stalkingwolf on 2009-02-19
Try using the recovery mode.
When the computer first starts, just before the Grub menu hit ESC.
this will bring up the boot menu.  select recovery. enter.
it will run its thing and then a box with several options will come up.
select Fix broken packages.  enter.  when that finishes select reboot.

Hope that helps.

---

