---
title: "Digital USB Camera Program"
date: 2009-06-05
forum: General Help
---

### Post by unleadedblues on 2009-06-05
My digital camera was working just fine last week.  Now, when I plug it in the message to download pictures does not come up anymore.  I think that I might have uninstalled the application which handles this.  Does anyone know what application that might be?

Oh, gphoto2 recognizes the camera just fine and /var/log/messages shows the following when the phone is connected and then disconnected.  So, I think it is just an issue of the program instead of a system/drivers problem.

/var/log/messages
-----------------
usb 3-2: new full speed USB device using uhci_hcd and address 3
usb 3-2: configuration #1 chosen from 1 choice
usb 3-2: USB disconnect, address 3

Thanks,
Curt

---

### Post by jerrrys on 2009-06-05
go to Places>Computer and right click on camera (usb device) and choose the program that you want to open with...i usually use fspot for this...

---

### Post by unleadedblues on 2009-06-05
The camera doesn't show up anywhere under Places-> .

---

### Post by jerrrys on 2009-06-05
ok, if im following you, the camera is not doing auto mount. you can force mount [http://www.google.com/search?q=force+mount+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=force+mount+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a) or just restart your box, then do settings for camera...

i forgot to tell you to have camera plugged in durning restart...sorry...

---

