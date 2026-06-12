---
title: "Ubuntu USB flash startup disc"
date: 2009-05-01
forum: General Help
---

### Post by dontwindowsme on 2009-05-01
Hi. I'm trying to make full featured Ubuntu on usb flash key. Is it possible? 
I want have two in one, use and install Ubuntu from one flash key.
First, I have created usb startup disk with Ubuntu usb startup disc creator. Then Nvidia proprietary videodriver was installed on the system. But restarting the system I found that Ubuntu don't use nvidia driver. I have persistent file 512 mb, this file saves only home directory, and videodriver config  is saved in etc/x11/xorg.conf that is not in home directory. I have mannually write string driver "nvidia" in etc/x11/xorg.conf, but this string disappeared if Ubuntu restarted. How does make Ubuntu use nvidia driver?

---

### Post by codeseer on 2009-05-01
> **dontwindowsme said:**
> Hi. I'm trying to make full featured Ubuntu on usb flash key. Is it possible? 
I want have two in one, use and install Ubuntu from one flash key.
First, I have created usb startup disk with Ubuntu usb startup disc creator. Then Nvidia proprietary videodriver was installed on the system. But restarting the system I found that Ubuntu don't use nvidia driver. I have persistent file 512 mb, this file saves only home directory, and videodriver config  is saved in etc/x11/xorg.conf that is not in home directory. I have mannually write string driver "nvidia" in etc/x11/xorg.conf, but this string disappeared if Ubuntu restarted. How does make Ubuntu use nvidia driver?

Well, I think you'd have to set up some type of boot loader on it. The drive would have to be pretty big as well. I'd think you would have the boot information up front, then give a little space and start with the system install, then at the very end of the drive put the Live CD part. You would also have to be careful not to 'need' to exceed what you allocate for them up front.

---

### Post by dontwindowsme on 2009-05-01
> **codeseer said:**
> Well, I think you'd have to set up some type of boot loader on it. The drive would have to be pretty big as well. I'd think you would have the boot information up front, then give a little space and start with the system install, then at the very end of the drive put the Live CD part. You would also have to be careful not to 'need' to exceed what you allocate for them up front.

Thank you. But I need more detailed information about it, even step-by-step instruction. Can you help me? What about script that automaticly writes string 'driver "nvidia"' in etc/x11/xorg.conf during Ubuntu booting?

---

### Post by codeseer on 2009-05-01
> **dontwindowsme said:**
> Thank you. But I need more detailed information about it, even step-by-step instruction. Can you help me? What about script that automaticly writes string 'driver "nvidia"' in etc/x11/xorg.conf during Ubuntu booting?

I'm not sure exactly about the step-by-step instruction right off hand. Maybe someone else will come by that can show you exactly how to do it. If not, then I'll try to make time soon to do it and write a guide up. You'll be looking to set it up something like this, but you'll have an actual install partitioned off and then edit the menu.lst: [http://ubuntuforums.org/showthread.php?t=1098238](http://ubuntuforums.org/showthread.php?t=1098238)

Have you tried setting xorg.conf to read-only? That or you could possibly just write a bash script that copies a backup, known good, xorg.conf over the one that's there.

---

### Post by dontwindowsme on 2009-05-01
Read-only? I thought about it. May be it will work. I'll try. 
If you can write bash script or any instruction please pm me. Thanks a lot.

---

### Post by dontwindowsme on 2009-05-02
No, it's not working. After Ubuntu reboot the atributes of xorg.conf file changes to their default values (read-and-write). It's only way remaining. Can anyone write bash script for automatic rewriting xorg.conf file at Ubuntu boot process?

---

