---
title: "[SOLVED] Desktop Customization"
date: 2008-12-31
forum: General Help
---

### Post by ash369 on 2008-12-31
Hey all

I'm having a little trouble, not used Ubuntu that much and i need help installing icons. I also need help with my theme, its installed but I'm getting a message saying "This theme will not look as intended because the required GTK+ theme engine" is not installed.

Also, could i have some guidance on some addons i can use, to spice the desktop up a bit, looks a bit dull.

Thanks.

---

### Post by tech9 on 2008-12-31
[www.gnome-look.org](www.gnome-look.org)

---

### Post by fubbleskag on 2008-12-31
try this: [http://ubuntuforums.org/showthread.php?p=6130341#post6130341](http://ubuntuforums.org/showthread.php?p=6130341#post6130341)

---

### Post by ash369 on 2008-12-31
Thanks for the quick replies, i found this addon called Beryl could i run that with Ubuntu 8.10 if so could i have some guidance as to installing it. Thanks for the help :)

---

### Post by steveneddy on 2009-01-01
> **ash369 said:**
> Thanks for the quick replies, i found this addon called Beryl could i run that with Ubuntu 8.10 if so could i have some guidance as to installing it. Thanks for the help :)

[sigh....]

(again) Bery is dead and has been replaced by compiz, which, BTW, is installed by default in Ubuntu.

The very first post at the top of this very section of the Forums is:

[http://ubuntuforums.org/showthread.php?t=809695](http://ubuntuforums.org/showthread.php?t=809695)

Please read.

---

### Post by ash369 on 2009-01-02
Really sorry steveneddy i read that post not long ago after adding the post above. Using ccsm and screenlets now really cool effects 3d cube is great!

At least other people new to Ubuntu can refer to this thread if they don't read like me ^^

Just wanted to ask a quick question, not really relevant to this topic but i have 6 different boot options that i can select when my computer starts up. I was wondering if deleting some options i don't need will effect anything?

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		87a853fc-d401-4f06-b1ad-4d44ef054efb
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=87a853fc-d401-4f06-b1ad-4d44ef054efb ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		87a853fc-d401-4f06-b1ad-4d44ef054efb
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=87a853fc-d401-4f06-b1ad-4d44ef054efb ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		87a853fc-d401-4f06-b1ad-4d44ef054efb
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=87a853fc-d401-4f06-b1ad-4d44ef054efb ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		87a853fc-d401-4f06-b1ad-4d44ef054efb
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=87a853fc-d401-4f06-b1ad-4d44ef054efb ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		87a853fc-d401-4f06-b1ad-4d44ef054efb
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
chainloader	+1

I was going to take out the older kernal boot, would this be ok?

---

### Post by Forlong on 2009-01-02
Just remove the kernels you don't use via Synaptic. The list will be updated accordingly.

Please do this only if you know what you are doing.

---

### Post by ash369 on 2009-01-02
I want to take out the older version 

title Ubuntu 8.10, kernel 2.6.27-7-generic
uuid 87a853fc-d401-4f06-b1ad-4d44ef054efb
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=87a853fc-d401-4f06-b1ad-4d44ef054efb ro quiet splash
initrd /boot/initrd.img-2.6.27-7-generic
quiet

title Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid 87a853fc-d401-4f06-b1ad-4d44ef054efb
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=87a853fc-d401-4f06-b1ad-4d44ef054efb ro single
initrd /boot/initrd.img-2.6.27-7-generic

So i would uninstall this kernel image?

linux-image-2.6.27-7-generic
Linux kernel image for version 2.6.27 on x86/x86_64

And keep this one:

linux-image-2.6.27-9-generic
Linux kernel image for version 2.6.27 on x86/x86_64

---

### Post by Forlong on 2009-01-03
Seems correct to me.

---

### Post by ash369 on 2009-01-03
Thanks for the help Forlong, worked great and only 4 options now.

---

