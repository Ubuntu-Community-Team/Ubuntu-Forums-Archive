---
title: "Setting up an 802.11g PCI card"
date: 2005-12-07
forum: Desktop Environments
---

### Post by pr0fess0r on 2005-12-07
Hi again
I have a Dick Smith (New Zealand) XH8196 802.11g PCI card, which I installed in Ubuntu and it shows up as an Intersil ISL3890 [Prism GT/Prism] PCI card. It also shows up as eth1 rather than wlan0
Dick Smith offer untested beta drivers but I dont know how to install them, can anyone help? The file structure is:
2.8.0.0 UMAC      singlesource_linux_ddk_sources_0.6.0.0

./2.8.0.0 UMAC:
3886lmac_2.7.0.0.arm                  umac_arm_le_sdt_aof_2.8.0.0.lib
smoid2.h                              umac_i386_le_gcc_elf_2.8.0.0.lib
softmac2.h                            umac_mips_be_gcc_elf_2.8.0.0.lib
umac_arm9e_le_ads_elf_2.8.0.0.lib     umac_mips_le_gcc_elf_2.8.0.0.lib
umac_arm9e_le_gcc_elf_2.8.0.0.lib     umac_powerpc_be_gcc_elf_2.8.0.0.lib
umac_arm_le_ads_elf_2.8.0.0.lib       umac_sh_be_gcc_elf_2.8.0.0.lib
umac_arm_le_gcc_elf_2.8.0.0.lib       umac_xscale_be_gcc_elf_2.8.0.0.lib
umac_arm_le_isos_gcc_elf_2.8.0.0.lib  umac_xscale_le_gcc_elf_2.8.0.0.lib
umac_arm_le_rvct_elf_2.8.0.0.lib

./singlesource_linux_ddk_sources_0.6.0.0:
./singlesource_linux_ddk_sources_0.6.0.0/External:
./singlesource_linux_ddk_sources_0.6.0.0/External/OpenSource:
./singlesource_linux_ddk_sources_0.6.0.0/External/OpenSource/pcmcia-cs:
./singlesource_linux_ddk_sources_0.6.0.0/External/OpenSource/pcmcia-cs/cardmgr:
./singlesource_linux_ddk_sources_0.6.0.0/External/OpenSource/pcmcia-cs/clients:
./singlesource_linux_ddk_sources_0.6.0.0/External/OpenSource/pcmcia-cs/debug-tools:
./singlesource_linux_ddk_sources_0.6.0.0/External/OpenSource/pcmcia-cs/doc:
./singlesource_linux_ddk_sources_0.6.0.0/External/OpenSource/pcmcia-cs/etc:
./singlesource_linux_ddk_sources_0.6.0.0/External/OpenSource/pcmcia-cs/etc/cis:
./singlesource_linux_ddk_sources_0.6.0.0/External/OpenSource/pcmcia-cs/flash:
./singlesource_linux_ddk_sources_0.6.0.0/External/OpenSource/pcmcia-cs/include:
./singlesource_linux_ddk_sources_0.6.0.0/External/OpenSource/pcmcia-cs/include/asm:
./singlesource_linux_ddk_sources_0.6.0.0/External/OpenSource/pcmcia-cs/include/linux:
./singlesource_linux_ddk_sources_0.6.0.0/External/OpenSource/pcmcia-cs/include/net:
./singlesource_linux_ddk_sources_0.6.0.0/External/OpenSource/pcmcia-cs/include/pcmcia:
./singlesource_linux_ddk_sources_0.6.0.0/External/OpenSource/pcmcia-cs/include/static:
./singlesource_linux_ddk_sources_0.6.0.0/External/OpenSource/pcmcia-cs/include/static/pcmcia:
./singlesource_linux_ddk_sources_0.6.0.0/External/OpenSource/pcmcia-cs/man:
./singlesource_linux_ddk_sources_0.6.0.0/External/OpenSource/pcmcia-cs/modules:
./singlesource_linux_ddk_sources_0.6.0.0/External/OpenSource/pcmcia-cs/wireless:
./singlesource_linux_ddk_sources_0.6.0.0/Software:
./singlesource_linux_ddk_sources_0.6.0.0/Software/Applications:
./singlesource_linux_ddk_sources_0.6.0.0/Software/Applications/getoid:
./singlesource_linux_ddk_sources_0.6.0.0/Software/Applications/getoid/main:
./singlesource_linux_ddk_sources_0.6.0.0/Software/Applications/lmterm:
./singlesource_linux_ddk_sources_0.6.0.0/Software/Applications/lmterm/main:
./singlesource_linux_ddk_sources_0.6.0.0/Software/Applications/paed:
./singlesource_linux_ddk_sources_0.6.0.0/Software/Applications/paed/main:
./singlesource_linux_ddk_sources_0.6.0.0/Software/Applications/setoid:
./singlesource_linux_ddk_sources_0.6.0.0/Software/Applications/setoid/main:
./singlesource_linux_ddk_sources_0.6.0.0/Software/Applications/smconf:
./singlesource_linux_ddk_sources_0.6.0.0/Software/Applications/smconf/main:
./singlesource_linux_ddk_sources_0.6.0.0/Software/Drivers:
./singlesource_linux_ddk_sources_0.6.0.0/Software/Drivers/SingleSourceLinuxDriver:
./singlesource_linux_ddk_sources_0.6.0.0/Software/Drivers/SingleSourceLinuxDriver/main:
./singlesource_linux_ddk_sources_0.6.0.0/Software/Lib:
./singlesource_linux_ddk_sources_0.6.0.0/Software/Lib/prismioctl:
./singlesource_linux_ddk_sources_0.6.0.0/Software/Lib/prismioctl/main:
./singlesource_linux_ddk_sources_0.6.0.0/Software/Lib/prismoids:
./singlesource_linux_ddk_sources_0.6.0.0/Software/Lib/prismoids/main:

