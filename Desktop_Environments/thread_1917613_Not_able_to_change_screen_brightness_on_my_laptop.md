---
title: "Not able to change screen brightness on my laptop"
date: 2012-01-30
forum: Desktop Environments
---

### Post by Sammax on 2012-01-30
I have a sony laptop with nvidia graphics card....i have updated the restricted drivers but the function keys wont work....please someone help...its difficult to work with full brightness...

---

### Post by JC Cheloven on 2012-01-30
> **Sammax said:**
> I have a sony laptop with nvidia graphics card....i have updated the restricted drivers but the function keys wont work....please someone help...its difficult to work with full brightness...
Sure it is ;)

In the system menu you should have the nvidia-settings entry. It is the control window for the proprietary nvidia driver. There you'll find an item named "X server color correction". You can adjust brightness, contrast and gamma nicely from there.

---

### Post by Sammax on 2012-01-30
[JC Cheloven]("http://ubuntuforums.org/member.php?u=469152") thanx a lot for the quick reply.....it works nicely.....
but the functions keys wont work.....no way we can fix that??

---

### Post by JC Cheloven on 2012-01-30
> **Sammax said:**
> [JC Cheloven]("http://ubuntuforums.org/member.php?u=469152") thanx a lot for the quick reply.....it works nicely.....
but the functions keys wont work.....no way we can fix that??

If you care, please open a terminal, and edit the relevant system file by typing this comand ```
sudo nano /etc/default/grub
```
Then search for the line GRUB_CMDLINE_LINUX and edit it to look like this
```
GRUB_CMDLINE_LINUX="acpi_backlight=vendor"
```
Save and exit. Then, again at terminal ```
sudo update-grub
```
Then reboot.

Hope it works for you.

---

