---
title: "Missing MBR?"
date: 2007-05-27
forum: Desktop Environments
---

### Post by jerrywo on 2007-05-27
I've made a clone copy of my hard drive (a 250GB drive in an external case - USB).  Once upon a time, I was able to boot from the clone copy.

Since then, I've bounced back & forth, trying various distro's.  I'm back in Ubuntu-land at the moment.  I've created a clone copy of my hard drive.  I go into the BIOS during boot, select the USB HDD and the system will boot from the internal drive.

I can boot a CD in the drawer and boot from that - so the BIOS seems to be doing its job.

It sounds like I don't have a boot record on my secondary drive?  Is that plausible?  any thoughts?  I like the notion of having a backup drive that I can actually boot from.
Thanks in Advance
Jerry

---

### Post by Patrick K on 2007-05-27
I've never done this with Linux but with windows you need to do a sys X (X is the drive you want to boot from). This puts the files needed to boot in the root directory. What needs to be done in Linux to accomplish the same thing, I don't know.

---

### Post by jerrywo on 2007-05-28
Hmmmm, when I made this "cloned" external drive, I don't think I really cloned the HD per se, I just copied the "/" to "/media/disk".  If the info need to boot was outside "/", then it didn't get copied.  

When I installed Ubuntu, I didn't partition my internal hard drive, i.e., I used the entire 250GB disk.

This morning I tried (basically) to rsync ".dev/sda1 (my internal HDD) to dev/sdb1 (my external drive)".  A few bytes were transferred and I thought that would do the trick...but alas, I still can't boot from the external drive.
I'm still reading and tinkering.
Thanks for your tip

---

