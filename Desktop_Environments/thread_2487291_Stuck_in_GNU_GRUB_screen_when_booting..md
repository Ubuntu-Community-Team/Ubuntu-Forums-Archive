---
title: "Stuck in GNU GRUB screen when booting."
date: 2023-05-29
forum: Desktop Environments
---

### Post by ginousi on 2023-05-29
Hi, 

We encounter system stuck in GNU GRUB screen when booting,
it occurred sometimes, randomly.
Our installed Ubuntu version is 22.04.2 LTS or 23.04.
Platform is Intel Alder lake with Insyde BIOS.

issue screenshot
[https://i.imgur.com/W45T73G.jpg](https://i.imgur.com/W45T73G.jpg)

Could you tell us what component/setting to cause this GNU GRUB screen occurred?


We follow this video's commands to patch it, 
then can avoid this issue.
but it has any side effect for this patch?

 >> [https://www.youtube.com/watch?v=WOG-YIihgHQ](https://www.youtube.com/watch?v=WOG-YIihgHQ) 


Thanks & Regards.
USIGino

---

### Post by oldfred on 2023-05-29
Please remove in line screen shot & only use attachments.
 If you use the Forum's advanced editor, you can use the paperclip icon to attach screenshots or other info. Post #4 , also no larger than1024x768 if photo
[https://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098](https://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098)

And grub> is a common issue, and that is all you need to post.

But it works sometimes?
Is there a timing issue on boot and mounting of drive(s)?

Is UEFI most current firmware. And if SSD does it have latest firmware?

Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed. Use often updated ppa version over somewhat older ISO with your USB installer  or any working install.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

You may be able to manually boot.
[https://help.ubuntu.com/community/Grub2/Troubleshooting](https://help.ubuntu.com/community/Grub2/Troubleshooting)

Find partitions, example finds / or /boot in (0,5):
grub> ls
grub> ls (hd0,5)/
ls # Do you see (hd0), (hd0,5) ? If so, run the next command. Change if not hd0,5.
configfile (hd0,5)/boot/grub/grub.cfg
OR:
set prefix=(hd0,5)/boot/grub
set root=(hd0,5)
linux (hd0,5)/boot/vmlinuz root=/dev/sda5 ro
initrd (hd0,5)/boot/initrd.img
boot

---

### Post by ginousi on 2023-06-08
Hi,

For system sometimes stuck in GNU GRUB screen when booting,
Our BIOS vendor Insyde fixed it.


Thanks & Regards.
USIGino

---

