---
title: "inspiron 1525 Integrated webcam problem"
date: 2008-03-12
forum: Dell  Ubuntu Support
---

### Post by ssp3nc3r on 2008-03-12
hello,

I recently recieved my shiney new Dell Inspiron 1525 which came pre-installed w/ vista.  The first thing i did was to install Gutsy on it.  I downloaded and installed from ubuntu-dell-1525n-intelvideo-reinstall.iso from the linux dell site.  Everything works perfectly *except* the integrated webcam.  I've spent some time now trying to figure out exactly what the problem is, and have not been able to determine why it is not working.  'dmesg|grep uvc'  shows me:

 [   13.492000] uvcvideo: Found UVC 1.00 device Laptop Integrated Webcam (05a9:2640)
[   13.492000] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp. 26).
[   13.548000] usbcore: registered new interface driver uvcvideo

and 'lsmod|grep uvc' shows:

uvcvideo               48644  0 
compat_ioctl32          2304  1 uvcvideo
videodev               29312  1 uvcvideo
v4l1_compat            15364  2 uvcvideo,videodev
v4l2_common            18432  2 uvcvideo,videodev
usbcore               138632  8 hsfosspec,uvcvideo,xpad,hci_usb,usbhid,ehci_hcd,uhci_hcd

I have tried unloading and reloading the module, and still no joy.  When the module is loaded, the blue led by the camera does flash on, and when i run an app (like Ekiga Softphone, or XawTV) the led does flash on, but i'm given an error message stating that the app can't open the integrated webcam.  

I'm pretty stumped at this point.  Any ideas, or advice would be appreciated.

tia,

Steve

---

### Post by CRCarl on 2008-03-13
Run a lsusb and a lspci. Post the results. 

C

---

### Post by ssp3nc3r on 2008-03-13
'lsusb'
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. 
Bus 006 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 046d:c51b Logitech, Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 005 Device 005: ID 0a5c:4503 Broadcom Corp. 
Bus 005 Device 003: ID 413c:8126 Dell Computer Corp. 
Bus 005 Device 004: ID 0a5c:4502 Broadcom Corp. 
Bus 005 Device 002: ID 0a5c:4500 Broadcom Corp. 
Bus 005 Device 001: ID 0000:0000  
'lspci'
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
02:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)


tia,

Steve

---

### Post by notwen on 2008-03-13
Found [this]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Built_In_Digital_Camera_Does_Not_Work") on the Dell Linux Wiki.  Hope it helps.  =]

---

### Post by ssp3nc3r on 2008-03-13
> **notwen said:**
> Found [this]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Built_In_Digital_Camera_Does_Not_Work") on the Dell Linux Wiki.  Hope it helps.  =]

Thanks! this got the webcam working for Ekiga.  I changed the plugin to v4l2 as suggested in the link above, and voila.. worked perfectly.  So this proves to me that the hardware is working correctly, but begs the question: Can i change something to make it work for all webcam apps globally, or do i have to only use applications which have this plugin available ??  I really don't understand where the real issue is...  any further explanation would be greatly appreciated.

Thanks,

Steve

---

### Post by notwen on 2008-03-13
You may want to make a thread in the hardware/laptop sub-forum regarding global settings regarding this plugin and what exactly it does to enable your webcam.  I do not have  a laptop w/ a webcam and cannot comment anything of use on it.  Best of luck w/ this.  =]

---

### Post by edwardblum on 2008-03-21
I have the same camera as you, I to managed to get the webcam to work using V4L2, however skype had patchy support for it, I found installing all the ubuntu updates and installing  the DELL Linux BackPorts available from [here]("http://linux.dell.com/files/ubuntu/linux-backports-modules-2.6.22-14-generic_2.6.22-14.50_i386.deb") fixed it for me (tho the quality isnt quite at 2 mega pixels!)

---

