---
title: "How Do I Refresh Installed Drives Without Reboot?"
date: 2009-04-16
forum: General Help
---

### Post by Raemir on 2009-04-16
This has to be simple, but I can't figure it out.  I needed to wipe a couple SATA hard drives prior to a sale so I hooked one up via a USB adapter (external).  The machine didn't recognize that I'd added a new drive.  I had one machine open so I "installed" a drive with a regular SATA connector (internal), and it still wasn't recognized.  However, when I rebooted that machine the drive properly showed up as /dev/sdc.

When this drive is finished being overwritten I'll need to do two more, so how do I refresh the installed drives without rebooting the entire machine.

Thanks,
Raemir

---

### Post by cariboo on 2009-04-16
Hot plugging SATA drives does seem to work very well, the way I get around it is to plug the drive in, then plug in a usb thumb drive. This seems to start the process of recognizing the drive.

Jim

---

