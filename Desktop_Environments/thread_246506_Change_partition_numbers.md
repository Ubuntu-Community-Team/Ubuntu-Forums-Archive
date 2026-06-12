---
title: "Change partition numbers"
date: 2006-08-29
forum: Desktop Environments
---

### Post by PaulFXH on 2006-08-29
I have a usb hd with eight (8) logical partitions.
Long story short, due to some "experimentation", many of the partition numbers (/dev/sdaX), have been bumped up by one. As a result, a bootcd I use has become "disorientated".
So, I need to restore the partition numbers as they had been. Is this possible through GPartEd? or otherwise? I have tried with GPartEd but can't get the changes I need.
Any light at the end of the tunnel?](*,)

---

### Post by huygens on 2006-08-29
I do not know an easy way. But actually the Hack #83 in the book "Ubuntu Hacks" seems to be just about solving your issue, or at least finding a work around for it :-)
I am not sure if I can reproduce the hack here (copyright permission...) and also, this hack is pretty huge. The hack consist at giving device name to a block device, so your partition is not one time /dev/sda1 and the other time /dev/sda2, but is always mounted to a name you specify, for example /dev/ext-hd.
Haha, this hack is based on a solution/resource find in these links:
[http://www.ubuntuforums.org/showthread.php?t=91948](http://www.ubuntuforums.org/showthread.php?t=91948)
[http://www.reactivated.net/writing_udev_rules.html](http://www.reactivated.net/writing_udev_rules.html)


Huygens

PS: I am in no way affiliate to the Editor or Authors of the aboved-mentionned book.

---

### Post by PaulFXH on 2006-08-29
Thanks for the reply.
However, it seems to me that the links you provided allow the NAME of a device to be changed rather than the individual partition numbers on that device.
So, my /dev/sda could become /dev/USB_HD but the partition numbers would remain the same.

What I want is to rename /dev/sda6 to /dev/sda7 whereas what I am seeing will only permit me to change the "sda" part rather than the "number" part.
However, I'm going to have a more in-depth look later on.

---

### Post by doobit on 2006-08-29
edit

---

### Post by huygens on 2006-08-30
Sorry PaulFXH, I can then not help you further, I have no clue how to do it... :-(

Huygens

---

### Post by PaulFXH on 2006-08-30
Hi huygens
Not to worry, I re-installed all of the stuff that was implicated in the disorientated bootcd so that the correct partitions are now referred to.

So, I've learned that if partition numbers are important, you need to be very careful when removing partitions as there doesn't seem to be a pain-free way of changing the partition numbers.:D 
Cheers
Paul

---

