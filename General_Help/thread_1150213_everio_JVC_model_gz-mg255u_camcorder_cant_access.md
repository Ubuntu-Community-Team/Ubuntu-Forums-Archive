---
title: "everio JVC model gz-mg255u camcorder cant access"
date: 2009-05-05
forum: General Help
---

### Post by clevefan on 2009-05-05
I have a everio jvc model gz-mg255u. I turn it on and plug it into the usb slot. The menu on the camera lets me select connect to device. I select it. Then nothing happens on ubuntu. Plz help.

---

### Post by cariboo on 2009-05-05
What is the output of:

```
dmesg | tail -n15
```

When you plug your device in? The above command must be run in an Applications-->Accessories-->Terminal

---

### Post by clevefan on 2009-05-05
this is the output from the command you gave me. After my device was connected


clevefan@laptop:~$ dmesg | tail -n15
[29014.407400] usb 7-4: configuration #1 chosen from 1 choice
[29014.411395] scsi6 : SCSI emulation for USB Mass Storage devices
[29014.413546] usb 7-4: USB disconnect, address 7
[29014.448595] usb-storage: device found at 7
[29014.448606] usb-storage: waiting for device to settle before scanning
[29014.547687] usb 7-4: new high speed USB device using ehci_hcd and address 8
[29014.686094] Inbound IN=wlan0 OUT= MAC=00:1d:d9:76:eb:59:00:1c:df:3e:7d:65:08:00 SRC=68.197.164.54 DST=192.168.2.4 LEN=131 TOS=0x00 PREC=0x00 TTL=107 ID=30566 PROTO=UDP SPT=60958 DPT=6881 LEN=111 
[29015.625642] Inbound IN=wlan0 OUT= MAC=00:1d:d9:76:eb:59:00:1c:df:3e:7d:65:08:00 SRC=71.96.142.98 DST=192.168.2.4 LEN=131 TOS=0x00 PREC=0x00 TTL=110 ID=8146 PROTO=UDP SPT=32984 DPT=6881 LEN=111 
[29016.022576] Inbound IN=wlan0 OUT= MAC=00:1d:d9:76:eb:59:00:1c:df:3e:7d:65:08:00 SRC=77.87.93.180 DST=192.168.2.4 LEN=131 TOS=0x00 PREC=0x00 TTL=108 ID=61519 PROTO=UDP SPT=58788 DPT=6881 LEN=111 
[29016.086454] Inbound IN=wlan0 OUT= MAC=00:1d:d9:76:eb:59:00:1c:df:3e:7d:65:08:00 SRC=203.51.13.171 DST=192.168.2.4 LEN=131 TOS=0x00 PREC=0x00 TTL=100 ID=5721 PROTO=UDP SPT=27970 DPT=6881 LEN=111 
[29018.256604] Inbound IN=wlan0 OUT= MAC=00:1d:d9:76:eb:59:00:1c:df:3e:7d:65:08:00 SRC=88.73.227.50 DST=192.168.2.4 LEN=131 TOS=0x00 PREC=0x00 TTL=105 ID=16460 PROTO=UDP SPT=23807 DPT=6881 LEN=111 
[29018.356680] Inbound IN=wlan0 OUT= MAC=00:1d:d9:76:eb:59:00:1c:df:3e:7d:65:08:00 SRC=221.130.57.144 DST=192.168.2.4 LEN=132 TOS=0x00 PREC=0x00 TTL=105 ID=57761 PROTO=UDP SPT=61054 DPT=6881 LEN=112 
[29021.066505] Inbound IN=wlan0 OUT= MAC=00:1d:d9:76:eb:59:00:1c:df:3e:7d:65:08:00 SRC=120.28.171.128 DST=192.168.2.4 LEN=131 TOS=0x00 PREC=0x00 TTL=107 ID=5866 PROTO=UDP SPT=50858 DPT=6881 LEN=111 
[29021.544696] Inbound IN=wlan0 OUT= MAC=00:1d:d9:76:eb:59:00:1c:df:3e:7d:65:08:00 SRC=221.130.57.144 DST=192.168.2.4 LEN=132 TOS=0x00 PREC=0x00 TTL=105 ID=16064 PROTO=UDP SPT=61054 DPT=6881 LEN=112 
[29021.761500] Inbound IN=wlan0 OUT= MAC=00:1d:d9:76:eb:59:00:1c:df:3e:7d:65:08:00 SRC=200.201.5.10 DST=192.168.2.4 LEN=131 TOS=0x00 PREC=0x00 TTL=111 ID=62294 PROTO=UDP SPT=38918 DPT=6881 LEN=111 
clevefan@laptop:~$

---

### Post by clevefan on 2009-05-05
Okay, after i connect the camera and in its menu select connect to device. the I run the command you gave me. it brings up f-spot and allows me to download my photos. but I'm not able to get my videos.

---

### Post by mjitkop on 2009-06-17
clevefan, if you are still monitoring this thread, I would suggest that you not open F-Spot but instead click on Places in the Ubuntu menu and you should have an entry called EVERIO_HDD. Click that entry and you should see the content of your camcorder hardrive. 

On my Everio hard drive, I have 4 directories: DCIM, EXTMOV, PRIVATE and SD_VIDEO.

The pictures that I took with the camcorder are located in DCIM.

The videos that I recorded are in SD_VIDEO and they have the .MOD extension. There are sub-directories in SD_VIDEO so you just have to browse and see what you have in there. 

You can simply copy the files of interest to your computer hard drive.

The .MOD files seem to be normal MPEG2 video files and Ubuntu's movie player has no problems playing them. I will try to use DVD Styler to make DVDs with the .MOD files directly. I have no idea if that is going to work.

I hope this helps.

---

