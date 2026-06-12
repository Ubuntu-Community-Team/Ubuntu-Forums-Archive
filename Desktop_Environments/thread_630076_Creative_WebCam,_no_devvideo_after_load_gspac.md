---
title: "Creative WebCam, no /dev/video after load gspac"
date: 2007-12-02
forum: Desktop Environments
---

### Post by ricewin on 2007-12-02
Hi,

I have a Creative WebCam PD1100, which is supported by spca5xx. My system is ubuntu 7.10

After plug it in usb, I can see it with
lsusb
Bus 001 Device 002: ID 041e:401b Creative Technology, Ltd 

and the gspca is loaded with modprobe gspca
lsmod | grep gspca
gspca                 608336  0 
videodev               29312  1 gspca
usbcore               138632  4 gspca,ehci_hcd,uhci_hcd

However, there is no /dev/video files.
ls -al /dev/video*
ls: /dev/video*: No such file or directory

I also installed camorama. It says "could not connect to video device. Please check connection". Please let me know how to creat this /dev/video file.

Thank you

---

