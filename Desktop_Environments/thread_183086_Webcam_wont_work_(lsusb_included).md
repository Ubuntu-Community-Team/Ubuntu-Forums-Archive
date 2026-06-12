---
title: "Webcam wont work (lsusb included)"
date: 2006-05-27
forum: Desktop Environments
---

### Post by Rackerz on 2006-05-27
It's a Logitech Quickcam Messenger, I reinstalled Ubuntu but before I reinstalled my cam was working. 

Bus 004 Device 001: ID 0000:0000
Bus 001 Device 002: ID 046d:08f0 Logitech, Inc. QuickCam Messenger
Bus 001 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

That's my lsusb and as far as I know my chipset is common and works with alot drivers. 

I've tried easycam2 but it just keeps saying, 'Could not connect to video device /dev/video0). Please check connection.'

I've tried the other howto's but I just can't seem to get my cam working even though it has worked fine before. 

Darren

---

### Post by marcos89 on 2006-05-27
modprobe quickcam  < run this command.

---

### Post by Rackerz on 2006-05-29
EDIT: I got it working in the end, the drivers didn't install correctly the first two times :S.

---

