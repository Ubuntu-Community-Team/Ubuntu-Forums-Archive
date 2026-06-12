---
title: "Booting on laptop but not server"
date: 2011-03-10
forum: Desktop Environments
---

### Post by Dragonorb13 on 2011-03-10
Ok, this may seem a little odd, but I used my server to install Ubuntu on to an external hard drive. (long story short, the server won't recognize any internal hard disks with any type of video card installed. The video card works just fine when installed, and it will read both CDs/DVDs and USB drives just fine, it just refuses to even notice hard disks. I'm assuming an IRQ issue, but I've tried changing them with no success.) 
Having installed Ubuntu 10.04 on my external 250g hard disk, I attempted to boot it from the USB drive, since the system has that option. It tells me "error: out of disk" and goes to the Grub rescue prompt. Having followed multiple threads and advice posts, including on this forum, I was unable to resolve the issue. 
For s'n'gs, I hooked affore mentioned external hard disk to my laptop and tested it. Boots just fine. Then hooked it back to my server to see if it would boot. Still no dice 
[Just a side note, no the video card is not currently installed in said server, I was testing it to see if the thing would install and operate alright before I tested it with video card installed. Only ever make one change at a time, that way if something explodes, I know what caused it.]
My initial objective was to get an operating system that would boot with the video card installed. Any ideas what might be going wrong here?

---

### Post by Dragonorb13 on 2011-03-11
I'm going to guess, then, that nobody has any ideas. Well, thanks to anyone who read the post atleast

---

### Post by oldfred on 2011-03-11
I think out of disk means, it cannot find grub. But you said it booted on laptop.

So is server older and has the 137GB limit on boot? Where the laptop is newer and has no limit.

If you install the entire root or use a separate /boot all within the 137GB limit it may work. I usually suggest small / partitions and larger /home or /data partitions. Then all of the boot files on on the partition within the 137GB limit.

---

