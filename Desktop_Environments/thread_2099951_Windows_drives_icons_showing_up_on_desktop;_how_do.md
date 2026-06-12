---
title: "Windows drives icons showing up on desktop; how do I remove them?"
date: 2012-12-31
forum: Desktop Environments
---

### Post by DBogaard on 2012-12-31
Just installed Xubuntu 12.10. Everything great, except for one thing: It's a dual boot with Windows 7, and on the Xubuntu desktop icons show up for each Windows 7 drive. I know I can remove them using Desktop settings -> Icons -> unclick Removable Devices, but this also removes the icons for other things like my external hard drive and USB Stick. 

I only want to get rid of the desktop icons related to the windows drives, how do I do this?

Thanks in Advance!

---

### Post by The Cog on 2012-12-31
From your **Start** menu, go **Settings Manager**, then choose **Desktop**, go to the **Icons** tab and un-check Removable Devices.

Edit - just re-read your original post. No, there is no other way at the moment. I believe there is a bug report outstanding on the issue.

---

### Post by pavitrabalse on 2012-12-31
I have used windows7 os before. i think this ubuntu is totally different type of os. i have not used but want to try once.

---

### Post by DBogaard on 2012-12-31
Hi The Cog,

Thanks for your reply; however this does not solve my problem. Unchecking that item also means that my external hard drive and USB stick won't show up anymore on my desktop. I just want to remove the icons for the internal drives from Windows 7 from the desktop.

GrtD

---

### Post by vanadium on 2012-12-31
You can mount the windows drives in the traditional way, i.e., by including an entry for them in /etc/fstab. Then they will not be shown as a separate drive.

---

### Post by Toz on 2012-12-31
You can hide the windows partitions using udev. Create (as root) the file **/etc/udev/rules.d/10-hide-partitions.rules** with th following content:
```

KERNEL=="sda3", ENV{UDISKS_PRESENTATION_HIDE}="1"

```
...change **sda3** to the correct partition name that you want to hide. If you have more than one partition to hide, simply create another entry.

Probably need to reboot for changes to take effect.

---

### Post by Toz on 2012-12-31
> **Toz said:**
> You can hide the windows partitions using udev. Create (as root) the file **/etc/udev/rules.d/10-hide-partitions.rules** with th following content:
```

KERNEL=="sda3", ENV{UDISKS_PRESENTATION_HIDE}="1"

```
...change **sda3** to the correct partition name that you want to hide. If you have more than one partition to hide, simply create another entry.

Probably need to reboot for changes to take effect.

Looks like its changed in 12.10. The proper code is as follows:
```

KERNEL=="sda3", ENV{UDISKS_IGNORE}="1"

```

---

