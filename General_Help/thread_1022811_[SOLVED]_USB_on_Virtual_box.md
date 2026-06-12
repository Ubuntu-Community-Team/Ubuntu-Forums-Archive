---
title: "[SOLVED] USB on Virtual box"
date: 2008-12-27
forum: General Help
---

### Post by underdog512 on 2008-12-27
I am using Sun Virtual box (the non-open source edition) and I am having an issue with usb. When I click on settings I immediately get an error message stating that "Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND).The service might not be installed on the host computer." I really need to be able to use USB in the virtual machine.

---

### Post by damis648 on 2008-12-27
You need to make a modification to your fstab for this to work:
Open up your fstab for editing
```
gksudo gedit /etc/fstab
```
and add this line at the bottom:
```
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0
```
and save. Reboot, and USB should work. :popcorn:

EDIT PS: Also, be sure to unmount any devices that will be mounted by the VM, as vbox will forcefully unmount them (equivalent of directly unplugging)

---

### Post by underdog512 on 2008-12-27
That did it thanks!

---

