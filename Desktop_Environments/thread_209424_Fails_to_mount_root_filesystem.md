---
title: "Fails to mount root filesystem"
date: 2006-07-05
forum: Desktop Environments
---

### Post by 3saul on 2006-07-05
I just booted my computer. It got to the ubuntu splash on the second stage which is Mounting root filesystem. From their to goes to an ash prompt and tells me that the 'Target filesystem doesn't have /sbin/init' - of course because root is not mounted.

Does anybody know why this happens or how to fix it? I haven't added or removed (or in any other way altered) my machine since last boot (which worked). I can see the partition that has ubuntu install on it in windows (using ifs). All seems fine...except it won't/can't mount. Is this a udev issue?

From menu.lst (my linux partition is physically located on the third partition...so this looks good)
[B]title		Ubuntu, kernel 2.6.15-25-686
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-25-686 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-25-686
savedefault
boot[/B]

---

### Post by Blairboy on 2006-07-05
Well, do you normally use bash instead of ash?  Your grub looks fine.  The next thing would be have you changed anything since the last time when it actually mounted properly?  Also, not having a fs mounted pretty much makes checking error logs impossible, unless you can do something in that ash terminal, or someone else here knows how to get logs without a fs being mounted.

---

### Post by 3saul on 2006-07-05
As mentioned in my original post :) I can indeed get to the partition from windows, and no, nothing has changed on my machine since the last boot.

---

### Post by dsyates on 2006-07-07
The exact same thing happened to me last night. Same situation too, I can access the partition from a live cd, and nothing has changed since last boot. Only difference is my root resides on /dev/hda1. If anyone has a solution to this please let me know. This is sorta the straw that broke the camel's back for me. I may go back to debian stable, if I don't get this fixed soon.

---

### Post by dsyates on 2006-07-07
I solved the problem! I booted a livecd (damn small linux was what I used). Once in that environment I did the following:
sudo mkdir /mnt/root
sudo mount -t ext3 -o rw /dev/hda1 /mnt/root
sudo chroot /mnt/root
sudo apt-get update
sudo apt-get upgrade
(the last two steps were unecessary precautions)
sudo dpkg-reconfigure udev


I am not sure why this worked, but it did. I am noticing no ill effects as of yet. 
All seems well. ymmv

---

