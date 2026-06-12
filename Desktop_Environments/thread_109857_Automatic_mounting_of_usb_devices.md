---
title: "Automatic mounting of usb devices"
date: 2005-12-29
forum: Desktop Environments
---

### Post by Eisinger on 2005-12-29
I have recently converted my private server from Debian to Ubuntu. So far I think Ubuntu is a great distribution.
When I tried to use my USB stick or a digital camera on USB I experienced the problem, that both the devices /dev/sdc and /dev/sdc1 where created, but gnome-volume-manager (or hal) did only try to mount /dev/sdc. This leads to an error message on "invalid format on /dev/sdc" when I double-click on the respective icon in nautilus and automatic mounting is aborted. Investigating the case I found that /dev/sdc1 can be mounted (using e.g. pmount) without problems. This shows that /dev/sdc seems to be superfluous, that it is unfortunately chosen by gnome-volume-manager (or hal)  instead of /dev/sdc1.
Reading in the documentation of hal I found that for the installed version of hal (>0.5) kernel >2.6.12 is recommended. I do not know whether this is the problem? 
I could (temporarily) solve the problem by adding /dev/sdc1 to /etc/fstab, mounting /dev/sdc1 to /media/usb. This adds an additional icon in nautilus, which works for reading the USB stick (or the camera). Still, I think this is an ugly solution. 
[LIST]
[*] Is my problem a 'known issue'?
[*] Does somebody know of a better solution?
[*] Is the kernel version the root problem? and when will kernel 2.6.14 become available for ubuntu?
[/LIST]

---

### Post by mlomker on 2005-12-29
[QUOTE=Eisinger][*] Is the kernel version the root problem? and when will kernel 2.6.14 become available for ubuntu?
[/LIST][/QUOTE]

It'll be in Dapper, the next release. You can search bugzilla (link at top of page) to see if it is a known issue.  I moved your post to gnome desktop since you had posted in the KDE forum...

Do you have more than one partition on your USB stick?

---

### Post by Eisinger on 2005-12-30
Thank you for moving the post - I was not aware that I wrote it in KDE.

There should only be one partition on the USB stick. In addition, the camera connection had the same problem.

---

