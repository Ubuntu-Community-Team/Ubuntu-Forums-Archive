---
title: "reinstall GRUB"
date: 2008-12-30
forum: General Help
---

### Post by inxygnuu on 2008-12-30
hello, i just recently installed windoze, (after ubuntu) and it overwrote my MBR. I want to reinstall GRUB, but I have an error. This is where I am:

I booted a live cd, and typed in 'grub' on the command line. I then typed in 'root (hd0,7)' hd0,7 is where my GRUB boot files and ubuntu are. It then says "selected disk does not exist" After that "Selected disk does not exist" What is happening? I just checked /boot/grub, everything is there. I have even tried 'root (hd,x)' in which x=any number. Even when I boot into a usb disk, nothing, what is happening? :cry::cry::confused:

---

### Post by maddog46113 on 2008-12-30
If your using intrepid the live cd has issues with recognizing other hard drives you may try restoring grub with a previous version of the ubuntu live cd. Also try installing grub on the primary master hard drive.

---

### Post by inxygnuu on 2008-12-30
fixed!:KS:popcorn::D:o:)=P~ I had to do 'SUDO grub', not just grub. stupid me! 

P.S. love the avatar! "flying monkeys stole my avatar. damn them" :lol:

---

