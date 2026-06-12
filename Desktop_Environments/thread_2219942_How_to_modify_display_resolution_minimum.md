---
title: "How to modify display resolution minimum?"
date: 2014-04-26
forum: Desktop Environments
---

### Post by K.Kong on 2014-04-26
I have just installed Ubuntu 14.04 in a virtual machine (Windows 8 Hyper-V).  Everything went flawlessly.  The only issue is the display sizes has only one option: current 1152x864, minimum 1152x864, and maximum 1152x864.

How to I set it to 800x600 or, if that is outside specifications, 1024x768?

Thanks.

---

### Post by Doug_Coleman on 2014-04-26
There are probably better ways, but this worked for me (setting my resolution to the current max of the synthetic display driver which is 1920x1080):
[FONT=arial]
sudo nano /etc/default/[/FONT][FONT=arial]grub[/FONT][FONT=arial]/cfg[/FONT][FONT=arial]set the GRUB_CMDLINE_LINUX_DEFAULT to include [FONT=Ubuntu Mono]"quiet splash video=hyperv_fb:1920x1080"[/FONT][/FONT]
[FONT=arial]sudo  update-grub


shutdown then power on your vm
[/FONT]


Hope this helps,
Doug Coleman

---

### Post by K.Kong on 2014-04-27
Thanks.

cfgset is an empty file.  What is the syntax o the line to add?

---

