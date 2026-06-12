---
title: "Archos GMini XS100"
date: 2005-09-22
forum: Desktop Environments
---

### Post by theFallen on 2005-09-22
Hi,

I have an Archos GMini XS100 mp3 player. It won't auto mount and I ran out of ideas. Okay, I have to say, I'm quit new to Linux. But I did my researches. The hotplug system works fine with my usb-camera. The mp3 player worked in the biginning. I did a Firware update (and I can't remeber if it worked afterwards, becaus I did my uploading and got my vacation :) ). The damn thing is working under windows.
So what else do you need from me to give me some advice?

---

### Post by Keffin on 2005-09-22
Plug the mp3 player in, turn it on, wait a few seconds, then run "sudo tail /var/log/messages" in a terminal.

> Sep 22 21:57:53 localhost kernel: usbcore: registered new driver usb-storage
Sep 22 21:57:53 localhost kernel: USB Mass Storage support registered.
Sep 22 21:57:53 localhost usb.agent[12342]:      usb-storage: loaded successfully
Sep 22 21:57:58 localhost kernel:   Vendor: USB-HS    Model: HTC426020G7CE00   Rev: 0.01
Sep 22 21:57:58 localhost kernel:   Type:   Direct-Access                      ANSI SCSI revision: 00
Sep 22 21:57:58 localhost kernel: SCSI device sdb: 39070080 512-byte hdwr sectors (20004 MB)
Sep 22 21:57:58 localhost kernel: SCSI device sdb: 39070080 512-byte hdwr sectors (20004 MB)
Sep 22 21:57:59 localhost kernel:  /dev/scsi/host4/bus0/target0/lun0: p1
Sep 22 21:57:59 localhost kernel: Attached scsi disk sdb at scsi4, channel 0, id 0, lun 0
Sep 22 21:57:59 localhost scsi.agent[12437]:      sd_mod: loaded sucessfully

This is the output from me doing the same, with a fully working automounting Gmini 200.

Also have you looked to see if it is actually mounting but just not popping up a file manager for you to notice? Run "ls /media" before and after plugging in the player.

Hopefully that will at least narrow it down.

---

### Post by theFallen on 2005-09-23
Hi,

dmesg and messages contains only inbound traffic. how can I change what the shall log?

The output is like this

> Inbound IN=eth0 OUT= MAC=00:20:ed:71:44:d2:00:50:18:1b:a0:ae:08:00 SRC=72.25.107.140 DST=192.168.123.179 LEN=235 TOS=0x00 PREC=0x00 TTL=106 ID=60781 PROTO=UDP SPT=6881 DPT=6881 LEN=215
Inbound IN=eth0 OUT= MAC=00:20:ed:71:44:d2:00:50:18:1b:a0:ae:08:00 SRC=71.113.250.169 DST=192.168.123.179 LEN=231 TOS=0x00 PREC=0x00 TTL=111 ID=11556 PROTO=UDP SPT=6881 DPT=6881 LEN=211 

I couldn't find your kind of output. Furthermore when I use the command "lsusb" only my mouse and my printer show up.

---

### Post by Keffin on 2005-09-23
Do you definitely only get those lines in /var/log/messages? Fire it up in an editor to see the whole file, I get that stuff drowning out other messages too.

Is it possible to downgrade the firmware version to what you had to see if that suddenly makes it work again?

---

### Post by theFallen on 2005-09-27
Hi, 

I looked it up and you're right there where those lines hidden beneath all those other outputs.
But I have to say there is no change when I plug in xs100, I can tell the difference by pluggin in my camera, then I have following lines:

> Sep 27 11:59:04 localhost kernel: [4295205.798000] usb 1-2: new full speed USB device using uhci_hcd and address 4
Sep 27 11:59:04 localhost kernel: [4295206.058000] SCSI subsystem initialized
Sep 27 11:59:04 localhost kernel: [4295206.071000] Initializing USB Mass Storage driver...
Sep 27 11:59:04 localhost kernel: [4295206.080000] scsi0 : SCSI emulation for USB Mass Storage devices
Sep 27 11:59:04 localhost kernel: [4295206.082000] usbcore: registered new driver usb-storage
Sep 27 11:59:04 localhost kernel: [4295206.082000] USB Mass Storage support registered.
Sep 27 11:59:04 localhost usb.agent[10008]:      usb-storage: loaded successfully
Sep 27 11:59:09 localhost kernel: [4295211.085000]   Vendor: Digital   Model: Camera            Rev: 1.00
Sep 27 11:59:09 localhost kernel: [4295211.085000]   Type:   Direct-Access                      ANSI SCSI revision: 00
Sep 27 11:59:10 localhost kernel: [4295211.365000] SCSI device sda: 498176 512-byte hdwr sectors (255 MB)
Sep 27 11:59:10 localhost kernel: [4295211.370000] sda: Write Protect is off
Sep 27 11:59:10 localhost kernel: [4295211.382000] SCSI device sda: 498176 512-byte hdwr sectors (255 MB)
Sep 27 11:59:10 localhost kernel: [4295211.385000] sda: Write Protect is off
Sep 27 11:59:10 localhost kernel: [4295211.385000]  /dev/scsi/host0/bus0/target0/lun0: p1
Sep 27 11:59:10 localhost scsi.agent[10091]:      sd_mod: loaded sucessfully (for disk)
Sep 27 11:59:10 localhost kernel: [4295211.399000] Attached scsi removable disk sda at scsi0, channel 0, id 0, lun 0

I'm waiting now for the archos support to send me the old firware, so I can try it.

---

### Post by rwabel on 2005-12-22
I've an archos video av340. I can remeber that it once worked. but it was still on hoary I guess. now i'm on dapper. it doens't get mounted, but my rio carbon does just fine!
here is the log:
> Dec 22 11:12:39 localhost kernel: [4336947.165000] scsi0 : SCSI emulation for USB Mass Storage devices
Dec 22 11:12:39 localhost kernel: [4336947.165000] usbcore: registered new driver usb-storage
Dec 22 11:12:39 localhost kernel: [4336947.165000] USB Mass Storage support registered.
Dec 22 11:12:40 localhost kernel: [4336948.158000] usb 4-1: USB disconnect, address 6
Dec 22 11:15:54 localhost kernel: [4337141.864000] usb 4-1: new high speed USB device using ehci_hcd and address 7
Dec 22 11:15:54 localhost kernel: [4337141.981000] scsi1 : SCSI emulation for USB Mass Storage devices
Dec 22 11:15:54 localhost kernel: [4337142.408000] usb 4-1: USB disconnect, address 7
Dec 22 11:15:55 localhost kernel: [4337143.364000] usb 4-1: new high speed USB device using ehci_hcd and address 8
Dec 22 11:15:56 localhost kernel: [4337143.482000] scsi2 : SCSI emulation for USB Mass Storage devices
Dec 22 11:15:59 localhost kernel: [4337146.908000] usb 4-1: USB disconnect, address 8


---

### Post by theFallen on 2005-12-22
Well, I still got no message from Archos..... :mad: 
But I got a hand on some USB Cables and one of them was better shielded (at least it is the thickest of all) and it did work after that without complaints. It seems there are even differences between USB 2.0 Cables, although there should none. Why is there a standard?????

Now at least for me the problem is solved. 

Ah, one other hint, which made me get those calbes, was the dmesg output. It showed read/write errors and after searching with google, I found some posts wich stated that it could mean there is not sufficent power for the device due to interference.

---

### Post by rwabel on 2005-12-22
[quote=theFallen]Well, I still got no message from Archos..... :mad: 
But I got a hand on some USB Cables and one of them was better shielded (at least it is the thickest of all) and it did work after that without complaints. It seems there are even differences between USB 2.0 Cables, although there should none. Why is there a standard?????

Now at least for me the problem is solved. 

Ah, one other hint, which made me get those calbes, was the dmesg output. It showed read/write errors and after searching with google, I found some posts wich stated that it could mean there is not sufficent power for the device due to interference.[/quote]

thanks for the hint, I'll try with other cables

---