I tried using wpa_supplicant but got this:

 wpa_supplicant -ieth1 -c/etc/wpa_supplicant.conf -Dprism54
ioctl[SIOCSIWPMKSA]: Operation not permitted
ioctl[SIOCSIWMODE]: Operation not permitted
Could not configure driver to use managed mode
SIOCSIFFLAGS: Permission denied
Could not set interface 'eth1' UP
socket(PF_PACKET): Operation not permitted
ioctl[PRISM54_HOSTAPD]: Operation not permitted
ioctl[PRISM54_HOSTAPD]: Operation not permitted
wpa_driver_prism54_set_countermeasures - not yet implemented
ioctl[SIOCSIWAP]: Operation not permitted
SIOCSIFFLAGS: Permission denied

so i'm a bit stuck as to where to go next... any links or tips appreciated
cheers
Lucas

---

### Post by pr0fess0r on 2005-12-07
I'm going to try the ndiswrapper, I downloaded the Windows drivers for the card and the inf file thinks it's a Prism too:

;***********************************************************************

; O4I01.INF

;

;   This installation script supports Windows 98, Me, 2000 and XP for the

;   OEM 54Mbps 2.4GHz Wireless Adapter.

;

;   Copyright (c) 2003 OEM Corporation.

;   All Rights Reserved.

;   

;***********************************************************************



[Version]

 DriverVer = 12/3/2003, 2.1.10.0

 Signature           = "$Chicago$"

 Compatible          = 1

 Class               = Net

 ClassGUID           = {4d36e972-e325-11ce-bfc1-08002be10318}

 Provider            = %VER_VENDOR_STR%

 CatalogFile         = O4I01A.cat

 ;MillenniumPreferred = .ME



[ControlFlags]

;Exclude all PNP adapters from user selection

 ExcludeFromSelect   = *



[Manufacturer]

 %VER_VENDOR_NAME_STR% = DeviceList,NTx86.5.1



[DeviceList.NTx86.5.1]

 %DCB1_DESC_STR%     = PRISM_DCB1_XP,        PCI\VEN_1260&DEV_3890&SUBSYS_42021113



[DeviceList]

 %DCB1_DESC_STR%     = PRISM_DCB1,        PCI\VEN_1260&DEV_3890&SUBSYS_42021113



;==========================================

