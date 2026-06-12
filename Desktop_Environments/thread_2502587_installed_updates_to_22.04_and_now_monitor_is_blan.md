---
title: "installed updates to 22.04 and now monitor is blank/black"
date: 2024-11-20
forum: Desktop Environments
---

### Post by howard_rutiezer on 2024-11-20
I posted this about 3 weeks ago in the "general" forum and received no replies so thought I would try here.

Inherited a desktop system that dual boots an older version of ubuntu, think it was one of the versions of ubuntu 18, and windows 10. I would install all ubuntu updates. Think windows is on an external drive.  Did not know password for windows. About 3 weeks ago updated to ubuntu 22.04  and it was successfully running on the machine. Set the system to run timeshift and believe there was at least 1 backup immediately after installing 22.04. About 2 weeks ago installed latest updates of 22.04. After this update the system start the boot process with everything looking ok, and then after the ubuntu splash screen the monitor would be black and nothing else was visible.

I know there is no problem with cables since I was able to start up windows 10 although could not login because do not know password, was able to run memtest and screen was working.

Any suggestions?

Was wondering if I could start up computer in a maintenance mode and from that command line mode invoke timeshift and restore the last working version of the OS?

Or some other suggestion?

---

### Post by grahammechanical on 2024-11-20
It would help if you told us the specification of the hardware and the partition layout. Do you see a Grub boot menu. We usually see a Grub boot menu when we dual boot. At the Grub boot menu select Advanced Options for Ubuntu and select either one of the older Linux kernels to boot or a kernel with recovery mode. That should load the Friendly Recovery menu.

At the recovery menu you can select Resume and that will load Ubuntu using an open source video driver. If that works the problem could be with the proprietary video driver.

Also, at the recovery menu select Network. That will establish an internet connection. When back at the recovery menu select Root. That will take you to a root shell prompt. You can then run commands like apt update and apt upgrade. That sometimes fixes problems. Or, you can run the timeshift commands. To get back to the recovery menu type exit and then select Resume.

Regards

---

### Post by yancek on 2024-11-22
>  Think windows is on an external drive.

That is highly unlikely as windows is an has been designed NOT to install to an external drive.  There is or has been software that could be used to do this.  If windows is actually on an external hard drive connected by usb, that might be why it does not boot.  That is by design.

>  About 3 weeks ago updated to ubuntu 22.04  

Does that mean you installed 22.04 to the drive overwriting the previous by downloading the Ubuntus iso, writing it to a USB and booting the USB and installing?  Updating generally refers to updating from a terminal or the software manager which would have been difficult if you had 18.04 installed as supported ended for it in April, 2023.

If you answer the questions in post 2 that would help and also post the output of the command:  sudo parted -l to list partition information.  You can use the Ubuntu USB to do this.

---

### Post by howard_rutiezer on 2024-11-23
I now think the version computer was on was [Ubuntu 20.04.6 LTS (Focal Fossa)]("https://releases.ubuntu.com/focal/").
Started the computer and in bios went to grub page and there were 5 options:
*Ubuntu
Advanced options for Ubuntu
2 lines of memory test
Windows 10 (on /dev/sdb1)

Took photos of each of the pages but
Did not see how to do file attachments.
Saw [https://wiki.ubuntu.com/HelpOnConfiguration/FileAttachments](https://wiki.ubuntu.com/HelpOnConfiguration/FileAttachments)
but still do not see how to attach files.

Since can not do the attachments have to describe what happened.

Clicked on advanced options and went to 6.8.0-48-generic (recovery mode).
Got to recovery menu and all the lines were split over multiple lines and did not know what to do.
Think I pressed enter.
And after a while ubuntu came up with the jellyfish page.

Previously when trying multiple times to boot, all that happened in the end for a blank/black page.

Looks like problem is solved.
Did a timeshift backup.

Thanks to all of you who submitted suggestions.

May buy a key for windows 11 since do not know password for the windows 10 on computer.
Don't know yet; have not dual booted windows for many, many years.

---

