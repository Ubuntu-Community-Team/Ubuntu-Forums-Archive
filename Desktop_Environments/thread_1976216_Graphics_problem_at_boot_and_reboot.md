---
title: "Graphics problem at boot and reboot"
date: 2012-05-08
forum: Desktop Environments
---

### Post by Pistdov on 2012-05-08
This problem began when I tried using a default splash screen. When Xubuntu gets to the logon screen the logon window itself is fine, but the entire rest of my screen is scrambled looking with colors and lines everywhere. Once I enter my logon information it goes away and loads the GUI just fine. The only other time this happens is when I'm shutting down/rebooting-it will do it for just a sec or two before rebooting. I'm using the ATI proprietary drivers.

Here's what I've tried so far:

Edited /etc/default/grub
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" to GRUB_CMDLINE_LINUX_DEFAULT=""
#GRUB_GFXMODE=640x480 to GRUB_GFXMODE=1920X1080

Set splash screen back to none and tried the other ones (it only displays a splash for like half a second now, if at all anyway)

I am assuming this problem has to do with the ATI drivers, but I don't necessarily want to remove them. Hopefully someone has some other ideas I can try. Thanks!

---

### Post by Pistdov on 2012-05-08
Also tried removing /lib/plymouth/themes/default.plymouth and text.plymouth with no success.

I just noticed I haven't installed the FGLRX post-release updates. Going to try this next.

---

### Post by Pistdov on 2012-05-08
Anyone know why the post-release updates won't install for FGLRX? Here's the /var/log/jockey

