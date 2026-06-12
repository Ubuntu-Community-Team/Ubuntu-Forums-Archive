---
title: "strange usb problem, usb-storage never initializes!"
date: 2006-09-10
forum: Desktop Environments
---

### Post by soulglo83 on 2006-09-10
when plugging in a cybershot camera in ubuntu, no /dev/sd* entry is created.  it is however recognized by lsusb and dmesg.  I'm using kernel 2.6.15-26-386 w/ fglrx (obviously given the dmesg output). Here's the lsusb output:

Bus 005 Device 004: ID 054c:0010 Sony Corp. DSC-S30/S70/S75/F505V/F505/FD92 Cybershot/Mavica Digital Camera
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 04e8:326c Samsung Electronics Co., Ltd 
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  

and the tail of the dmesg output:

[17179717.324000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17179717.324000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xe53ce680 for 983040 bytes
[17179732.624000] usb 5-3: USB disconnect, address 3
[17179736.644000] usb 5-3: new high speed USB device using ehci_hcd and address 4
[17179736.776000] usb 5-3: configuration #1 chosen from 2 choices

Other USB devices work fine, like my samsung ml-2010 laser printer and laser mouse.  Even after having modprobe'd usb-storage, it does not change my dmesg output.
I think its weird that it just craps out, at that last line, thats literally all the further it goes.  Has anyone encountered this?  More specifically How do i go about fixing it?  Thanks to all those that reply!

---

### Post by lukew on 2006-09-11
I would try mounting it by hand.

Luke

---

### Post by soulglo83 on 2006-09-11
thanks for the reply, but, in order to mount anything, there needs to be a /dev entry created after hotplugging.  if no such entry exists, im missing part of the command necessary to mount the device.

---

### Post by soulglo83 on 2006-09-12
I'm no fan of bumping, but this is a very important matter to me.  I have been using linux for about 2 years, and have not had to reinstall linux for a year and a half, after successfully dist-upgrading 3 monumental times.  Linux is my home, thats where I've learned to do everything I do now.  This USB issue, continually lands me in windows land, so I can access my camera's photos from my camera, and paper's from my flash drive.  I love Ubuntu, it's the greatest software in the world, but without USB its worthless to me.  Is there really no way around a format and reinstall?

---

### Post by lukew on 2006-09-12
Hi,

You are supose to get something like this in your dmesg which instructs you where it is mapped to.

Can you find anything? Looks like from the tail of dmesg there was nothing. Look like it is not properly connected.

[17180944.500000] sdb: assuming drive cache: write through
[17180944.500000]  sdb: sdb1

If you dont see this it has not connected properly.

Looking at your errors it looks like there is a problem with your graphics card. Did you do dmesg | tail straight after the usb device was connected?

BTW: I saw someone elses mount comman for mounting a usb device and it was not /dev/sd* - mine always goes in there though. 

Post your findings so we can continue to help.

Luke

---

### Post by soulglo83 on 2006-09-12
Thank you for your reply lukew!  I hadn't noticed how poorly worded my previous explanation about my dmesg output was.  Below is the last five lines of my dmesg output.  The two lines about fglrx i have googled, and apparently they arent causing people much trouble.  Thats what the initial 100-600 messages in my dmesg output is is repeats of those two lines and errors similar to it.  The only real pertinent information are the last 3 lines, where the ehci_hcd module assigns an address to the device, but usb-storage and scsi emulation never initialize, and so the device is never assigned a /dev/ entry.  My computer halts the hotplug script right after assigning the address!.

[17186667.256000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17186667.256000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xd68aee40 for 5242880 bytes
[17186695.148000] usb 5-3: USB disconnect, address 3
[17186697.404000] usb 5-3: new high speed USB device using ehci_hcd and address 4
[17186697.536000] usb 5-3: configuration #1 chosen from 2 choices
sandwich@ubuntu:~$

---

### Post by soulglo83 on 2006-09-13
ok thank god.  fixed, finally.  i decided dist-upgrading might iron this out, and sure enough i'm kickin it inside a very beautiful successor to dapper drake.  personally, im kinda glad i had this headache now, edgy f'in rox!

---

