---
title: "&quot;Stop error&quot; running Windows image from Qemu in VMware Player"
date: 2005-12-27
forum: General Help
---

### Post by Azrael on 2005-12-27
I want to switch from using Qemu to using VMware Player instead. I have a 2GB hd.vmdk file which contains the Windows 2000 installation I installed and used with Qemu. I created the following hd.vmx config file:
```
config.version = "8"
virtualHW.version = "3"

MemAllowAutoScaleDown = "FALSE"
MemTrimRate = "-1"

uuid.location = "56 4d 5c cc 3d 4a 43 29-55 89 5c 28 1e 7e 06 58"
uuid.bios = "56 4d 5c cc 3d 4a 43 29-55 89 5c 28 1e 7e 06 58"

uuid.action = "create"
checkpoint.vmState = ""

displayName = "Win2000Pro"
guestOS = "win2000Pro"
memsize = "256"

ethernet0.present = "TRUE"
ethernet0.connectionType = "nat"
ethernet0.addressType = "generated"
ethernet0.generatedAddress = "00:0c:29:7e:06:58"
ethernet0.generatedAddressOffset = "0"

usb.present = "TRUE"
usb.generic.autoconnect = "TRUE"

sound.present = "FALSE"

scsi0.present = "FALSE"

floppy0.present = "FALSE"

ide0:0.present = "TRUE"
ide0:0.fileName = "/home/ark/hd.vmdk"
ide0:0.deviceType = "disk"
ide0:0.mode = ""
ide0:0.redo = ""
ide0:0.startConnected = "TRUE"
ide0:0.autodetect = "TRUE"

ide0:1.present = "FALSE"

ide1:0.present = "FALSE"

ide1:1.present = "FALSE"
``` 
When I start VMware Player everything seems normal until the Windows 2000 initialization screen jumps to a BSOD delivering the following statement:

STOP:           0x0000007B (0xF741B84C,0xC0000034,0x00000000,0x00000000)
           INACCESSIBLE_BOOT_DEVICE

Anyone know what's going wrong here? I'd also like to know if anyone else has succesfully switched from Qemu to VMware player while keeping the same old disk image. Save me from ignorance.

---

