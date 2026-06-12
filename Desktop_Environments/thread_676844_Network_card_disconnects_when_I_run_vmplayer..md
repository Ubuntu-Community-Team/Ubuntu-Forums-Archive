---
title: "Network card disconnects when I run vmplayer."
date: 2008-01-24
forum: Desktop Environments
---

### Post by tirithen on 2008-01-24
I'm running gutsy and using wicd as network manager due to problems with the built-in manager and my wireless connection. I now also have an windows server installation that I run as a virtual machine with vmware player. The problem is that when I run windows my network connection disappears in ubuntu and it stays gone even if I shut vmplayer down I cannot connect, not until I restart my computer. My wireless network card is on /dev/etc1.

Is there a way of getting the network up and running in ubuntu and windows at the same time?

There are my .vmx-file:
> 
#!/usr/bin/vmware
config.version = "8"
virtualHW.version = "3"
ide0:0.present = "TRUE"
ide0:0.filename = "Windows Server 2003.vmdk"
memsize = "384"
MemAllowAutoScaleDown = "FALSE"
mainMem.useNamedFile="FALSE"

ide1:0.present = "TRUE"
ide1:0.fileName = "auto detect"
ide1:0.deviceType = "cdrom-raw"
ide1:0.autodetect = "TRUE"
floppy0.present = "FALSE"
ethernet0.present = "TRUE"
usb.present = "TRUE"
sound.present = "TRUE"
sound.virtualDev = "es1371"
displayName = "Windows Server 2003"
guestOS = "winNetStandard"
nvram = "Windows Server 2003.nvram"
MemTrimRate = "-1"

ide0:0.redo = ""
ethernet0.addressType = "generated"
uuid.location = "56 4d d6 34 f3 2d 02 06-28 91 e6 6e cb 56 69 83"
uuid.bios = "56 4d d6 34 f3 2d 02 06-28 91 e6 6e cb 56 69 83"
ethernet0.generatedAddress = "00:0c:29:56:69:83"
ethernet0.generatedAddressOffset = "0"

tools.syncTime = "TRUE"
ide1:0.startConnected = "TRUE"

uuid.action = "create"

checkpoint.vmState = "Windows Server 2003.vmss"

extendedConfigFile = "Windows Server 2003.vmxf"
virtualHW.productCompatibility = "hosted"
tools.upgrade.policy = "manual"

isolation.tools.hgfs.disable = "TRUE"
tools.remindInstall = "FALSE"

usb.autoConnect.device0 = ""
I also cannot find a driver for the soundcard, it shows as a device with no driver in vmware, I have wmtools installed in windows, should not that include all drivers? In Ubuntu the sound works fine.

---

