---
title: "Problems with wife's laptop after upgrades"
date: 2007-09-10
forum: Dell  Ubuntu Support
---

### Post by EABonney on 2007-09-10
Ok, I did an upgrade on my wife's new 1420 Dell using the KPackage maanger. It went just fine but now for whatever reason the laptop will not retain any of the login information required for my wireless network. If I do happen to get it running it is fine as long we don't have to reboot the machine. Once she reboots, the machine loses the information again. :(

The machine seems to be very slow now when trying to initially log onto her account and we have had some issues with closing applications, but I can't really narrow it down to this upgrade.

Shutting down seems to be hit and miss also. Sometimes it will work from the login manager and sometimes it won't. When it doesn't work we have to hold down the power button to force it to shutdown.

She is running KDE with KDM and kernel 2.6.20.-16.31-generic.

Does anyone know if it is possible to revert back to the initial kernel that she had installed without having to revert to factory defaults? Any ideas why KDE will not maintain the credentials needed to log into my wireless network?

Thanks,
-Eric

---

### Post by ridgeland on 2007-10-01
If she upgraded a kernel the old kernel should still be available as an option in GRUB.  The kernel upgrade caused problems for my wifes PC too.  I just set it to still boot to the old kernel by changing GRUB.
Look in /boot and you should see the two kernel versions.
I don't use KDE and cannot offer any suggestions there.

---

