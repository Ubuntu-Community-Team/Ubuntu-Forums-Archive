---
title: "Detect hard drive after reboot"
date: 2007-07-14
forum: Dell  Ubuntu Support
---

### Post by edtechre on 2007-07-14
Hello all,

I'm running Ubuntu on a Dell 1501.  Reboot works great, until I try a reboot after doing a hibernate or a suspend.  Basically, the OS shuts down properly, but when I'm supposed to see a BIOS screen, all I see is a blank screen.

I'm thinking the problem here is that my hard drive isn't being detected, since I don't see any light for my HD, even though the machine is on.  This would also make sense since us 1501 users have to add pci=nomsi to the kernel command for GRUB to get the HD detected.

Is there any way to make sure pci=nomsi gets used after a reboot?

---

### Post by edtechre on 2007-07-14
*bump*

Again, the main problem is not seeing anything when the BIOS screen should come up.

---

### Post by edtechre on 2007-07-16
Fixed.  

I added a BIOS option to reboot on my kernel line in GRUB (reboot=b):

kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=46cfa80e-6a0a-444c-9086-5bf5f0ea47ea ro quiet reboot=b pci=nomsi

I also removed the splash screen, though I don't know if that had anything to do with it.

---

### Post by Seamus on 2007-07-17
THis looks very similar to what I'm having at the moment actually - can you confirm that your OS was booting fine from a cold start, it was only when you were shutting it down/rebooting it that it hung on the "final" stage before it should launch a restart or shut down completely...

I did post in another thread about this issue here:

[http://ubuntuforums.org/showthread.php?t=502816](http://ubuntuforums.org/showthread.php?t=502816)

---

### Post by Seamus on 2007-07-17
> **Seamus said:**
> THis looks very similar to what I'm having at the moment actually - can you confirm that your OS was booting fine from a cold start, it was only when you were shutting it down/rebooting it that it hung on the "final" stage before it should launch a restart or shut down completely...

I did post in another thread about this issue here:

[http://ubuntuforums.org/showthread.php?t=502816](http://ubuntuforums.org/showthread.php?t=502816)

Just confirming this fixed it for me as well.

---

### Post by mommebu on 2007-07-18
Seamus,
I am wondering, as this post talks about a kernel reboot option, does this option really resolve the shutdown/reboot issue you were talking about in the other post?
That's because I seem to have the same problem you have, which is  especially annoying on shutdown, as it is a notebook that I shutdown 2-3 times a day.
For what you found, is it the reboot option or the pci option or the combination of both that does the job?

thanks.

---

### Post by Seamus on 2007-07-18
HI,

It is has definitely resolved the issue for me.

In my /boot/grub/menu.lst I originally had the following:

> ## ## End Default Options ##

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,0)
kernel          /vmlinuz-2.6.20-16-generic root=/dev/md0 ro quiet splash
initrd          /initrd.img-2.6.20-16-generic
quiet
savedefault


I now have

> ## ## End Default Options ##

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,0)
kernel          /vmlinuz-2.6.20-16-generic root=/dev/md0 ro quiet reboot=b splash
initrd          /initrd.img-2.6.20-16-generic
quiet
savedefault


The only difference I can put it down to was the addition of:

**reboot=b**

There is ONE other thing that I had managed to iron out prior to making this change - when I was applying updates onmy new install it was erroring on the OpenOffice updates because it was saying it could not write to the cache directories for the fonts.

I resolved this issue, and then made the change to the above file and it worked fine.

I'm picking it was the change, or else it's a mighty big coincidence.

Cheers

---

### Post by mommebu on 2007-07-18
For the moment it seems to work also for me...

Thanks for the quick answer.

---

### Post by mommebu on 2007-08-10
...back from holidays I have to correct, the problem came out to be still there. After a series of successfull shutdowns, the computer hungd again. Most of all the problem seems to appear absolutely arbitrarily, as during holidays I was using the computer in an abolsute constant way, i. e. turn it on, log in, connect, check mail, read mail, disconnect, shutdown. Somtimes the computer shut down, sometimes not, with apparently no regularity. 
no more ideas...

---

### Post by Seamus on 2007-08-10
Odd ... mine has worked consistently since I made this post.

---

