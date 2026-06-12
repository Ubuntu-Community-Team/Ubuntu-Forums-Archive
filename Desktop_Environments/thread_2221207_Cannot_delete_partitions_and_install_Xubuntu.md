---
title: "Cannot delete partitions and install Xubuntu"
date: 2014-05-01
forum: Desktop Environments
---

### Post by Ronjet on 2014-05-01
Hello,

I have created livs usb with Xubuntu 14.04 but I've got problem with installation process. I am unable to delete partitions: sda4,sda5,sda6. There's is no +/- highlighted during installation process.

Screenshots:

[http://i.imgur.com/ildmmcr.png](http://i.imgur.com/ildmmcr.png)

[http://i.imgur.com/dIh5PHl.png](http://i.imgur.com/dIh5PHl.png)

How can I delete those partitions and install Xubuntu?

Best regards,
Ronald.

---

### Post by Xubuntist on 2014-05-01
Hello Ronjet

If you right-click on **sda6** can you choose "*stop swapping*" or something similar? If so, this shold unlock the partitions allowing you to delete them.

Rgds

François

---

### Post by oldfred on 2014-05-01
Your old install is LVM, so most partition tools do not work on the LVM. You may have to delete the LVM first?

       LVM gui tool:
[http://www.howtogeek.com/127246/linux-sysadmin-how-to-manage-lvms-with-a-gui/](http://www.howtogeek.com/127246/linux-sysadmin-how-to-manage-lvms-with-a-gui/)
sudo apt-get install system-config-lvm


 LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)

---

### Post by Ronjet on 2014-05-02
> **Xubuntist said:**
> Hello Ronjet

If you right-click on **sda6** can you choose "*stop swapping*" or something similar? If so, this shold unlock the partitions allowing you to delete them.

Rgds

François

> **oldfred said:**
> Your old install is LVM, so most partition tools do not work on the LVM. You may have to delete the LVM first?

       LVM gui tool:
[http://www.howtogeek.com/127246/linux-sysadmin-how-to-manage-lvms-with-a-gui/](http://www.howtogeek.com/127246/linux-sysadmin-how-to-manage-lvms-with-a-gui/)
sudo apt-get install system-config-lvm


 LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)

Problem solved, thank you very much :)

---

