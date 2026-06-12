---
title: "ttyUSB0 device."
date: 2006-03-28
forum: Desktop Environments
---

### Post by pdl5000 on 2006-03-28
I have an USB Serial device that I am trying to get to work under Ubuntu.  I installed the usbutils, and I have 'usb serial' & 'usb core' loaded.  I do not see /dev/ttyusb0, so how else would I access the port?  

NOTE:  This device works fine under Windows (via COM3), but I am really trying to ditch Windows so any help would be strongly appreicated.

Thanks,
Paul

---

### Post by scubajeff on 2006-03-28
I don't know what exactly your device is. But my Palm use ttyUSB0 to sync with Ubuntu. The /dev directory is managed by udev, so every device file is created dynamically. What I see on my system is: when I connect my Palm to the usb port and push the sync button on Palm, the /dev/ttyUSB0 will be created on the fly. And after the sync is over, the /dev/ttyUSB0 gone too. So you might not see the /dev/ttyUSB0 device file if your device is not activated.

---

