---
title: "Failed Attempt to Run Fedora - Anyone Else?"
date: 2007-06-29
forum: Fedora/RedHat and derivatives
---

### Post by hermesrules on 2007-06-29
Hi,

I recently decided to give Fedora 7 a try, having been a long-time Kubuntu and currently OpenSuse user and not having experimented with Fedora since the Core 3 days... I downloaded the KDE Live CD, everything seemed to work fine, so then I proceeded with the install.

The first thing that got me surprised (most probably due to my own ignorance in reading the documentation) was that the Live CD did not allow me to chose any packages, it just copied most of itself onto my hard drive. Anyway, that was not a big deal, I could always go back and install whatever else I needed.

The biggest surprise came upon reboot. I have my /home folder on an external usb drive partition, and for some reason it seemed to me that Fedora is trying to mount the drive before it has loaded a kernerl module to be able to do so. As a result, a few seconds upon booting I would just get a message telling me that the device labeled /HOME cannot be found.

I tried to change the fstab entries manually, to indicate the actual drives (like /dev/sdb3 in this case) instead of drive labels, but that led to the same result. Then, I concluded I will just get back to OpenSuse, and Fedora stood no chance on my machine.

Has anyone else encountered anything like this? Or perhaps someone can suggest a workaround? I was curious to try Fedora and still am, so if I am confident I can make it work, then I'll most likely give it a test-drive :)

Thanks!

---

### Post by ButteBlues on 2007-07-01
There was an issue I had where it didn't want to auto-mount filesystems it felt were not clean, even though they were.

I just ran a fsck, and then it mounted.

---