[PRISM_DCB1]       ; Win9x

 DelReg         = COMMON_AMAC_DEL.reg

 AddReg         = PRISM_DCB1.reg, PRISM_DCB1.reg1, COMMON_ICB.reg, COMMON_NDIS.reg, COMMON.reg, COMMON_PSMODE.reg, COMMON_AMAC.reg

 CopyFiles      = PRISM_DRIVER.copy, PRISM_FWDCB.copy, PRISM_CCU.copy



[PRISM_DCB1.NT]    ; Win2k

 DelReg         = COMMON_AMAC_DEL.reg

 AddReg         = PRISM_DCB1.reg, COMMON_ICB.reg, COMMON_NDIS.reg.NT, COMMON.reg, COMMON_PS_MODE_XP.reg, COMMON_AMAC.reg

 CopyFiles      = PRISM_DRIVER.copy.NT, PRISM_FWDCB.copy.NT, PRISM_CCU.copy

 BusType        = 5     ; PCI

 Characteristics= 0x84  ; NCF_PHYSICAL | NCF_HAS_UI

 

[PRISM_DCB1.NT.Services]

 AddService     = "O4I01A", 2, PRISM_DRIVER_DCB1.Service, PRISM_DRIVER.EventLog



[PRISM_DCB1.NT.CoInstallers]

 CopyFiles      = PRISM_COINSTALL.copy.NT

 AddReg         = PRISM_COINSTALL.reg.NT



[PRISM_DCB1_XP]    ; Winxp

 DelReg         = COMMON_AMAC_DEL.reg

 AddReg         = PRISM_DCB1.reg, COMMON_ICB.reg, COMMON_NDIS.reg.NT, COMMON.reg, COMMON_PS_MODE_XP.reg, COMMON_AMAC.reg

 CopyFiles      = PRISM_DRIVER.copy.XP, PRISM_FWDCB.copy.NT, PRISM_CCU.copy

 BusType        = 5     ; PCI

 Characteristics= 0x84  ; NCF_PHYSICAL | NCF_HAS_UI

 

[PRISM_DCB1_XP.Services]

 AddService     = "O4I01A", 2, PRISM_DRIVER_DCB1.Service, PRISM_DRIVER.EventLog



[PRISM_DCB1_XP.CoInstallers]

 CopyFiles      = PRISM_COINSTALL.copy.NT

 AddReg         = PRISM_COINSTALL.reg.NT 



[PRISM_DCB1.reg1]

; HKLM,SOFTWARE\Microsoft\Windows\CurrentVersion\RunOnce, "O4I01A",, "%11%\O4I01DCS.exe"



[PRISM_DCB1.reg]

 HKR,Ndi,DeviceID,0,"PCI\VEN_&DEV_&SUBSYS__PRISM_PCI_SUBSYSID_"

; 0x3890 = 14480

 HKR,,PlatformID,0,14480

 HKR,,VendorDesc,0,%DCB1_DESC_STR%

 HKR,,11dMode,0,0

 HKR,,EnableRadio,0,1

 HKR,,CountryCode,0,0

 HKR,,CountryName,0,72

 HKR,,DomainCode,1,00,55,53,20



;###############################################################################

[PRISM_COINSTALL.reg.NT]

; HKR,           ,CoInstallers32         ,0x00010000     ,"O4I01DCS.dll,CoDCSUup"



[PRISM_DRIVER_DCB1.Service]

 DisplayName    = %PRISM_SERVICE_DISPLAY_DCB%

 ServiceType    = 1    ; SERVICE_KERNEL_DRIVER

 StartType      = 3    ; SERVICE_DEMAND_START

 ErrorControl   = 1    ; NORMAL

 ServiceBinary  = %12%\O4I01A.sys

 LoadOrderGroup = NDIS

 

[PRISM_DRIVER.EventLog]

 AddReg         = PRISM_DRIVER.EventLog.reg



[PRISM_DRIVER.EventLog.reg]

 HKR,           ,EventMessageFile       ,0x00020000     ,"%%SystemRoot%%\System32\netevent.dll"

 HKR,           ,TypesSupported         ,0x00010001     ,7



;###############################################################################

;RegKey,SubKey          ,Name                   ,Type   ,Value

;-------------          -----                   -----   ------

