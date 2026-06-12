---
title: "Ubuntu cannot boot correctly after Windows 10 updating"
date: 2022-01-03
forum: Desktop Environments
---

### Post by ruwan2 on 2022-01-03
Hello,

I bought a Lenovo Legion T5 desktop one year ago. I made it dual boot a Ubuntu 20.04 LTS on its SSD 256GB M.2 drive with Windows 10. The dual boot was successful until after Windows 10 got an updates. The GRUB menu font was changed to bigger and an error message as shown in below picture:
[https://ibb.co/TbXbF4b](https://ibb.co/TbXbF4b)

It says: "Failed to open \EFI\UBUNTU\Failed to load image \EFI\UBUNTU\start_image0 returned Invalid Parameter, failing back to default loader"
[IMG]https://ibb.co/TbXbF4b[/IMG]
[IMG]https://ibb.co/TbXbF4b[/IMG]


If I re-install Ubuntu, GRUB menu can go back to normal. Unfortunately, a recent Windows update made the above error appears again.


How can I avoid this error for good?


Thanks in advance.

---

### Post by Autodave on 2022-01-04
This is not an unheard of issue.....Win loves to screw Linux.  The way that I finally found is that I installed a second SSD and installed Ubuntu on that. AFTER disconnecting the Windows drive.  So, I pick, on booting, from the menu which drive I want the machine to boot to.

---

### Post by ruwan2 on 2022-01-04
Yes, I found a similar solution is to re-install GRUB to the EFI of the 2nd SSD.
Thanks!

---

