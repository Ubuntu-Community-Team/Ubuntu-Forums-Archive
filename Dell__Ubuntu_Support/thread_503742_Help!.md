---
title: "Help!"
date: 2007-07-18
forum: Dell  Ubuntu Support
---

### Post by Lina_inpas on 2007-07-18
Hihi......
I reinstalled Windows xp yesterday and now I cannot get access to the Linux.
I have tried many ways searching from internet but all failed. 
Anybody can help me?
I use Kubuntu to install the Linux.
Thank you!!!:sad:

---

### Post by benjaminwr on 2007-07-18
Boot your Ubuntu Installation CD and then do:

As root (or with sudo), type grub
 When at the grub prompt, type find /boot/grub/stage2
This will return something like (hd0,2)
To setup the boot partition boot type root (hd0,2). This is the harddrive and the partition your linux is installed on...
And then to configure grub type setup (hd0)
Now you're done, so exit with quit 

that should do the trick

Cheers

---

### Post by strabes on 2007-07-18
Check the link in my signature about fixing/reinstalling GRUB.

---