[COMMON_ICB.reg]

 HKR,NDI                ,Service                ,0      ,"O4I01A"

 HKR,                   ,BusType                ,0      ,"5"

 HKR,                   ,DeviceVxDs             ,0      ,"O4I01A.sys"

 HKR,                   ,CardBusBridgeLatencyTimer  ,0  ,"32"

 HKR,                   ,CardBusBridgeCacheLineSize ,0  ,"8"

; HKR,                   ,EnableIRQSharing       ,1      ,01,00,00,00

; HKR,                   ,IOBaseAddress          ,1      ,02,00,00,00

; HKR,                   ,InterruptNumber        ,1      ,04,00,00,00



[COMMON_NDIS.reg]

 HKR,                   ,RunningWin9X           ,0      ,"0"

 HKR,                   ,DevLoader              ,0      ,"*ndis"

 HKR,                   ,EnumPropPages          ,0      ,"netdi.dll,EnumPropPages"

 HKR,NDI\Interfaces     ,UpperRange             ,0      ,"ndis3"

 HKR,NDI\Interfaces     ,LowerRange             ,0      ,"ethernet"

 HKR,NDI\Interfaces     ,DefUpper               ,0      ,"ndis3"

 HKR,NDI\Interfaces     ,DefLower               ,0      ,"ethernet"

 HKR,NDIS               ,LogDriverName          ,0      ,"O4I01A"

 HKR,NDIS               ,MajorNdisVersion       ,1      ,03

 HKR,NDIS               ,MinorNdisVersion       ,1      ,0a



[COMMON_NDIS.reg.NT]

 HKR,NDI\Interfaces     ,UpperRange             ,0      ,"ndis5"

 HKR,NDI\Interfaces     ,LowerRange             ,0      ,"ethernet"



[COMMON.reg]

 HKR,                   ,PRISMIOC               ,0      ,"0"

 HKR,                   ,SilentInstall          ,0      ,"1"

;Uncomment the line above to install without user interface prompts



 HKR,NDI\params\RTSThresh,,0,2347

 HKR,Ndi\params\RTSThresh,default,0,2347

 HKR,NDI\params\RTSThresh,ParamDesc,0,%RTSTHRESH_STR%

 HKR,NDI\params\RTSThresh,type,0,int

 HKR,NDI\params\RTSThresh,flag,1,20,00,00,00

 HKR,NDI\params\RTSThresh,min,0,0

 HKR,NDI\params\RTSThresh,max,0,2347

 HKR,NDI\params\RTSThresh,step,0,1

 HKR,NDI\params\RTSThresh,optional,0,1



 HKR,NDI\params\FragThresh,,0,2346

 HKR,Ndi\params\FragThresh,default,0,2346

 HKR,NDI\params\FragThresh,ParamDesc,0,%FRAGTHRESH_STR%

 HKR,NDI\params\FragThresh,type,0,int

 HKR,NDI\params\FragThresh,flag,1,20,00,00,00

 HKR,NDI\params\FragThresh,min,0,256

 HKR,NDI\params\FragThresh,max,0,2346

 HKR,NDI\params\FragThresh,step,0,2

 HKR,NDI\params\FragThresh,optional,0,1



[COMMON_AMAC_DEL.reg]

 HKR,defaults,DataRates

 HKR,NDI\params\DataRates

 HKR,NDI\params\DataRate

 HKR,DSChannel

 HKR,defaults,DSChannel

 HKR,NDI\params\DSChannel



