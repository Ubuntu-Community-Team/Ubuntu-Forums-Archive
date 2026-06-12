---
title: "Broadcom BCM4311 wireless doesnt work after reboot 11.10"
date: 2011-10-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by XxTriviumxX on 2011-10-15
Hi, like in every reinstallation I download the driver from the additional driver app, then i install the wireless plugin with ndiswapper (the .inf file etc..) then my wireless works fine !  then when i reboot my laptop i have to reinstall the driver again with ndiswapper .. how can i make it a permanent install ?  in ndiswapper it says its installed but i have to delete my driver and reinstall it  every time i shut down my laptop . Can anyone help me ? i can provide more information...

---

### Post by varunendra on 2011-10-17
I don't think you need ndiwrapper for BCM4311. Just uninstall it, and install firmware-b43-installer and b43-fwcutter instead.

Make sure 'multiverse' repository is enabled in 'Software Sources' (along with default ones), then run the following command in a terminal-
```
sudo apt-get install firmware-b43-installer b43-fwcutter
```

If having problems, please follow this guide and post back where you have the problem: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by garvinrick4 on 2011-10-17
Might have to purge these before the correct drivers will load, broadcom thing (maker of card and driver). The code just makes sure anything else bcm is removed so your correct drivers can load.
Link from broadcom. (3.0 and up kernels and 11.10 uses 3.0 and up) Natty is below 3.0 just ignore the link.
[http://www.broadcom.com/docs/linux_sta/bcma.txt](http://www.broadcom.com/docs/linux_sta/bcma.txt)

```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```From:
[http://ubuntuforums.org/showthread.php?t=1861669](http://ubuntuforums.org/showthread.php?t=1861669)

---

### Post by XxTriviumxX on 2011-10-17
thanks now it works perfectly :P

---

### Post by Do0d on 2012-05-07
> **varunendra said:**
> I don't think you need ndiwrapper for BCM4311. Just uninstall it, and install firmware-b43-installer and b43-fwcutter instead.

Make sure 'multiverse' repository is enabled in 'Software Sources' (along with default ones), then run the following command in a terminal-
```
sudo apt-get install firmware-b43-installer b43-fwcutter
```

If having problems, please follow this guide and post back where you have the problem: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

This works for a fresh install of 12.04, just remove the drivers that auto install with	

Code:

sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source

as garvinrick4 stated and your up and running!

---

