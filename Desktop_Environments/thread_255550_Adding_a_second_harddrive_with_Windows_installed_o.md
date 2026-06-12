---
title: "Adding a second harddrive with Windows installed on it"
date: 2006-09-11
forum: Desktop Environments
---

### Post by ultim8 on 2006-09-11
Hello, I have two computers with exactly the same specs.  One has Ubuntu on it, the other has Windows on it.  I want to take the hard-drive out of the windows computer and add it as a second hard-drive in my ubuntu computer.  I also want to set up grub so that this one computer can boot up in either ubuntu or windows.  Is this easly doable?

I have moved the hard-drive into the Ubuntu computer and set the jumper settings on it to be a slave.  I have access to it within ubuntu, but I don't know how to set up grub to have windows as a boot option.

---

### Post by bernied on 2006-09-11
I don't know if this is going to work, as the windows install is likely to be specific to the computer it was installed on, but to set up grub, you need to edit the /boot/grub/menu.lst file.

It needs to have an entry something like this, and put this at the bottom, after it says 'End Automagic kernel list' or similar:

title Windows              # write anything you want here
root (hd1,0)
map (hd1) (hd0)
map (hd0) (hd1)
chainloader +1

That entry depends on Windows being on the first partition of the second disk (as they are counted by grub), but be aware that grub doesn't count the same as windows, or sometimes the same as bios, so the disk order can be not what you expect. So try that first, then come back if it doesn't work.

---

### Post by ultim8 on 2006-09-11
When trying what you suggested I got this message:

root (hd1,0)
Filesystem type unknown, Partition type 0x7
map (hd1)(hd0)
Error 11: Unrecognized device string
Hit <enter> to continue

---

### Post by bernied on 2006-09-11
> Filesystem type unknown, Partition type 0x7
This is not critical, and almost to be expected.
> map (hd1)(hd0)
Error 11: Unrecognized device string
There should be a space between the two devices
map (hd1)<space>(hd0)
And the same applies to the next line.

---

### Post by bernied on 2006-09-12
So did it work?

---