[COMMON_AMAC.reg]

 HKR,NDI\params\ShortRetryLimit,,0,7

 HKR,NDI\params\ShortRetryLimit,default,0,7

 HKR,NDI\params\ShortRetryLimit,ParamDesc,,%SHORT_RETRY_STR%

 HKR,NDI\params\ShortRetryLimit,type,,int

 HKR,NDI\params\ShortRetryLimit,min,0,1

 HKR,NDI\params\ShortRetryLimit,max,0,255

 HKR,NDI\params\ShortRetryLimit,step,0,1

 HKR,NDI\params\ShortRetryLimit,optional,0,1



 HKR,NDI\params\LongRetryLimit,,0,4

 HKR,NDI\params\LongRetryLimit,default,0,4

 HKR,NDI\params\LongRetryLimit,ParamDesc,,%LONG_RETRY_STR%

 HKR,NDI\params\LongRetryLimit,type,0,int

 HKR,NDI\params\LongRetryLimit,min,0,1

 HKR,NDI\params\LongRetryLimit,max,0,255

 HKR,NDI\params\LongRetryLimit,step,0,1

 HKR,NDI\params\LongRetryLimit,optional,0,1



 HKR,,ConfigProfile,0,256

 HKR,NDI\params\ConfigProfile,,0,1

 HKR,NDI\params\ConfigProfile,default,0,1

 HKR,NDI\params\ConfigProfile,ParamDesc,,%CONFIG_PROFILE%

 HKR,NDI\params\ConfigProfile,type,,enum

 HKR,NDI\params\ConfigProfile,flag,1,30,00,00,00

 HKR,NDI\params\ConfigProfile\enum,0,,%CONFIG_PROF_B_ONLY%

 HKR,NDI\params\ConfigProfile\enum,1,,%CONFIG_PROF_MIXED%

 HKR,NDI\params\ConfigProfile\enum,2,,%CONFIG_PROF_MIXED_LONG%

 HKR,NDI\params\ConfigProfile\enum,3,,%CONFIG_PROF_G_ONLY%

 HKR,NDI\params\ConfigProfile\enum,4,,%CONFIG_PROF_TEST%

 HKR,NDI\params\ConfigProfile\enum,5,,%CONFIG_PROF_B_WIFI%

 HKR,NDI\params\ConfigProfile\enum,6,,%CONFIG_PROF_MIXED_SHORT%

 HKR,NDI\params\ConfigProfile\enum,256,,%CONFIG_PROF_WIFI_SPEC%

 HKR,NDI\params\ConfigProfile,optional,0,1



 HKR,,NitroMode,0,"1"

 HKR,NDI\params\NitroMode,,0,1

 HKR,NDI\params\NitroMode,default,0,1

 HKR,NDI\params\NitroMode,ParamDesc,,%NITRO_MODE%

 HKR,NDI\params\NitroMode,type,,enum

 HKR,NDI\params\NitroMode,flag,1,30,00,00,00

 HKR,NDI\params\NitroMode\enum,0,,%OFF_STR%

 HKR,NDI\params\NitroMode\enum,1,,%ON_STR%

 HKR,NDI\params\NitroMode,optional,0,1





[COMMON_PSMODE.reg]

 HKR,defaults,PSMode,0,1

 HKR,NDI\params\PSMode,,0,1

 HKR,Ndi\params\PSMode,default,0,1

 HKR,NDI\params\PSMode,ParamDesc,,%POWER_SAVE_STR%

 HKR,NDI\params\PSMode,type,,enum

 HKR,NDI\params\PSMode,flag,1,30,00,00,00

 HKR,NDI\params\PSMode\enum,1,,%POWER_SAVE_OFF_STR%

 HKR,NDI\params\PSMode\enum,2,,%POWER_SAVE_DYN_STR%

 HKR,NDI\params\PSMode\enum,3,,%POWER_SAVE_MAX_STR%

 HKR,NDI\params\PSMode,optional,0,1

 

[COMMON_PS_MODE_XP.reg]

 HKR,defaults,PSMode,0,1

 HKR,NDI\params\PSMode,,0,1

 HKR,Ndi\params\PSMode,default,0,1

 HKR,NDI\params\PSMode,ParamDesc,,%POWER_SAVE_STR%

 HKR,NDI\params\PSMode,type,,enum

 HKR,NDI\params\PSMode,flag,1,30,00,00,00

 HKR,NDI\params\PSMode\enum,1,,%POWER_SAVE_OFF_STR%

 HKR,NDI\params\PSMode\enum,2,,%POWER_SAVE_DYN_STR%

 HKR,NDI\params\PSMode\enum,3,,%POWER_SAVE_MAX_STR%

; HKR,NDI\params\PSMode\enum,4,,%POWER_SAVE_AUTO_DYN_STR%

; HKR,NDI\params\PSMode\enum,5,,%POWER_SAVE_AUTO_MAX_STR%

 HKR,NDI\params\PSMode,optional,0,1

 

;###############################################################################

[DestinationDirs]

;CopyFiles Section      = Destination Directory ID -- see layout.inf

