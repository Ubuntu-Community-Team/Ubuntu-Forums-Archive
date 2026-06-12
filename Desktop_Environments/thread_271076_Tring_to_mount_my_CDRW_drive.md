---
title: "Tring to mount my CDRW drive"
date: 2006-10-04
forum: Desktop Environments
---

### Post by Clark Nova on 2006-10-04
I'm trying to mount my CDRW drive so that I can burn an ISO file to a disc. Here is the contents of my fstab file:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2 -- converted during upgrade to edgy
UUID=e8f8c084-5601-4319-b627-e5cd34d7a03a / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=55610814-4bac-4eca-877f-ac5e316f5877 none swap sw 0 0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
#Added by diskmounter utility
# /dev/hda1 -- converted during upgrade to edgy
UUID=DCBC6CF8BC6CCF18 /media/hda1 ntfs ro,user,fmask=0111,dmask=0000 0 0

When I put a CDRW into the drive it recognises that I have put a blank disc in and asks me what I want to do with it but when I open up GnomeBaker to burn the ISO the only drive it recognises as being there is    a CD-ROM drive. If I use the "Disk Mounter" panel applet it says it is mounted and I can eject the CDRW drive too but it still doesn't show up in GnomeBaker.

Can anybody help me with this? Thanks :)

---

### Post by ajgreeny on 2006-10-04
Have you actually tried to use gnomebaker, ie burn something with it?  It sounds as though the prog may just be naming the drive wrongly.

If you can't get it to work, consider using k3b, which I think is much better anyway.  It will work fine on a gnome install if you have the right lib files installed, and if you use apt-get or synaptic, or better aptitude all dependencies will be sorted for you.  If you use aptitude, and decide to remove k3b all those dependencies will also be removed, putting you back where you were before.

---

### Post by Clark Nova on 2006-10-04
Thanks for the reply :)

I have tried using GnomeBaker and it was detecting my CD-ROM drive as the burning device. I installed K3B as you suggested and it detected my CDRW drive correctly and worked without a hitch (apart from not liking the first brand of CD I tried but I think that might be down to the drive itself) so thanks very much!:KS 

By the way, I installed K3B using aptitude as you suggested rather than apt-get. What is the difference between the two? I though apt-get also resolved any dependency issues?

---

### Post by ajgreeny on 2006-10-04
Yes, it does.  The difference is when (or if) you want to uninstall a program.  Apt-get or synaptic will only get rid of the prog itself, but aptitude will get rid of dependencies as well, but not any also needed by other installed programs.  Very clever, isn't it?

---

### Post by Clark Nova on 2006-10-04
*makes notes*

Thanks very much, so I guess I should alway use aptitude rather than apt-get to keep my computer tidier and stop having unused programs and dependencies lying around :)

---

### Post by factor on 2006-10-09
hi, i tried sudo aptitude install k3b but it shows missing dependencies and the solution it offers me doesn't install anything. how can i install k3b?

regards.

---

