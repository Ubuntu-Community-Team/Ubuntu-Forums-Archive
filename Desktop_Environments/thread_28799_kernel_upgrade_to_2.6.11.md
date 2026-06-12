---
title: "kernel upgrade to 2.6.11"
date: 2005-04-21
forum: Desktop Environments
---

### Post by SteveGodfrey on 2005-04-21
I'd like to upgrade the kernel from 2.6.10 to 2.6.11 to see if I have more success with the touchpad but I can't find 2.6.11 in the repositories.

Can someone point me in the right direction for installing the new kernel?

Thanks

---

### Post by nautilus on 2005-04-21
it's certainly there:

p   linux-image-2.6.11-1-386                                              - Linux kernel image for version 2.6.11 on 386.
p   linux-image-2.6.11-1-386                                              - Linux kernel image for version 2.6.11 on 386.
p   linux-image-2.6.11-1-686                                              - Linux kernel image for version 2.6.11 on PPro/Celeron/PII/PIII/PIV.
p   linux-image-2.6.11-1-686                                              - Linux kernel image for version 2.6.11 on PPro/Celeron/PII/PIII/PIV.
p   linux-image-2.6.11-1-686-smp                                          - Linux kernel image for version 2.6.11 on PPro/Celeron/PII/PIII/PIV SMP.
p   linux-image-2.6.11-1-686-smp                                          - Linux kernel image for version 2.6.11 on PPro/Celeron/PII/PIII/PIV SMP.
p   linux-image-2.6.11-1-k7                                               - Linux kernel image for version 2.6.11 on AMD K7.
p   linux-image-2.6.11-1-k7                                               - Linux kernel image for version 2.6.11 on AMD K7.
p   linux-image-2.6.11-1-k7-smp                                           - Linux kernel image for version 2.6.11 on AMD K7 SMP.
p   linux-image-2.6.11-1-k7-smp                                           - Linux kernel image for version 2.6.11 on AMD K7 SMP.

deb [http://ftp.ipv6.heanet.ie/pub/ubuntu](http://ftp.ipv6.heanet.ie/pub/ubuntu) hoary main restricted universe multiverse
deb-src [http://ftp.ipv6.heanet.ie/pub/ubuntu](http://ftp.ipv6.heanet.ie/pub/ubuntu) hoary main restricted
^- my setup.

have you updated your local package list recently?

---

### Post by SteveGodfrey on 2005-04-21
Hey I'm getting good at this!

apt-get update 

and now I have the 2.6.11 kernels :-)

It's installing as we speak.

Thanks for the help.

---

### Post by XDevHald on 2005-04-21
Hmm, in a way that kinda worries me because the 2.6.11 kernel is NOT stable just yet. If I were you, I would hold off on that install for awhile, and put on the 2.6.10-5 kernel 686/i686 and keep your system running if you want it to live ;)

I'm just kidding on that last part, if you come accross errors when you reboot, such as **kernel panic error **just reboot, and push **ESC **when you see it starting to load the system with a countdown time of 3 seconds.

The 2.6.11 freezes your HD and your desktop once you login, not a good thing, but can be fixed VERY easily, but I would check to see if your system can handle the 2.6.11 before doing anything else with it.

---

### Post by Technoviking on 2005-04-21
[QUOTE=SteveGodfrey]I'd like to upgrade the kernel from 2.6.10 to 2.6.11 to see if I have more success with the touchpad but I can't find 2.6.11 in the repositories.

Can someone point me in the right direction for installing the new kernel?
[/QUOTE]
This would not be a Toshiba Touchpad by chance?

Mike

---

### Post by SteveGodfrey on 2005-04-21
Spooky yes it's a Toshiba Tecra S1 with a dual point Alps touchpad

oh I'm talking to via using 2.6.11!

You're right about stability, gaim seems to lock gnome.

But at least the tap to click has gone!!!

---

### Post by BoHu on 2005-04-30
i agree with whoever said 2.6.11 is not stable. When i try to boot .11 my system freezes right after the log-in screen :-(

---

### Post by Dracontopes on 2005-04-30
[QUOTE=BoHu]i agree with whoever said 2.6.11 is not stable. When i try to boot .11 my system freezes right after the log-in screen :-([/QUOTE]
 Load your kernel with **noinotify** parameter. You can edit your /boot/grub/menu.lst and put this in like this:

```

title		Ubuntu, kernel 2.6.11-1-k7 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.11-1-k7 root=/dev/sda1 ro quiet splash **noinotify**
initrd		/boot/initrd.img-2.6.11-1-k7
savedefault
boot

```

That fixed the problem here.

---

### Post by abhaysahai on 2005-05-06
Thanks Dracontopes,
I was using 2.6.10 because of this error. However, now I can easily boot with 2.6.11 kernel.

Thanks again.
Abhay

---

