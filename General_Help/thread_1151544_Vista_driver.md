---
title: "Vista driver"
date: 2009-05-07
forum: General Help
---

### Post by sakiusa on 2009-05-07
I have a USB-SERIAL driver from WINCHIPHEAD and its for Windows 98/XP/2000 ONLY.Can someone advice on which driver to use on my Vista Basic OS.
 
pLS HELP!!!its urgent

---

### Post by shazbut on 2009-05-07
Open a terminal and enter:
```
tail -f /var/log/messages
```
Now plug in the serial port adapter and take note of the messages that appear.  Somewhere in there it should tell you the model, for example, mine gives: kernel: [312494.071750] pl2303: Prolific PL2303 USB to serial adaptor driver

Then google the manufacturer and model and see if they have a vista driver available.

---

### Post by sakiusa on 2009-05-07
> **sakiusa said:**
> I have a USB-SERIAL driver from WINCHIPHEAD and its for Windows 98/XP/2000 ONLY.Can someone advice on which driver to use on my Vista Basic OS.
 
pLS HELP!!!its urgent
i have typed this command on my Command Prompt
**C:\Users\NEC>**[COLOR=red]tail -f/var/log/messages[/COLOR]  ...nothing happens as a message comes up
''tail' is not recognised as an internal or external command,operable program or batch file on my Command Prompt Window..

---

### Post by sakiusa on 2009-05-07
> **sakiusa said:**
> i have typed this command on my Command Prompt
**C:\Users\NEC>**[COLOR=red]tail -f/var/log/messages[/COLOR]  ...nothing happens as a message comes up
''tail' is not recognised as an internal or external command,operable program or batch file on my Command Prompt Window..
This is the setup iNFORMATION that comes with the adaptor.
 
; USBSER34.INF
; Driver for (USB=>SERIAL chip) V2.1
; WDM&VXD for Windows 98/ME/2000/XP
; Copyright (C) W.ch 2001-2005
;
[Version]
Signature = "$Chicago$"
Class     = Ports
ClassGuid = {4D36E978-E325-11CE-BFC1-08002BE10318}
Provider  = %WinChipHead%
DriverVer = 12/26/2005, 2.1.2005.12
[ControlFlags]
ExcludeFromSelect = USB\VID_4348&PID_5523
ExcludeFromSelect = USB\VID_4348&PID_5521
ExcludeFromSelect = USBSERPORT\SER5523
ExcludeFromSelect = USBSERPORT\SER5521
[Manufacturer]
%WinChipHead% = WinChipHead
[WinChipHead]
%USBSER34.DeviceDesc% = USBSER34_Install, USB\VID_4348&PID_5523
%USBIRDA34.DeviceDesc% = USBSER34_Install, USB\VID_4348&PID_5521
%USBSER98.DeviceDesc% = USBSER98_Install, USBSERPORT\SER5523
%USBIRDA98.DeviceDesc% = USBSER98_Install, USBSERPORT\SER5521
[USBSER34_Install]
CopyFiles = USBSER34.CopyFiles.SYS
AddReg    = USBSER34.9X.AddReg
[USBSER34_Install.NT]
CopyFiles = USBSER34.NT.CopyFiles.SYS
AddReg    = USBSER34.NT.AddReg
[USBSER34_Install.NT.HW]
AddReg    = USBSER34.NT.HW.AddReg
[USBSER98_Install]
CopyFiles = USBSER98.CopyFiles.VXD, USBSER34.CopyFiles.SYS
AddReg    = USBSER98.9X.AddReg
[USBSER98_Install.NT]
[USBSER34.CopyFiles.SYS]
USBSER98.SYS, , , 2
[USBSER34.NT.CopyFiles.SYS]
USBSER34.SYS, , , 2
[USBSER98.CopyFiles.VXD]
USBSER34.VXD, , , 2
[USBSER34.9X.AddReg]
HKR, , DevLoader, , *NTKERN
HKR, , NTMPDriver, , USBSER98.SYS
[USBSER34.NT.AddReg]
HKR,,EnumPropPages32,,"MsPorts.dll,SerialPortPropPageProvider"
[USBSER34.NT.HW.AddReg]
;HKR,,"UpperFilters",0x00010000,"serenum"
[USBSER98.9X.AddReg]
HKR, , DevLoader, , *vcomm
HKR, , PortDriver, , USBSER34.VXD
HKR, , Contention, , *vcd
HKR, , ConfigDialog, , serialui.dll
HKR, , DCB, 3, 1C,00,00,00, 80,25,00,00, 11,00,00,00, 00,00,0A,00, 0A,00,08,00, 00,11,13,00, 00,00,00,00
HKR, , PortSubClass, 1, 01
HKR, , EnumPropPages, , "serialui.dll,EnumPropPages"
;HKR, , Enumerator, , serenum.vxd
[USBSER34_Install.NT.Services]
AddService = USBSER34, 2, USBSER34.Service
[USBSER34.Service]
DisplayName   = "USBSER34"
ServiceType   = 1
StartType     = 3
ErrorControl  = 1
ServiceBinary = %10%\System32\Drivers\USBSER34.SYS
[DestinationDirs]
DefaultDestDir      = 10, System32\Drivers
USBSER34.CopyFiles.SYS = 10, System32\Drivers
USBSER34.NT.CopyFiles.SYS = 10, System32\Drivers
USBSER98.CopyFiles.VXD = 11
[SourceDisksFiles]
USBSER34.SYS  = 1
USBSER98.SYS  = 1
USBSER34.VXD  = 1
[SourceDisksNames]
1 = "USB Serial Installation Disk", USBSER34.INF, ,
[Strings]
WinChipHead      = ""
USBSER34.DeviceDesc = "USB-SERIAL"
USBIRDA34.DeviceDesc = "USB-IRDA"
USBSER98.DeviceDesc = "USB-SERIAL"
USBIRDA98.DeviceDesc = "USB-IRDA"

---

### Post by bapoumba on 2009-05-07
I have added the [other_os] tag to your thread. Are you aware these are Ubuntu Linux forums?

---