2012-05-08 13:58:52,076 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c4afc8>
2012-05-08 13:58:54,413 DEBUG: reading modalias file /lib/modules/3.2.0-24-generic/modules.alias
2012-05-08 13:58:54,567 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-05-08 13:58:54,574 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-05-08 13:58:54,642 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2012-05-08 13:58:54,683 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2012-05-08 13:58:54,683 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2012-05-08 13:58:54,716 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2012-05-08 13:58:54,716 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-05-08 13:58:54,790 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-05-08 13:58:54,791 DEBUG: Firmware for DVB cards not available
2012-05-08 13:58:54,791 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-05-08 13:58:54,799 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-05-08 13:58:54,799 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-05-08 13:58:54,799 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-05-08 13:58:54,800 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2012-05-08 13:58:54,809 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2012-05-08 13:58:54,820 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2012-05-08 13:58:55,097 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2012-05-08 13:58:55,098 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-05-08 13:58:55,145 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-05-08 13:58:55,160 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2012-05-08 13:58:55,160 DEBUG: fglrx.available: falling back to default
2012-05-08 13:58:55,249 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2012-05-08 13:58:55,277 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-05-08 13:58:55,278 DEBUG: fglrx.available: falling back to default
2012-05-08 13:58:55,366 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-05-08 13:58:55,367 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-05-08 13:58:55,388 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-05-08 13:58:55,402 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-05-08 13:58:55,406 DEBUG: nvidia.available: falling back to default
2012-05-08 13:58:55,450 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-05-08 13:58:55,451 DEBUG: NVIDIA accelerated graphics driver not available
2012-05-08 13:58:55,461 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-05-08 13:58:55,476 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-05-08 13:58:55,478 DEBUG: nvidia.available: falling back to default
2012-05-08 13:58:55,566 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-05-08 13:58:55,577 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-05-08 13:58:55,593 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2012-05-08 13:58:55,595 DEBUG: nvidia.available: falling back to default
2012-05-08 13:58:55,683 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-05-08 13:58:55,695 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-05-08 13:58:55,709 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2012-05-08 13:58:55,711 DEBUG: nvidia.available: falling back to default
2012-05-08 13:58:55,758 DEBUG: XorgDriverHandler(nvidia_173_updates, nvidia-173-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-05-08 13:58:55,759 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-05-08 13:58:55,769 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-05-08 13:58:55,784 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-05-08 13:58:55,786 DEBUG: nvidia.available: falling back to default
2012-05-08 13:58:55,829 DEBUG: XorgDriverHandler(nvidia_173, nvidia-173, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-05-08 13:58:55,830 DEBUG: NVIDIA accelerated graphics driver not available
2012-05-08 13:58:55,841 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2012-05-08 13:58:55,856 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2012-05-08 13:58:55,858 DEBUG: nvidia.available: falling back to default
2012-05-08 13:58:55,902 DEBUG: XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-05-08 13:58:55,903 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-05-08 13:58:55,903 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-05-08 13:58:55,917 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-05-08 13:58:55,966 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-05-08 13:58:55,967 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-05-08 13:58:55,968 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-05-08 13:58:56,083 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-05-08 13:58:56,119 DEBUG: Software modem not available
2012-05-08 13:58:56,119 DEBUG: all custom handlers loaded
2012-05-08 13:58:56,120 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c4afc8> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-05-08 13:58:56,120 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c4afc8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2012-05-08 13:58:56,134 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-08 13:58:56,336 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-08 13:58:56,336 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c4afc8> about HardwareID('modalias', 'acpiNP0800:')
2012-05-08 13:58:56,336 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c4afc8> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2012-05-08 13:58:56,337 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c4afc8> about HardwareID('modalias', 'pci:v000010DEd00000751sv000010DEsd0000CB84bc05sc00i00')
2012-05-08 13:58:56,687 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c4afc8> about HardwareID('modalias', 'usb:v0D8Cp000Cd0100dc00dsc00dp00ic01isc02ip00')
2012-05-08 13:58:56,701 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c4afc8> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-05-08 13:58:56,701 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c4afc8> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-05-08 13:58:56,702 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-08 13:58:56,702 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-08 13:58:56,702 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-05-08 13:58:56,702 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-05-08 13:58:56,702 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c4afc8> about HardwareID('modalias', 'acpi:PNP0200:')
2012-05-08 13:58:56,702 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c4afc8> about HardwareID('modalias', 'platform:pcspkr')
2012-05-08 13:58:56,702 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2012-05-08 13:58:56,703 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-05-08 13:58:56,703 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2012-05-08 13:58:56,703 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-05-08 13:58:56,703 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c4afc8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2012-05-08 13:58:56,703 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-08 13:58:56,703 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-08 13:58:56,703 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c4afc8> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-05-08 13:58:56,704 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c4afc8> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-05-08 13:58:56,704 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c4afc8> about HardwareID('modalias', 'pci:v000010DEd00000754sv00001458sd00005001bc05sc00i00')
2012-05-08 13:58:56,707 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c4afc8> about HardwareID('modalias', 'pci:v000010DEd00000759sv00001458sd00005002bc01sc01i8a')
2012-05-08 13:58:56,710 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pata_amd'}
2012-05-08 13:58:56,710 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_amd', 'jockey_handler': 'KernelModuleHandler'}
2012-05-08 13:58:56,710 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c4afc8> about HardwareID('modalias', 'wmi:F6CB5C3C-9CAE-4EBD-B577-931EA32A2CC0')
2012-05-08 13:58:56,710 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mxm_wmi'}
2012-05-08 13:58:56,710 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mxm_wmi', 'jockey_handler': 'KernelModuleHandler'}
2012-05-08 13:58:56,711 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c4afc8> about HardwareID('modalias', 'acpiNP0103:')
2012-05-08 13:58:56,711 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c4afc8> about HardwareID('modalias', 'acpiNP0000:')
2012-05-08 13:58:56,711 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c4afc8> about HardwareID('modalias', 'pci:v000010DEd0000075Dsv00001458sd00000C11bc06sc01i00')
2012-05-08 13:58:56,714 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c4afc8> about HardwareID('modalias', 'pci:v000010DEd0000077Esv00001458sd00005004bc0Csc03i20')
2012-05-08 13:58:56,717 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c4afc8> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-05-08 13:58:56,717 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c4afc8> about HardwareID('modalias', 'pci:v00001002d0000AA50sv00001682sd0000AA50bc04sc03i00')
2012-05-08 13:58:57,034 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-05-08 13:58:57,034 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-05-08 13:58:57,034 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c4afc8> about HardwareID('modalias', 'pci:v000010DEd00000AD0sv00001458sd0000B002bc01sc01i85')
2012-05-08 13:58:57,038 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c4afc8> about HardwareID('modalias', 'pci:v00001022d00001102sv00000000sd00000000bc06sc00i00')
2012-05-08 13:58:57,050 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'amd64_edac_mod'}
2012-05-08 13:58:57,050 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'amd64_edac_mod', 'jockey_handler': 'KernelModuleHandler'}
2012-05-08 13:58:57,050 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c4afc8> about HardwareID('modalias', 'usb:v046DpC245d6900dc00dsc00dp00ic03isc00ip00')
2012-05-08 13:58:57,076 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-05-08 13:58:57,076 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-05-08 13:58:57,076 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c4afc8> about HardwareID('modalias', 'usb:v1532p0109d0B62dc00dsc00dp00ic03isc00ip00')
2012-05-08 13:58:57,076 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-05-08 13:58:57,076 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-05-08 13:58:57,076 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c4afc8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2012-05-08 13:58:57,077 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-08 13:58:57,077 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-08 13:58:57,077 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c4afc8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-05-08 13:58:57,077 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-08 13:58:57,077 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-08 13:58:57,077 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c4afc8> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2012-05-08 13:58:57,085 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-05-08 13:58:57,085 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-05-08 13:58:57,085 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c4afc8> about HardwareID('modalias', 'input:b0003v1532p0109e0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2012-05-08 13:58:57,085 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-08 13:58:57,085 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-08 13:58:57,085 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-05-08 13:58:57,085 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-05-08 13:58:57,085 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c4afc8> about HardwareID('modalias', 'acpi:PNP0400:')
2012-05-08 13:58:57,085 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c4afc8> about HardwareID('modalias', 'pci:v0000104Cd00008024sv00001458sd00001000bc0Csc00i10')
2012-05-08 13:58:57,096 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci'}
2012-05-08 13:58:57,097 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2012-05-08 13:58:57,097 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c4afc8> about HardwareID('modalias', 'input:b0003v046DpC245e0110-e0,1,2,4,k110,111,112,113,114,115,116,117,r0,1,8,am4,lsfw')
2012-05-08 13:58:57,097 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-08 13:58:57,097 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-08 13:58:57,097 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-05-08 13:58:57,097 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-05-08 13:58:57,097 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c4afc8> about HardwareID('modalias', 'dmi:bvnAwardSoftwareInternational,Inc.:bvrF7:bd01/22/2009:svnGigabyteTechnologyCo.,Ltd.nM750SLI-DS4vr:rvnGigabyteTechnologyCo.,Ltd.:rnM750SLI-DS4:rvrx.x:cvnGigabyteTechnologyCo.,Ltd.:ct3:cvr:')
2012-05-08 13:58:57,112 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c4afc8> about HardwareID('modalias', 'pci:v00001022d00001100sv00000000sd00000000bc06sc00i00')
2012-05-08 13:58:57,112 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c4afc8> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-05-08 13:58:57,112 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c4afc8> about HardwareID('modalias', 'pci:v000010DEd00000760sv00001458sd0000E000bc02sc00i00')
2012-05-08 13:58:57,115 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'forcedeth'}
2012-05-08 13:58:57,115 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'forcedeth', 'jockey_handler': 'KernelModuleHandler'}
2012-05-08 13:58:57,116 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c4afc8> about HardwareID('modalias', 'input:b0003v1532p0109e0110-e0,1,2,3,4,k71,72,73,74,77,80,82,83,85,86,87,88,89,8A,8B,8C,8E,8F,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B1,B2,B5,CE,CF,D0,D1,D2,D4,D8,D9,DB,E4,EA,EB,F1,100,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,1BA,r6,a20,m4,lsfw')
2012-05-08 13:58:57,116 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-08 13:58:57,116 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-08 13:58:57,116 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-05-08 13:58:57,116 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-05-08 13:58:57,116 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-05-08 13:58:57,116 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-05-08 13:58:57,116 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c4afc8> about HardwareID('modalias', 'usb:v1532p0109d0B62dc00dsc00dp00ic03isc01ip01')
2012-05-08 13:58:57,117 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-05-08 13:58:57,117 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-05-08 13:58:57,117 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2012-05-08 13:58:57,117 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2012-05-08 13:58:57,117 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c4afc8> about HardwareID('modalias', 'usb:v0D8Cp000Cd0100dc00dsc00dp00ic01isc01ip00')
2012-05-08 13:58:57,117 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio'}
2012-05-08 13:58:57,117 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio', 'jockey_handler': 'KernelModuleHandler'}
2012-05-08 13:58:57,117 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c4afc8> about HardwareID('modalias', 'usb:v0D8Cp000Cd0100dc00dsc00dp00ic03isc00ip00')
2012-05-08 13:58:57,118 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-05-08 13:58:57,118 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-05-08 13:58:57,118 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c4afc8> about HardwareID('modalias', 'pci:v00001022d00001103sv00000000sd00000000bc06sc00i00')
2012-05-08 13:58:57,118 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'k8temp'}
2012-05-08 13:58:57,118 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k8temp', 'jockey_handler': 'KernelModuleHandler'}
2012-05-08 13:58:57,118 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c4afc8> about HardwareID('modalias', 'pci:v000010DEd00000568sv00000000sd00000000bc05sc00i00')
2012-05-08 13:58:57,121 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c4afc8> about HardwareID('modalias', 'pci:v00001022d00001101sv00000000sd00000000bc06sc00i00')
2012-05-08 13:58:57,122 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c4afc8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-05-08 13:58:57,122 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-08 13:58:57,122 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-08 13:58:57,122 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c4afc8> about HardwareID('modalias', 'acpiNP0C01:')
2012-05-08 13:58:57,122 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c4afc8> about HardwareID('modalias', 'wmi:A1799AF2-9429-4529-927E-DFE13736EEBA')
2012-05-08 13:58:57,122 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c4afc8> about HardwareID('modalias', 'acpiNP0100:')
2012-05-08 13:58:57,122 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c4afc8> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-05-08 13:58:57,122 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c4afc8> about HardwareID('modalias', 'pci:v000010DEd00000752sv00001458sd00000C11bc0Csc05i00')
2012-05-08 13:58:57,125 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_nforce2'}
2012-05-08 13:58:57,126 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_nforce2', 'jockey_handler': 'KernelModuleHandler'}
2012-05-08 13:58:57,126 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c4afc8> about HardwareID('modalias', 'acpiNP0501:')
2012-05-08 13:58:57,126 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c4afc8> about HardwareID('modalias', 'usb:v046DpC245d6900dc00dsc00dp00ic03isc01ip02')
2012-05-08 13:58:57,126 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-05-08 13:58:57,126 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-05-08 13:58:57,126 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2012-05-08 13:58:57,127 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-05-08 13:58:57,127 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c4afc8> about HardwareID('modalias', 'wmi:A1799ACA-9429-4529-927E-DFE13736EEBA')
2012-05-08 13:58:57,127 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c4afc8> about HardwareID('modalias', 'pci:v00001002d00006899sv00001682sd00002970bc03sc00i00')
2012-05-08 13:58:57,131 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2012-05-08 13:58:57,131 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2012-05-08 13:58:57,131 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx'}
2012-05-08 13:58:57,177 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-05-08 13:58:57,177 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-05-08 13:58:57,131 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2012-05-08 13:58:57,306 DEBUG: fglrx.available: falling back to default
2012-05-08 13:58:57,356 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-05-08 13:58:57,356 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-05-08 13:58:57,331 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2012-05-08 13:58:57,477 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2012-05-08 13:58:57,500 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-05-08 13:58:57,501 DEBUG: fglrx_updates is not the alternative in use
2012-05-08 13:58:57,477 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-05-08 13:58:57,507 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-05-08 13:58:57,516 DEBUG: fglrx.available: falling back to default
2012-05-08 13:58:57,569 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-05-08 13:58:57,569 DEBUG: fglrx_updates is not the alternative in use
2012-05-08 13:58:57,543 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-05-08 13:58:57,569 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2012-05-08 13:58:57,594 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-05-08 13:58:57,595 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-05-08 13:58:57,570 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2012-05-08 13:58:57,723 DEBUG: fglrx.available: falling back to default
2012-05-08 13:58:57,772 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-05-08 13:58:57,772 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-05-08 13:58:57,748 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2012-05-08 13:58:57,893 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c4afc8> about HardwareID('modalias', 'pci:v000010DEd0000077Csv00001458sd00005004bc0Csc03i20')
2012-05-08 13:58:57,899 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c4afc8> about HardwareID('modalias', 'pci:v000010DEd0000075Asv00001458sd0000026Fbc06sc04i01')
2012-05-08 13:58:57,904 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c4afc8> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-05-08 13:58:57,904 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-05-08 13:58:57,904 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-05-08 13:58:57,904 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2012-05-08 13:58:57,905 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-05-08 13:58:57,905 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c4afc8> about HardwareID('modalias', 'input:b0003v0D8Cp000Ce0100-e0,1,4,k71,72,73,ram4,lsfw')
2012-05-08 13:58:57,905 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-08 13:58:57,905 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-08 13:58:57,905 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-05-08 13:58:57,905 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-05-08 13:58:57,905 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c4afc8> about HardwareID('modalias', 'pci:v000010DEd00000774sv00001458sd0000A002bc04sc03i00')
2012-05-08 13:58:57,910 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-05-08 13:58:57,911 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-05-08 13:58:57,911 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c4afc8> about HardwareID('modalias', 'wmi:921A2F40-0DC4-402D-AC18-B48444EF9ED2')
2012-05-08 13:58:57,911 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c4afc8> about HardwareID('modalias', 'acpiNP0B00:')
2012-05-08 13:58:57,911 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2fc2320> about HardwareID('modalias', 'acpiNP0C04:')
2012-05-08 13:58:57,911 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2fc2320> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2012-05-08 13:58:57,911 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2fc2320> about HardwareID('modalias', 'acpiNP0800:')
2012-05-08 13:58:57,911 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2fc2320> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2012-05-08 13:58:57,911 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2fc2320> about HardwareID('modalias', 'pci:v000010DEd00000751sv000010DEsd0000CB84bc05sc00i00')
2012-05-08 13:58:57,911 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2fc2320> about HardwareID('modalias', 'usb:v0D8Cp000Cd0100dc00dsc00dp00ic01isc02ip00')
2012-05-08 13:58:57,912 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2fc2320> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-05-08 13:58:57,912 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2fc2320> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-05-08 13:58:57,912 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2fc2320> about HardwareID('modalias', 'acpiNP0200:')
2012-05-08 13:58:57,912 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2fc2320> about HardwareID('modalias', 'platformcspkr')
2012-05-08 13:58:57,912 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2fc2320> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2012-05-08 13:58:57,912 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2fc2320> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-05-08 13:58:57,912 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2fc2320> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-05-08 13:58:57,912 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2fc2320> about HardwareID('modalias', 'pci:v000010DEd00000754sv00001458sd00005001bc05sc00i00')
2012-05-08 13:58:57,912 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2fc2320> about HardwareID('modalias', 'pci:v000010DEd00000759sv00001458sd00005002bc01sc01i8a')
2012-05-08 13:58:57,913 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2fc2320> about HardwareID('modalias', 'wmi:F6CB5C3C-9CAE-4EBD-B577-931EA32A2CC0')
2012-05-08 13:58:57,913 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2fc2320> about HardwareID('modalias', 'acpiNP0103:')
2012-05-08 13:58:57,913 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2fc2320> about HardwareID('modalias', 'acpiNP0000:')
2012-05-08 13:58:57,913 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2fc2320> about HardwareID('modalias', 'pci:v000010DEd0000075Dsv00001458sd00000C11bc06sc01i00')
2012-05-08 13:58:57,913 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2fc2320> about HardwareID('modalias', 'pci:v000010DEd0000077Esv00001458sd00005004bc0Csc03i20')
2012-05-08 13:58:57,913 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2fc2320> about HardwareID('modalias', 'acpiNP0C02:')
2012-05-08 13:58:57,913 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2fc2320> about HardwareID('modalias', 'pci:v00001002d0000AA50sv00001682sd0000AA50bc04sc03i00')
2012-05-08 13:58:57,913 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2fc2320> about HardwareID('modalias', 'pci:v000010DEd00000AD0sv00001458sd0000B002bc01sc01i85')
2012-05-08 13:58:57,913 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2fc2320> about HardwareID('modalias', 'pci:v00001022d00001102sv00000000sd00000000bc06sc00i00')
2012-05-08 13:58:57,913 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2fc2320> about HardwareID('modalias', 'usb:v046DpC245d6900dc00dsc00dp00ic03isc00ip00')
2012-05-08 13:58:57,914 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2fc2320> about HardwareID('modalias', 'usb:v1532p0109d0B62dc00dsc00dp00ic03isc00ip00')
2012-05-08 13:58:57,914 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2fc2320> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2012-05-08 13:58:57,914 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2fc2320> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-05-08 13:58:57,914 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2fc2320> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2012-05-08 13:58:57,914 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2fc2320> about HardwareID('modalias', 'input:b0003v1532p0109e0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2012-05-08 13:58:57,914 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2fc2320> about HardwareID('modalias', 'acpiNP0400:')
2012-05-08 13:58:57,914 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2fc2320> about HardwareID('modalias', 'pci:v0000104Cd00008024sv00001458sd00001000bc0Csc00i10')
2012-05-08 13:58:57,914 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2fc2320> about HardwareID('modalias', 'input:b0003v046DpC245e0110-e0,1,2,4,k110,111,112,113,114,115,116,117,r0,1,8,am4,lsfw')
2012-05-08 13:58:57,914 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2fc2320> about HardwareID('modalias', 'dmi:bvnAwardSoftwareInternational,Inc.:bvrF7:bd01/22/2009:svnGigabyteTechnologyCo.,Ltd.nM750SLI-DS4vr:rvnGigabyteTechnologyCo.,Ltd.:rnM750SLI-DS4:rvrx.x:cvnGigabyteTechnologyCo.,Ltd.:ct3:cvr:')
2012-05-08 13:58:57,914 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2fc2320> about HardwareID('modalias', 'pci:v00001022d00001100sv00000000sd00000000bc06sc00i00')
2012-05-08 13:58:57,915 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2fc2320> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-05-08 13:58:57,915 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2fc2320> about HardwareID('modalias', 'pci:v000010DEd00000760sv00001458sd0000E000bc02sc00i00')
2012-05-08 13:58:57,915 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2fc2320> about HardwareID('modalias', 'input:b0003v1532p0109e0110-e0,1,2,3,4,k71,72,73,74,77,80,82,83,85,86,87,88,89,8A,8B,8C,8E,8F,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B1,B2,B5,CE,CF,D0,D1,D2,D4,D8,D9,DB,E4,EA,EB,F1,100,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,1BA,r6,a20,m4,lsfw')
2012-05-08 13:58:57,915 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2fc2320> about HardwareID('modalias', 'usb:v1532p0109d0B62dc00dsc00dp00ic03isc01ip01')
2012-05-08 13:58:57,915 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2fc2320> about HardwareID('modalias', 'usb:v0D8Cp000Cd0100dc00dsc00dp00ic01isc01ip00')
2012-05-08 13:58:57,915 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2fc2320> about HardwareID('modalias', 'usb:v0D8Cp000Cd0100dc00dsc00dp00ic03isc00ip00')
2012-05-08 13:58:57,915 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2fc2320> about HardwareID('modalias', 'pci:v00001022d00001103sv00000000sd00000000bc06sc00i00')
2012-05-08 13:58:57,915 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2fc2320> about HardwareID('modalias', 'pci:v000010DEd00000568sv00000000sd00000000bc05sc00i00')
2012-05-08 13:58:57,915 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2fc2320> about HardwareID('modalias', 'pci:v00001022d00001101sv00000000sd00000000bc06sc00i00')
2012-05-08 13:58:57,915 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2fc2320> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-05-08 13:58:57,916 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2fc2320> about HardwareID('modalias', 'acpiNP0C01:')
2012-05-08 13:58:57,916 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2fc2320> about HardwareID('modalias', 'wmi:A1799AF2-9429-4529-927E-DFE13736EEBA')
2012-05-08 13:58:57,916 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2fc2320> about HardwareID('modalias', 'acpiNP0100:')
2012-05-08 13:58:57,916 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2fc2320> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-05-08 13:58:57,916 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2fc2320> about HardwareID('modalias', 'pci:v000010DEd00000752sv00001458sd00000C11bc0Csc05i00')
2012-05-08 13:58:57,916 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2fc2320> about HardwareID('modalias', 'acpiNP0501:')
2012-05-08 13:58:57,916 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2fc2320> about HardwareID('modalias', 'usb:v046DpC245d6900dc00dsc00dp00ic03isc01ip02')
2012-05-08 13:58:57,916 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2fc2320> about HardwareID('modalias', 'wmi:A1799ACA-9429-4529-927E-DFE13736EEBA')
2012-05-08 13:58:57,916 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2fc2320> about HardwareID('modalias', 'pci:v00001002d00006899sv00001682sd00002970bc03sc00i00')
2012-05-08 13:58:57,916 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2fc2320> about HardwareID('modalias', 'pci:v000010DEd0000077Csv00001458sd00005004bc0Csc03i20')
2012-05-08 13:58:57,917 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2fc2320> about HardwareID('modalias', 'pci:v000010DEd0000075Asv00001458sd0000026Fbc06sc04i01')
2012-05-08 13:58:57,917 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2fc2320> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-05-08 13:58:57,917 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2fc2320> about HardwareID('modalias', 'input:b0003v0D8Cp000Ce0100-e0,1,4,k71,72,73,ram4,lsfw')
2012-05-08 13:58:57,917 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2fc2320> about HardwareID('modalias', 'pci:v000010DEd00000774sv00001458sd0000A002bc04sc03i00')
2012-05-08 13:58:57,917 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2fc2320> about HardwareID('modalias', 'wmi:921A2F40-0DC4-402D-AC18-B48444EF9ED2')
2012-05-08 13:58:57,917 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2fc2320> about HardwareID('modalias', 'acpiNP0B00:')
2012-05-08 13:58:57,971 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-05-08 13:58:57,971 DEBUG: fglrx_updates is not the alternative in use
2012-05-08 13:58:58,029 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-05-08 13:58:58,029 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-05-08 13:58:58,279 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-05-08 13:58:58,280 DEBUG: fglrx_updates is not the alternative in use
2012-05-08 13:58:58,313 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-05-08 13:58:58,314 DEBUG: fglrx_updates is not the alternative in use
2012-05-08 13:58:58,339 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-05-08 13:58:58,340 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-05-08 13:59:15,729 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-05-08 13:59:15,730 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-05-08 13:59:16,960 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-05-08 13:59:16,961 DEBUG: fglrx_updates is not the alternative in use
2012-05-08 13:59:17,869 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-05-08 13:59:17,869 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-05-08 13:59:23,304 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-05-08 13:59:23,304 DEBUG: fglrx_updates is not the alternative in use
2012-05-08 14:02:02,108 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-05-08 14:02:02,108 DEBUG: fglrx_updates is not the alternative in use
2012-05-08 14:02:02,959 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-05-08 14:02:02,960 DEBUG: fglrx_updates is not the alternative in use
2012-05-08 14:02:10,684 DEBUG: Installing package: fglrx-updates
2012-05-08 14:02:11,442 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 0.000000
2012-05-08 14:02:11,444 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 0.000000
2012-05-08 14:02:11,473 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 0.000000
2012-05-08 14:02:11,633 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 0.000000
2012-05-08 14:02:11,806 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 0.001566
2012-05-08 14:02:12,307 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 0.157377
2012-05-08 14:02:12,809 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 0.518939
2012-05-08 14:02:13,310 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 0.964399
2012-05-08 14:02:13,812 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 1.629593
2012-05-08 14:02:14,313 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 2.172935
2012-05-08 14:02:14,814 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 3.001931
2012-05-08 14:02:15,316 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 3.657137
2012-05-08 14:02:15,817 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 4.374268
2012-05-08 14:02:16,318 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 5.087404
2012-05-08 14:02:16,819 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 5.598784
2012-05-08 14:02:17,320 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 6.166097
2012-05-08 14:02:17,822 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 6.701448
2012-05-08 14:02:18,323 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 7.264766
2012-05-08 14:02:18,825 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 7.842066
2012-05-08 14:02:19,377 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 8.451328
2012-05-08 14:02:19,878 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 8.986680
2012-05-08 14:02:20,380 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 9.563980
2012-05-08 14:02:20,881 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 10.131293
2012-05-08 14:02:21,383 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 10.718581
2012-05-08 14:02:21,884 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 11.289889
2012-05-08 14:02:22,385 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 11.887165
2012-05-08 14:02:22,887 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 12.354599
2012-05-08 14:02:23,388 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 12.814043
2012-05-08 14:02:23,889 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 13.305447
2012-05-08 14:02:24,391 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 13.860774
2012-05-08 14:02:24,892 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 14.404116
2012-05-08 14:02:25,393 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 15.053329
2012-05-08 14:02:25,895 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 15.698548
2012-05-08 14:02:26,396 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 16.291829
2012-05-08 14:02:26,897 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 16.917071
2012-05-08 14:02:27,399 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 17.504360
2012-05-08 14:02:27,900 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 18.135595
2012-05-08 14:02:28,402 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 18.784808
2012-05-08 14:02:28,903 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 19.392073
2012-05-08 14:02:29,404 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 20.013320
2012-05-08 14:02:29,906 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 20.642558
2012-05-08 14:02:30,407 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 21.289774
2012-05-08 14:02:30,908 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 21.948975
2012-05-08 14:02:31,410 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 22.718043
2012-05-08 14:02:31,911 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 23.573007
2012-05-08 14:02:32,412 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 24.382027
2012-05-08 14:02:32,914 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 25.262960
2012-05-08 14:02:33,415 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 26.000067
2012-05-08 14:02:33,917 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 26.449522
2012-05-08 14:02:34,418 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 27.036811
2012-05-08 14:02:34,919 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 27.620104
2012-05-08 14:02:35,420 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 28.147465
2012-05-08 14:02:35,922 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 28.826642
2012-05-08 14:02:36,423 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 29.385964
2012-05-08 14:02:36,925 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 29.981243
2012-05-08 14:02:37,426 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 30.650432
2012-05-08 14:02:37,927 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 31.303641
2012-05-08 14:02:38,428 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 31.960845
2012-05-08 14:02:38,930 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 32.472225
2012-05-08 14:02:39,431 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 32.951644
2012-05-08 14:02:39,932 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 33.508969
2012-05-08 14:02:40,433 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 34.106245
2012-05-08 14:02:40,935 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 34.735483
2012-05-08 14:02:41,436 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 35.352735
2012-05-08 14:02:41,937 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 36.021924
2012-05-08 14:02:42,438 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 36.699104
2012-05-08 14:02:42,940 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 37.348317
2012-05-08 14:02:43,441 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 37.955582
2012-05-08 14:02:43,942 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 38.584819
2012-05-08 14:02:44,443 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 39.174105
2012-05-08 14:02:44,945 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 39.805341
2012-05-08 14:02:45,446 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 40.422593
2012-05-08 14:02:45,947 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 41.131734
2012-05-08 14:02:46,449 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 41.798925
2012-05-08 14:02:46,950 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 42.416177
2012-05-08 14:02:47,451 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 43.037425
2012-05-08 14:02:47,952 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 43.574774
2012-05-08 14:02:48,454 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 44.112123
2012-05-08 14:02:48,955 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 44.787305
2012-05-08 14:02:49,457 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 45.498443
2012-05-08 14:02:49,958 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 46.293480
2012-05-08 14:02:50,459 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 47.054558
2012-05-08 14:02:50,960 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 47.787669
2012-05-08 14:02:51,462 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 48.602682
2012-05-08 14:02:51,963 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 49.391726
2012-05-08 14:02:52,464 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 50.180770
2012-05-08 14:02:52,965 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 50.989790
2012-05-08 14:02:53,467 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 51.830771
2012-05-08 14:02:53,968 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 52.633798
2012-05-08 14:02:54,469 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 53.396873
2012-05-08 14:02:54,970 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 54.072055
2012-05-08 14:02:55,472 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 54.797177
2012-05-08 14:02:55,973 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 55.502322
2012-05-08 14:02:56,474 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 56.113582
2012-05-08 14:02:56,976 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 56.804744
2012-05-08 14:02:57,477 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 57.593789
2012-05-08 14:02:57,978 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 58.450750
2012-05-08 14:02:58,480 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 59.259770
2012-05-08 14:02:58,981 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 59.853051
2012-05-08 14:02:59,483 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 60.568185
2012-05-08 14:02:59,984 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 61.237374
2012-05-08 14:03:00,485 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 61.896575
2012-05-08 14:03:00,987 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 62.495849
2012-05-08 14:03:01,488 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 63.214978
2012-05-08 14:03:01,989 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 63.844216
2012-05-08 14:03:02,491 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 64.361589
2012-05-08 14:03:02,992 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 64.950875
2012-05-08 14:03:03,493 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 65.372364
2012-05-08 14:03:03,994 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 65.807837
2012-05-08 14:03:04,496 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 66.271275
2012-05-08 14:03:04,997 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 66.762680
2012-05-08 14:03:05,498 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 67.260077
2012-05-08 14:03:06,000 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 67.709533
2012-05-08 14:03:06,501 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 68.202935
2012-05-08 14:03:07,002 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 68.698335
2012-05-08 14:03:07,503 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 69.147790
2012-05-08 14:03:08,005 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 69.661168
2012-05-08 14:03:08,506 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 70.194522
2012-05-08 14:03:09,007 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 70.765830
2012-05-08 14:03:09,508 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 71.305176
2012-05-08 14:03:10,010 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 71.914438
2012-05-08 14:03:10,511 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 72.547671
2012-05-08 14:03:11,012 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 73.154935
2012-05-08 14:03:11,514 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 73.824124
2012-05-08 14:03:12,015 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 74.764984
2012-05-08 14:03:12,516 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 75.711837
2012-05-08 14:03:13,017 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 76.566801
2012-05-08 14:03:13,518 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 77.108145
2012-05-08 14:03:14,020 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 77.777335
2012-05-08 14:03:14,521 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 78.434538
2012-05-08 14:03:15,022 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 78.822069
2012-05-08 14:03:15,523 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 79.503244
2012-05-08 14:03:16,025 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 80.058571
2012-05-08 14:03:16,526 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 80.703789
2012-05-08 14:03:17,027 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 80.959479
2012-05-08 14:03:17,528 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 81.752518
2012-05-08 14:03:18,030 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 82.309843
2012-05-08 14:03:18,531 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 82.845195
2012-05-08 14:03:19,032 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 83.470437
2012-05-08 14:03:19,533 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 84.073706
2012-05-08 14:03:20,035 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 84.702944
2012-05-08 14:03:20,536 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 85.284239
2012-05-08 14:03:21,037 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 85.919470
2012-05-08 14:03:21,538 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 86.496770
2012-05-08 14:03:22,040 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 87.036117
2012-05-08 14:03:22,541 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 87.727280
2012-05-08 14:03:23,042 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 88.386481
2012-05-08 14:03:23,543 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 88.991748
2012-05-08 14:03:24,045 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 89.565053
2012-05-08 14:03:24,546 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 90.090416
2012-05-08 14:03:25,047 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 90.631761
2012-05-08 14:03:25,549 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 91.237027
2012-05-08 14:03:25,976 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 91.827651
2012-05-08 14:03:25,977 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 91.831880
2012-05-08 14:03:26,478 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 92.429156
2012-05-08 14:03:26,979 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 93.062389
2012-05-08 14:03:27,480 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 93.691626
2012-05-08 14:03:27,981 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 94.406760
2012-05-08 14:03:28,483 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 95.008032
2012-05-08 14:03:28,984 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 95.523407
2012-05-08 14:03:29,486 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 96.142657
2012-05-08 14:03:29,987 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 96.781882
2012-05-08 14:03:30,488 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 97.393142
2012-05-08 14:03:30,989 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 98.054341
2012-05-08 14:03:31,491 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 98.627646
2012-05-08 14:03:31,992 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 99.180976
2012-05-08 14:03:32,493 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 99.772412
2012-05-08 14:03:32,641 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 100.000000
2012-05-08 14:03:33,494 DEBUG: install progress dpkg-exec 0.000000
2012-05-08 14:03:35,078 DEBUG: install progress fglrx-amdcccle 0.000000
2012-05-08 14:03:35,178 DEBUG: install progress fglrx-amdcccle 6.250000
2012-05-08 14:03:35,232 DEBUG: install progress fglrx-amdcccle 12.500000
2012-05-08 14:03:35,460 DEBUG: install progress fglrx-amdcccle 18.750000
2012-05-08 14:03:35,918 DEBUG: install progress fglrx 18.750000
2012-05-08 14:03:35,919 DEBUG: install progress fglrx 25.000000
2012-05-08 14:04:02,669 DEBUG: install progress fglrx 31.250000
2012-05-08 14:04:03,532 DEBUG: install progress fglrx 37.500000
2012-05-08 14:04:03,735 DEBUG: install progress ureadahead 37.500000
2012-05-08 14:04:03,954 DEBUG: install progress initramfs-tools 37.500000
2012-05-08 14:04:19,478 DEBUG: install progress libc-bin 37.500000
2012-05-08 14:04:19,967 DEBUG: install progress dpkg-exec 37.500000
2012-05-08 14:04:20,859 DEBUG: install progress fglrx-updates 37.500000
2012-05-08 14:04:20,859 DEBUG: install progress fglrx-updates 43.750000
2012-05-08 14:04:25,503 DEBUG: install progress fglrx-updates 50.000000
2012-05-08 14:04:25,605 DEBUG: install progress fglrx-updates 56.250000
2012-05-08 14:04:25,889 DEBUG: install progress fglrx-amdcccle-updates 56.250000
2012-05-08 14:04:25,990 DEBUG: install progress fglrx-amdcccle-updates 62.500000
2012-05-08 14:04:26,533 DEBUG: install progress fglrx-amdcccle-updates 68.750000
2012-05-08 14:04:26,638 DEBUG: install progress fglrx-amdcccle-updates 75.000000
2012-05-08 14:04:26,748 DEBUG: install progress ureadahead 75.000000
2012-05-08 14:04:27,147 DEBUG: install progress dpkg-exec 75.000000
2012-05-08 14:04:27,262 DEBUG: install progress fglrx-updates 75.000000
2012-05-08 14:04:27,723 DEBUG: install progress fglrx-updates 81.250000
2012-05-08 14:04:49,103 DEBUG: install progress fglrx-updates 87.500000
2012-05-08 14:04:49,371 DEBUG: install progress fglrx-amdcccle-updates 87.500000
2012-05-08 14:04:49,464 DEBUG: install progress fglrx-amdcccle-updates 93.750000
2012-05-08 14:04:49,540 DEBUG: install progress fglrx-amdcccle-updates 100.000000
2012-05-08 14:04:49,633 DEBUG: install progress initramfs-tools 100.000000
2012-05-08 14:05:03,939 DEBUG: install progress libc-bin 100.000000
2012-05-08 14:05:05,645 DEBUG: (Reading database ... 159265 files and directories currently installed.)
Removing fglrx-amdcccle ...
Removing fglrx ...
Removing all DKMS Modules
Done.
update-alternatives: removing manually selected alternative - switching x86_64-linux-gnu_gl_conf to auto mode
update-alternatives: using /usr/lib/pxpress/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /usr/bin/amdcccle because associated file /usr/lib/fglrx/bin/amdcccle (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdcccle.desktop because associated file /usr/share/fglrx/amdcccle.desktop (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdccclesu.desktop because associated file /usr/share/fglrx/amdccclesu.desktop (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl32.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl32.icd (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/bin/amdupdaterandrconfig because associated file /usr/lib/fglrx/bin/amdupdaterandrconfig (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/bin/amdxdg-su because associated file /usr/lib/fglrx/bin/amdxdg-su (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: removing manually selected alternative - switching i386-linux-gnu_gl_conf to auto mode
update-alternatives: using /usr/lib/pxpress/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-alternatives: using /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-24-generic
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Selecting previously unselected package fglrx-updates.
(Reading database ... 158994 files and directories currently installed.)
Unpacking fglrx-updates (from .../fglrx-updates_2%3a8.960-0ubuntu1_amd64.deb) ...
Selecting previously unselected package fglrx-amdcccle-updates.
Unpacking fglrx-amdcccle-updates (from .../fglrx-amdcccle-updates_2%3a8.960-0ubuntu1_amd64.deb) ...
Processing triggers for ureadahead ...
Setting up fglrx-updates (2:8.960-0ubuntu1) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl32.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl32.icd (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken.
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl32.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl32.icd (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: using /usr/lib/fglrx/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
Loading new fglrx-updates-8.960 DKMS files...
First Installation: checking all kernels...
Building only for 3.2.0-24-generic
Building for architecture x86_64
Building initial module for 3.2.0-24-generic
Done.

fglrx_updates:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-24-generic/updates/dkms/

depmod....

DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Setting up fglrx-amdcccle-updates (2:8.960-0ubuntu1) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-24-generic
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

2012-05-08 14:05:06,071 WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver
2012-05-08 14:05:28,954 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-05-08 14:05:28,954 DEBUG: fglrx_updates is not the alternative in use
2012-05-08 14:05:29,013 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-05-08 14:05:29,014 DEBUG: fglrx_updates is not the alternative in use
2012-05-08 14:06:56,424 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-05-08 14:06:56,425 DEBUG: fglrx_updates is not the alternative in use
2012-05-08 14:06:56,482 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-05-08 14:06:56,482 DEBUG: fglrx_updates is not the alternative in use
2012-05-08 14:06:56,564 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-05-08 14:06:56,564 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-05-08 14:06:56,953 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-05-08 14:06:56,953 DEBUG: fglrx_updates is not the alternative in use
2012-05-08 14:06:56,978 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-05-08 14:06:56,978 DEBUG: fglrx_updates is not the alternative in use
2012-05-08 14:06:57,022 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-05-08 14:06:57,022 DEBUG: fglrx_updates is not the alternative in use
2012-05-08 14:06:57,048 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-05-08 14:06:57,048 DEBUG: fglrx_updates is not the alternative in use
2012-05-08 14:06:57,081 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-05-08 14:06:57,081 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-05-08 14:07:00,126 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-05-08 14:07:00,127 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-05-08 14:07:05,241 DEBUG: Shutting down

---

### Post by Pistdov on 2012-05-08
I tried purging fglrx and that gives me errors. Then I tired installing the latest updates and still got errors. Don't know what's wrong.

---

