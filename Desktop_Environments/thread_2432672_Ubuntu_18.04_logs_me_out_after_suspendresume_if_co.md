---
title: "Ubuntu 18.04 logs me out after suspend/resume if connected to external screen"
date: 2019-12-06
forum: Desktop Environments
---

### Post by Vermind on 2019-12-06
Hi,
I am having a strange problem with already two laptops using Ubuntu 18.04 Gnome (Vanilla Gnome session). If the laptop is suspended while connected to an external screen, when I resume it, I see the log in screen, and have to log in again to the computer. When I do, the session comes up with all my apps killed, just like a new login, but in a locked state, and I have to type my password again.

If the laptop is not connected to anything, suspending and resuming works normally; apps come up in the same state as before suspend, there is only the one password prompt and no login screen.

I have these versions of gnome-related packages installed: [https://pastebin.com/GgnbhsSV](https://pastebin.com/GgnbhsSV)
My grub CMDLINE has:
[FONT=Courier New]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash usbcore.autosuspend=-1 mem_sleep_default=deep nvidia-drm.modeset=0"[/FONT]


The two affected laptops are a Thinkpad T480S and Asus Zenbook S13 UX392FN: [https://www.asus.com/Laptops/ASUS-ZenBook-S13-UX392FN/](https://www.asus.com/Laptops/ASUS-ZenBook-S13-UX392FN/)
Both laptops have dual graphics, and use nVidia graphics through the out-of-the-box offloading that you get when you install Ubuntu 18.04 and enable the nVidia driver.

EDIT: I think I am getting bitten by this:
[https://askubuntu.com/questions/1035208/ubuntu-18-04-error-on-waking-up-from-sleep-read-error-on-swap-device/1050201#1050201](https://askubuntu.com/questions/1035208/ubuntu-18-04-error-on-waking-up-from-sleep-read-error-on-swap-device/1050201#1050201)
The issue is described there as follows:
[FONT=Book Antiqua]the most frequent symptom is a crash of Xorg/Xwayland, i.e. killing the entire GUI, when a laptop is woken from system sleep. Frequency of the bug is described as once every few days[2].[/FONT]

Kernel version (uname -a):
[FONT=Courier New]Linux lgz-UX392FN 5.0.0-37-generic #40~18.04.1-Ubuntu SMP Thu Nov 14 12:06:39 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux[/FONT]
I have added  [FONT=Courier New]scsi_mod.scan=sync[/FONT] to kernel CMDLINE and checking out if that helps.


Any ideas?
Thanks.

---

### Post by Vermind on 2019-12-11
After adding scsi_mod.scan=sync to kernel CMDLINE I have not experienced this any more. This seems to be a working workaround. Marking this thread as solved.

---

### Post by zenb00ker on 2020-05-05
Sorry to hook up your thread @Vermind but I'm very intrested in running Linux on a zenbook S13 UX392 you mentioned.

Can you tell me a little about the hardware support? Does everything work like expected (beside the fingerprint reader which is badly placed inside the touchpad...). And how is the fan control? Is it on/loud very often or does it work silently on low loads with Linux?

Thanks!

---