;-----------------        ------------------------

 DefaultDestDir         = 11 ; Win9x=%windir%\system Win2k=%windir%\system32

 PRISM_DRIVER.copy      = 11 ; Win9x=%windir%\system

 PRISM_DRIVER.copy.NT   = 12 ; Win2k=%windir%\system32\drivers

 PRISM_DRIVER.copy.XP   = 12 ; Winxp=%windir%\system32\drivers

 PRISM_CCU.copy		= 11 ; Win9x=%windir%\system

 PRISM_FWDCB.copy      	= 11 ; Win9x=%windir%\system

 PRISM_FWDCB.copy.NT  	= 12 ; Win2k=%windir%\system32\drivers



[PRISM_CCU.copy]

; O4I01DCS.exe



[PRISM_DRIVER.copy]

 O4I01A.sys



[PRISM_DRIVER.copy.NT]

 O4I01A.sys,O4I01A51.sys



[PRISM_DRIVER.copy.XP]

 O4I01A.sys,O4I01A51.sys



[PRISM_FWDCB.copy]





[PRISM_FWDCB.copy.NT]





[PRISM_COINSTALL.copy.NT]

; O4I01DCS.dll



[SourceDisksNames]

;Source Disk ID         = Disk Name

;--------------           ---------

 1                      = %INSTALL_DISK_STR%,,,



[SourceDisksFiles]      ; Win9x

;File Name              = Source Disk ID

;---------                --------------

 O4I01A.sys           = 1

; O4I01DCS.exe		= 1



[SourceDisksFiles.X86]  ; Win2k/Xp

 O4I01A.sys           = 1

 O4I01A51.sys           = 1

;O4I01DCS.dll		= 1

; O4I01DCS.exe		= 1



;###############################################################################

[Strings]

;String ID              = String Text

;---------                -----------

 VER_VENDOR_STR         = "Accton"

 VER_VENDOR_NAME_STR    = "OEM Corporation"



 PRISM_SERVICE_DISPLAY_DCB = "54Mbps 2.4GHz Wireless Adapter Driver"

 INSTALL_DISK_STR       = "54Mbps 2.4GHz Wireless Adapter Install Disk"



 ON_STR                  = "On"

 OFF_STR                 = "Off"

 RTSTHRESH_STR           = "RTS Threshold"

 FRAGTHRESH_STR          = "Fragmentation Threshold"

 AUTHENT_TYPE_STR        = "Authentication Algorithm"

 POWER_SAVE_STR          = "Power Save Mode"

 POWER_SAVE_OFF_STR      = "Disabled"

 POWER_SAVE_DYN_STR      = "Dynamic"

 POWER_SAVE_MAX_STR      = "Maximum"

; POWER_SAVE_AUTO_DYN_STR = "Auto Dynamic"

; POWER_SAVE_AUTO_MAX_STR = "Auto Maximum"

 LOAD_FIRMWARE_STR       = "Firmware Download"

 SHORT_RETRY_STR         = "Short Retry Limit"

 LONG_RETRY_STR          = "Long Retry Limit"

 ANTENNA_TX_STR          = "Antenna Tx"    

 ANTENNA_RX_STR          = "Antenna Rx"    

 ANTENNA_DIVERSITY_STR   = "Antenna Diversity" 

 CHANNEL_STR             = "Channel"

 DATARATES_STR           = "Data Rate"

 DATARATES_AUTO          = "Fully Automatic"

 ALSR_STR                = "Auto Long Slot Reassociation"

 CONFIG_PROFILE          = "Configuration Profile"

 CONFIG_PROF_B_ONLY      = "B only"

 CONFIG_PROF_MIXED       = "Mixed"

 CONFIG_PROF_MIXED_LONG  = "Mixed Long"

 CONFIG_PROF_G_ONLY      = "G only"

 CONFIG_PROF_TEST        = "Test"

 CONFIG_PROF_B_WIFI      = "B WIFI"

; CONFIG_PROF_MIXED_SHORT = "Mixed Short"

; CONFIG_PROF_WIFI_SPEC   = "WiFi Spec"

 NITRO_MODE              = "Nitro Mode"



 DCB1_DESC_STR            = "54Mbps 802.11g PCI Adapter"

---

