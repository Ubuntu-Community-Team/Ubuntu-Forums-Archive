---
title: "image of disk"
date: 2009-07-28
forum: Desktop Environments
---

### Post by Ofloo on 2009-07-28
I was wondering I've almost got my desktop exactly the way I want it, now I was wondering if there would be a way to create an image from this desktop so next time i don't have to install it allover again if something goes wrong.

i was thinking dd of=/dev/sda1 if=myimage on an usb disk or something, but that would make the image unnecessarily big, .. so I wondered if there wasn't a better solution.

---

### Post by lisati on 2009-07-28
[Remastersys]("http://www.howtoforge.com/ubuntu-linux-mint-livecd-with-remastersys") might be what you're after

---

### Post by wojox on 2009-07-28
May want to look at this:

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

Have not personally used it but other member's around the board like it.

---

### Post by drs305 on 2009-07-28
Another two possibilities are partimage (ext3, ext4 not available yet) or for command line fsarchiver. Both of these allow you to save and restore complete systems but don't include the empty space.

---

### Post by mtbsoft on 2009-07-28
Try [this]("http://www.linux.com/learn/tutorials/8225-clone-your-ubuntu-installation-onto-a-new-hard-disk") article - it describes how to clone your hard drive, just ignore the second half!

---

### Post by Ofloo on 2009-07-29
Thank you for all the replies, I wasn't aware there where so many options despite my search efforts on google..

* Google search results are getting really bad these days, .. nothing but commercial crap.

---

