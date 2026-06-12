---
title: "Resolution for 1680x1050 is not there?"
date: 2012-07-05
forum: Desktop Environments
---

### Post by filip007 on 2012-07-05
I can't get to work 22" LCD with Radeon 3870, can't set to 1680x1050.

I was trying to install 3D driver and that did not work...i like to cooldown my GPU with 3D driver, else will be running like it is.

Here is my jockey.log, i hope that helps.

[PHP]2012-07-05 18:24:36,663 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x1afbd40>
2012-07-05 18:24:38,661 DEBUG: reading modalias file /lib/modules/3.2.0-23-generic/modules.alias
2012-07-05 18:24:38,957 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-07-05 18:24:39,006 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-07-05 18:24:39,141 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2012-07-05 18:24:39,201 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2012-07-05 18:24:39,202 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2012-07-05 18:24:39,240 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2012-07-05 18:24:39,241 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-07-05 18:24:39,362 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-07-05 18:24:39,373 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2012-07-05 18:24:39,373 DEBUG: fglrx.available: falling back to default
2012-07-05 18:24:39,640 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2012-07-05 18:24:39,646 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-07-05 18:24:39,653 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-07-05 18:24:39,653 DEBUG: fglrx.available: falling back to default
2012-07-05 18:24:39,683 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-07-05 18:24:39,684 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-07-05 18:24:39,762 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-07-05 18:24:39,763 DEBUG: Firmware for DVB cards not available
2012-07-05 18:24:39,763 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-07-05 18:24:39,769 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-07-05 18:24:39,773 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-07-05 18:24:39,775 DEBUG: nvidia.available: falling back to default
2012-07-05 18:24:39,789 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-07-05 18:24:39,790 DEBUG: NVIDIA accelerated graphics driver not available
2012-07-05 18:24:39,796 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-07-05 18:24:39,801 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-07-05 18:24:39,801 DEBUG: nvidia.available: falling back to default
2012-07-05 18:24:39,834 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-07-05 18:24:39,838 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-07-05 18:24:39,844 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2012-07-05 18:24:39,844 DEBUG: nvidia.available: falling back to default
2012-07-05 18:24:39,888 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-07-05 18:24:39,893 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-07-05 18:24:39,898 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2012-07-05 18:24:39,898 DEBUG: nvidia.available: falling back to default
2012-07-05 18:24:39,924 DEBUG: XorgDriverHandler(nvidia_173_updates, nvidia-173-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-07-05 18:24:39,924 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-07-05 18:24:39,927 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-07-05 18:24:39,935 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-07-05 18:24:39,938 DEBUG: nvidia.available: falling back to default
2012-07-05 18:24:39,954 DEBUG: XorgDriverHandler(nvidia_173, nvidia-173, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-07-05 18:24:39,955 DEBUG: NVIDIA accelerated graphics driver not available
2012-07-05 18:24:39,958 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2012-07-05 18:24:39,963 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2012-07-05 18:24:39,963 DEBUG: nvidia.available: falling back to default
2012-07-05 18:24:39,979 DEBUG: XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-07-05 18:24:39,979 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-07-05 18:24:39,979 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-07-05 18:24:40,016 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-07-05 18:24:40,017 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-07-05 18:24:40,018 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-07-05 18:24:40,018 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-07-05 18:24:40,030 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-07-05 18:24:40,059 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-07-05 18:24:40,059 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-07-05 18:24:40,059 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2012-07-05 18:24:40,065 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2012-07-05 18:24:40,069 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2012-07-05 18:24:40,096 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2012-07-05 18:24:40,096 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-07-05 18:24:40,112 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-07-05 18:24:40,146 DEBUG: Software modem not available
2012-07-05 18:24:40,146 DEBUG: all custom handlers loaded
2012-07-05 18:24:40,146 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1afbd40> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-07-05 18:24:40,146 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1afbd40> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2012-07-05 18:24:40,151 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-05 18:24:40,282 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:24:40,282 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1afbd40> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-07-05 18:24:40,282 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1afbd40> about HardwareID('modalias', 'acpi:PNP0103:')
2012-07-05 18:24:40,282 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1afbd40> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001458sd0000E000bc02sc00i00')
2012-07-05 18:24:40,291 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2012-07-05 18:24:40,292 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:24:40,292 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1afbd40> about HardwareID('modalias', 'platform:pcspkr')
2012-07-05 18:24:40,292 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2012-07-05 18:24:40,292 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:24:40,292 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2012-07-05 18:24:40,292 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:24:40,292 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1afbd40> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-07-05 18:24:40,305 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1afbd40> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-07-05 18:24:40,305 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-05 18:24:40,305 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:24:40,305 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-07-05 18:24:40,305 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:24:40,305 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1afbd40> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-07-05 18:24:40,305 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1afbd40> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2012-07-05 18:24:40,306 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1afbd40> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-07-05 18:24:40,306 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1afbd40> about HardwareID('modalias', 'wmi:ABBC0F6A-8EA1-11D1-00A0-C90629100000')
2012-07-05 18:24:40,306 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1afbd40> about HardwareID('modalias', 'pci:v00001002d00009501sv0000174Bsd0000E620bc03sc00i00')
2012-07-05 18:24:40,566 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2012-07-05 18:24:40,566 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:24:40,566 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2012-07-05 18:24:40,611 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-07-05 18:24:40,611 DEBUG: fglrx_updates is not the alternative in use
2012-07-05 18:24:40,566 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-07-05 18:24:40,615 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-07-05 18:24:40,620 DEBUG: fglrx.available: falling back to default
2012-07-05 18:24:40,650 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-07-05 18:24:40,650 DEBUG: fglrx_updates is not the alternative in use
2012-07-05 18:24:40,637 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-07-05 18:24:40,650 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2012-07-05 18:24:40,663 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-07-05 18:24:40,663 DEBUG: fglrx is not the alternative in use
2012-07-05 18:24:40,650 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-07-05 18:24:40,666 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-07-05 18:24:40,671 DEBUG: fglrx.available: falling back to default
2012-07-05 18:24:40,719 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-07-05 18:24:40,719 DEBUG: fglrx is not the alternative in use
2012-07-05 18:24:40,693 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-07-05 18:24:40,719 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1afbd40> about HardwareID('modalias', 'pci:v00001002d00004383sv00001458sd0000A002bc04sc03i00')
2012-07-05 18:24:40,723 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-07-05 18:24:40,723 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:24:40,723 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-07-05 18:24:40,723 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:24:40,723 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1afbd40> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-07-05 18:24:40,723 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1afbd40> about HardwareID('modalias', 'acpi:PNP0800:')
2012-07-05 18:24:40,723 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1afbd40> about HardwareID('modalias', 'acpi:PNP0000:')
2012-07-05 18:24:40,723 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1afbd40> about HardwareID('modalias', 'pci:v00001002d0000AA18sv0000174Bsd0000AA18bc04sc03i00')
2012-07-05 18:24:40,726 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-07-05 18:24:40,727 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:24:40,727 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-07-05 18:24:40,727 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:24:40,727 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1afbd40> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001458sd00005002bc01sc01i8a')
2012-07-05 18:24:40,734 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pata_atiixp'}
2012-07-05 18:24:40,734 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_atiixp', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:24:40,734 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1afbd40> about HardwareID('modalias', 'acpi:PNP0100:')
2012-07-05 18:24:40,735 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1afbd40> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2012-07-05 18:24:40,749 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1afbd40> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2012-07-05 18:24:40,750 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1afbd40> about HardwareID('modalias', 'usb:v0461p4EBCd0104dc00dsc00dp00ic03isc01ip01')
2012-07-05 18:24:40,751 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-07-05 18:24:40,751 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:24:40,751 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2012-07-05 18:24:40,751 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:24:40,751 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1afbd40> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2012-07-05 18:24:40,752 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-05 18:24:40,752 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:24:40,752 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1afbd40> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-07-05 18:24:40,752 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-05 18:24:40,752 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:24:40,752 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1afbd40> about HardwareID('modalias', 'input:b0003v0461p4EBCe0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8C,8E,96,98,9E,9F,A1,A3,A4,A5,A6,AD,B0,B1,B2,B3,B4,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2012-07-05 18:24:40,752 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-05 18:24:40,752 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:24:40,752 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-07-05 18:24:40,753 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:24:40,753 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1afbd40> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2012-07-05 18:24:40,753 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1afbd40> about HardwareID('modalias', 'input:b0003v046DpC05Be0111-e0,1,2,4,k110,111,112,113,114,115,116,117,r0,1,6,8,am4,lsfw')
2012-07-05 18:24:40,753 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-05 18:24:40,753 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:24:40,753 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-07-05 18:24:40,753 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:24:40,753 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1afbd40> about HardwareID('modalias', 'dmi:bvnAwardSoftwareInternational,Inc.:bvrF10:bd03/22/2011:svnGigabyteTechnologyCo.,Ltd.:pnGA-MA770T-UD3:pvr:rvnGigabyteTechnologyCo.,Ltd.:rnGA-MA770T-UD3:rvr:cvnGigabyteTechnologyCo.,Ltd.:ct3:cvr:')
2012-07-05 18:24:40,766 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1afbd40> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-07-05 18:24:40,767 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1afbd40> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2012-07-05 18:24:40,767 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'amd64_edac_mod'}
2012-07-05 18:24:40,767 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'amd64_edac_mod', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:24:40,767 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1afbd40> about HardwareID('modalias', 'input:b0003v0461p4EBCe0110-e0,1,4,k71,72,73,74,80,8C,8E,8F,90,9B,9C,9E,9F,A1,A3,A4,A5,A6,AB,AC,AD,D9,ram4,lsfw')
2012-07-05 18:24:40,767 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-05 18:24:40,767 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:24:40,767 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-07-05 18:24:40,767 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:24:40,767 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1afbd40> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-07-05 18:24:40,768 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1afbd40> about HardwareID('modalias', 'usb:v1B1Cp0AB1d0100dc00dsc00dp00ic08isc06ip50')
2012-07-05 18:24:40,768 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uas'}
2012-07-05 18:24:40,768 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uas', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:24:40,768 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1afbd40> about HardwareID('modalias', 'pci:v00001002d00004396sv00001458sd00005004bc0Csc03i20')
2012-07-05 18:24:40,779 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1afbd40> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-07-05 18:24:40,779 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-05 18:24:40,779 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:24:40,779 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1afbd40> about HardwareID('modalias', 'pci:v00001002d00004390sv00001458sd0000B002bc01sc06i01')
2012-07-05 18:24:40,790 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1afbd40> about HardwareID('modalias', 'usb:v0461p4EBCd0104dc00dsc00dp00ic03isc00ip00')
2012-07-05 18:24:40,791 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-07-05 18:24:40,791 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:24:40,791 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1afbd40> about HardwareID('modalias', 'pci:v00001002d00005957sv00001002sd00005957bc06sc00i00')
2012-07-05 18:24:40,794 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1afbd40> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-07-05 18:24:40,794 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1afbd40> about HardwareID('modalias', 'usb:v046DpC05Bd5400dc00dsc00dp00ic03isc01ip02')
2012-07-05 18:24:40,826 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-07-05 18:24:40,827 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:24:40,827 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2012-07-05 18:24:40,827 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:24:40,827 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1afbd40> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2012-07-05 18:24:40,827 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'k10temp'}
2012-07-05 18:24:40,827 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k10temp', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:24:40,827 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1afbd40> about HardwareID('modalias', 'pci:v00001002d00004385sv00001458sd00004385bc0Csc05i00')
2012-07-05 18:24:40,832 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4'}
2012-07-05 18:24:40,832 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:24:40,832 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco'}
2012-07-05 18:24:40,832 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:24:40,832 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1afbd40> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-07-05 18:24:40,836 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1afbd40> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2012-07-05 18:24:40,843 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-07-05 18:24:40,844 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:24:40,844 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1afbd40> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2012-07-05 18:24:40,844 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-05 18:24:40,844 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:24:40,844 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1afbd40> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001002sd0000439Dbc06sc01i00')
2012-07-05 18:24:40,847 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1afbd40> about HardwareID('modalias', 'acpi:PNP0200:')
2012-07-05 18:24:40,847 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e6b290> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-07-05 18:24:40,847 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e6b290> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2012-07-05 18:24:40,847 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e6b290> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-07-05 18:24:40,847 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e6b290> about HardwareID('modalias', 'acpi:PNP0103:')
2012-07-05 18:24:40,848 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e6b290> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001458sd0000E000bc02sc00i00')
2012-07-05 18:24:40,848 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e6b290> about HardwareID('modalias', 'platform:pcspkr')
2012-07-05 18:24:40,848 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e6b290> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-07-05 18:24:40,848 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e6b290> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-07-05 18:24:40,848 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e6b290> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-07-05 18:24:40,848 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e6b290> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2012-07-05 18:24:40,848 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e6b290> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-07-05 18:24:40,848 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e6b290> about HardwareID('modalias', 'wmi:ABBC0F6A-8EA1-11D1-00A0-C90629100000')
2012-07-05 18:24:40,848 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e6b290> about HardwareID('modalias', 'pci:v00001002d00009501sv0000174Bsd0000E620bc03sc00i00')
2012-07-05 18:24:40,848 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e6b290> about HardwareID('modalias', 'pci:v00001002d00004383sv00001458sd0000A002bc04sc03i00')
2012-07-05 18:24:40,848 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e6b290> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-07-05 18:24:40,848 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e6b290> about HardwareID('modalias', 'acpi:PNP0800:')
2012-07-05 18:24:40,848 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e6b290> about HardwareID('modalias', 'acpi:PNP0000:')
2012-07-05 18:24:40,848 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e6b290> about HardwareID('modalias', 'pci:v00001002d0000AA18sv0000174Bsd0000AA18bc04sc03i00')
2012-07-05 18:24:40,848 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e6b290> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001458sd00005002bc01sc01i8a')
2012-07-05 18:24:40,860 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e6b290> about HardwareID('modalias', 'acpi:PNP0100:')
2012-07-05 18:24:40,861 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e6b290> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2012-07-05 18:24:40,861 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e6b290> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2012-07-05 18:24:40,861 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e6b290> about HardwareID('modalias', 'usb:v0461p4EBCd0104dc00dsc00dp00ic03isc01ip01')
2012-07-05 18:24:40,861 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e6b290> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2012-07-05 18:24:40,861 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e6b290> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-07-05 18:24:40,861 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e6b290> about HardwareID('modalias', 'input:b0003v0461p4EBCe0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8C,8E,96,98,9E,9F,A1,A3,A4,A5,A6,AD,B0,B1,B2,B3,B4,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2012-07-05 18:24:40,861 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e6b290> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2012-07-05 18:24:40,861 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e6b290> about HardwareID('modalias', 'input:b0003v046DpC05Be0111-e0,1,2,4,k110,111,112,113,114,115,116,117,r0,1,6,8,am4,lsfw')
2012-07-05 18:24:40,861 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e6b290> about HardwareID('modalias', 'dmi:bvnAwardSoftwareInternational,Inc.:bvrF10:bd03/22/2011:svnGigabyteTechnologyCo.,Ltd.:pnGA-MA770T-UD3:pvr:rvnGigabyteTechnologyCo.,Ltd.:rnGA-MA770T-UD3:rvr:cvnGigabyteTechnologyCo.,Ltd.:ct3:cvr:')
2012-07-05 18:24:40,861 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e6b290> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-07-05 18:24:40,861 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e6b290> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2012-07-05 18:24:40,861 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e6b290> about HardwareID('modalias', 'input:b0003v0461p4EBCe0110-e0,1,4,k71,72,73,74,80,8C,8E,8F,90,9B,9C,9E,9F,A1,A3,A4,A5,A6,AB,AC,AD,D9,ram4,lsfw')
2012-07-05 18:24:40,861 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e6b290> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-07-05 18:24:40,861 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e6b290> about HardwareID('modalias', 'usb:v1B1Cp0AB1d0100dc00dsc00dp00ic08isc06ip50')
2012-07-05 18:24:40,861 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e6b290> about HardwareID('modalias', 'pci:v00001002d00004396sv00001458sd00005004bc0Csc03i20')
2012-07-05 18:24:40,861 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e6b290> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-07-05 18:24:40,861 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e6b290> about HardwareID('modalias', 'pci:v00001002d00004390sv00001458sd0000B002bc01sc06i01')
2012-07-05 18:24:40,861 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e6b290> about HardwareID('modalias', 'usb:v0461p4EBCd0104dc00dsc00dp00ic03isc00ip00')
2012-07-05 18:24:40,862 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e6b290> about HardwareID('modalias', 'pci:v00001002d00005957sv00001002sd00005957bc06sc00i00')
2012-07-05 18:24:40,862 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e6b290> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-07-05 18:24:40,862 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e6b290> about HardwareID('modalias', 'usb:v046DpC05Bd5400dc00dsc00dp00ic03isc01ip02')
2012-07-05 18:24:40,862 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e6b290> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2012-07-05 18:24:40,862 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e6b290> about HardwareID('modalias', 'pci:v00001002d00004385sv00001458sd00004385bc0Csc05i00')
2012-07-05 18:24:40,862 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e6b290> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-07-05 18:24:40,862 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e6b290> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2012-07-05 18:24:40,862 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e6b290> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2012-07-05 18:24:40,862 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e6b290> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001002sd0000439Dbc06sc01i00')
2012-07-05 18:24:40,862 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e6b290> about HardwareID('modalias', 'acpi:PNP0200:')
2012-07-05 18:24:40,904 DEBUG: handler xorg:fglrx_updates previously unseen
2012-07-05 18:24:40,905 DEBUG: handler xorg:fglrx previously unseen
2012-07-05 18:24:40,905 DEBUG: writing back check cache /var/cache/jockey/check
2012-07-05 18:24:40,918 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-07-05 18:24:40,918 DEBUG: fglrx_updates is not the alternative in use
2012-07-05 18:24:40,931 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-07-05 18:24:40,931 DEBUG: fglrx is not the alternative in use
2012-07-05 18:24:40,953 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-07-05 18:24:40,953 DEBUG: fglrx_updates is not the alternative in use
2012-07-05 18:24:48,546 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-07-05 18:24:48,547 DEBUG: fglrx_updates is not the alternative in use
2012-07-05 18:24:48,662 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-07-05 18:24:48,663 DEBUG: fglrx is not the alternative in use
2012-07-05 18:24:48,723 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-07-05 18:24:48,724 DEBUG: fglrx_updates is not the alternative in use
2012-07-05 18:24:48,807 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-07-05 18:24:48,808 DEBUG: fglrx_updates is not the alternative in use
2012-07-05 18:24:48,862 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-07-05 18:24:48,863 DEBUG: fglrx is not the alternative in use
2012-07-05 18:24:57,552 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-07-05 18:24:57,552 DEBUG: fglrx_updates is not the alternative in use
2012-07-05 18:25:05,119 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-07-05 18:25:05,119 DEBUG: fglrx_updates is not the alternative in use
2012-07-05 18:25:13,612 DEBUG: Installing package: fglrx-updates
2012-07-05 18:25:14,292 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 0.000000
2012-07-05 18:25:14,297 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 0.000000
2012-07-05 18:25:14,383 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 0.000000
2012-07-05 18:25:14,419 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 0.000000
2012-07-05 18:25:14,478 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 0.001542
2012-07-05 18:25:14,665 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 0.104421
2012-07-05 18:25:14,666 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 0.104421
2012-07-05 18:25:14,701 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 0.104421
2012-07-05 18:25:14,775 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 0.105963
2012-07-05 18:25:14,927 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 0.199585
2012-07-05 18:25:14,928 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 0.199585
2012-07-05 18:25:14,962 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 0.199585
2012-07-05 18:25:15,029 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 0.201127
2012-07-05 18:25:15,203 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 0.313163
2012-07-05 18:25:15,204 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 0.313163
2012-07-05 18:25:15,238 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 0.313163
2012-07-05 18:25:15,293 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 0.314706
2012-07-05 18:25:15,795 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 0.802331
2012-07-05 18:25:16,296 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 1.169926
2012-07-05 18:25:16,797 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 1.507513
2012-07-05 18:25:17,299 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 1.858228
2012-07-05 18:25:17,800 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 2.169558
2012-07-05 18:25:18,301 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 2.539028
2012-07-05 18:25:18,802 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 3.049159
2012-07-05 18:25:19,304 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 3.643687
2012-07-05 18:25:19,805 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 4.324487
2012-07-05 18:25:20,306 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 4.960276
2012-07-05 18:25:20,751 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 5.520240
2012-07-05 18:25:20,751 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 5.520240
2012-07-05 18:25:20,787 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 5.520240
2012-07-05 18:25:20,838 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 5.520240
2012-07-05 18:25:20,967 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 5.590671
2012-07-05 18:25:20,970 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 5.590671
2012-07-05 18:25:21,006 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 5.590671
2012-07-05 18:25:21,066 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 5.590671
2012-07-05 18:25:21,567 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 6.014190
2012-07-05 18:25:22,068 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 6.428672
2012-07-05 18:25:22,570 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 6.770009
2012-07-05 18:25:23,071 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 7.154483
2012-07-05 18:25:23,572 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 7.527704
2012-07-05 18:25:24,074 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 7.902801
2012-07-05 18:25:24,575 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 8.326660
2012-07-05 18:25:25,076 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 8.874300
2012-07-05 18:25:25,577 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 9.360050
2012-07-05 18:25:26,079 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 9.671380
2012-07-05 18:25:26,580 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 10.033349
2012-07-05 18:25:27,081 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 10.372811
2012-07-05 18:25:27,582 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 10.734779
2012-07-05 18:25:28,084 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 11.072366
2012-07-05 18:25:28,585 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 11.379945
2012-07-05 18:25:29,086 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 11.796302
2012-07-05 18:25:29,588 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 12.362698
2012-07-05 18:25:30,089 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 13.069754
2012-07-05 18:25:30,590 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 13.707418
2012-07-05 18:25:31,091 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 14.346958
2012-07-05 18:25:31,593 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 14.986497
2012-07-05 18:25:32,094 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 15.626037
2012-07-05 18:25:32,595 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 16.263701
2012-07-05 18:25:33,096 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 16.901365
2012-07-05 18:25:33,597 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 17.540904
2012-07-05 18:25:34,099 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 18.172942
2012-07-05 18:25:34,600 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 18.812481
2012-07-05 18:25:35,102 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 19.380752
2012-07-05 18:25:35,603 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 19.911514
2012-07-05 18:25:36,104 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 20.224720
2012-07-05 18:25:36,606 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 20.483536
2012-07-05 18:25:37,107 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 20.779862
2012-07-05 18:25:37,608 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 21.338756
2012-07-05 18:25:38,110 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 21.959541
2012-07-05 18:25:38,611 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 22.580325
2012-07-05 18:25:39,113 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 23.216114
2012-07-05 18:25:39,614 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 23.855653
2012-07-05 18:25:40,115 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 24.478313
2012-07-05 18:25:40,617 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 25.018452
2012-07-05 18:25:41,118 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 25.536085
2012-07-05 18:25:41,619 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 26.093104
2012-07-05 18:25:42,121 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 26.620114
2012-07-05 18:25:42,622 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 27.120868
2012-07-05 18:25:43,123 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 27.638501
2012-07-05 18:25:43,651 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 28.229278
2012-07-05 18:25:44,153 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 28.715028
2012-07-05 18:25:44,654 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 29.099502
2012-07-05 18:25:45,155 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 29.523361
2012-07-05 18:25:45,657 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 30.076628
2012-07-05 18:25:46,158 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 30.716168
2012-07-05 18:25:46,659 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 31.305069
2012-07-05 18:25:47,160 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 31.768313
2012-07-05 18:25:47,662 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 32.096523
2012-07-05 18:25:48,163 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 32.441611
2012-07-05 18:25:48,664 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 32.835463
2012-07-05 18:25:49,166 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 33.369975
2012-07-05 18:25:49,667 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 34.071406
2012-07-05 18:25:50,168 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 34.622797
2012-07-05 18:25:50,670 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 35.221076
2012-07-05 18:25:51,171 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 35.845612
2012-07-05 18:25:51,672 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 36.485151
2012-07-05 18:25:52,174 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 37.122815
2012-07-05 18:25:52,675 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 37.764230
2012-07-05 18:25:53,178 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 38.278112
2012-07-05 18:25:53,679 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 38.655084
2012-07-05 18:25:54,181 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 39.063939
2012-07-05 18:25:54,682 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 39.579697
2012-07-05 18:25:55,183 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 40.204233
2012-07-05 18:25:55,685 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 40.458305
2012-07-05 18:25:56,186 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 41.350152
2012-07-05 18:25:56,687 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 41.989692
2012-07-05 18:25:57,188 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 42.629231
2012-07-05 18:25:57,689 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 43.266895
2012-07-05 18:25:58,190 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 43.855797
2012-07-05 18:25:58,692 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 44.392185
2012-07-05 18:25:59,193 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 44.915444
2012-07-05 18:25:59,694 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 45.461210
2012-07-05 18:26:00,196 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 46.046360
2012-07-05 18:26:00,697 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 46.562118
2012-07-05 18:26:01,198 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 47.319813
2012-07-05 18:26:01,700 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 47.955601
2012-07-05 18:26:02,201 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 48.587639
2012-07-05 18:26:02,702 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 49.229054
2012-07-05 18:26:03,204 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 49.772944
2012-07-05 18:26:03,705 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 50.320584
2012-07-05 18:26:04,206 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 50.765074
2012-07-05 18:26:04,707 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 51.192684
2012-07-05 18:26:05,209 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 51.655928
2012-07-05 18:26:05,710 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 52.263584
2012-07-05 18:26:06,211 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 52.691194
2012-07-05 18:26:06,713 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 52.998773
2012-07-05 18:26:07,214 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 53.415130
2012-07-05 18:26:07,715 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 54.000281
2012-07-05 18:26:08,216 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 54.557299
2012-07-05 18:26:08,718 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 55.131197
2012-07-05 18:26:09,219 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 55.643203
2012-07-05 18:26:09,720 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 56.196471
2012-07-05 18:26:10,222 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 56.760991
2012-07-05 18:26:10,723 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 57.393028
2012-07-05 18:26:11,224 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 57.833767
2012-07-05 18:26:11,726 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 58.124466
2012-07-05 18:26:12,227 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 58.433921
2012-07-05 18:26:12,728 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 58.745251
2012-07-05 18:26:13,230 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 59.090340
2012-07-05 18:26:13,731 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 59.420425
2012-07-05 18:26:14,232 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 59.681117
2012-07-05 18:26:14,733 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 59.951186
2012-07-05 18:26:15,235 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 60.361917
2012-07-05 18:26:15,736 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 60.977075
2012-07-05 18:26:16,238 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 61.577229
2012-07-05 18:26:16,739 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 62.175508
2012-07-05 18:26:17,240 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 62.801919
2012-07-05 18:26:17,742 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 63.437708
2012-07-05 18:26:18,243 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 64.077247
2012-07-05 18:26:18,744 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 64.714911
2012-07-05 18:26:19,246 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 65.352575
2012-07-05 18:26:19,747 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 65.992115
2012-07-05 18:26:20,248 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 66.554759
2012-07-05 18:26:20,750 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 66.995498
2012-07-05 18:26:21,251 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 67.370594
2012-07-05 18:26:21,752 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 67.740064
2012-07-05 18:26:22,254 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 68.118912
2012-07-05 18:26:22,755 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 68.554024
2012-07-05 18:26:23,257 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 69.009766
2012-07-05 18:26:23,758 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 69.594916
2012-07-05 18:26:24,259 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 70.256962
2012-07-05 18:26:24,761 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 70.834610
2012-07-05 18:26:25,262 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 71.429138
2012-07-05 18:26:25,763 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 72.063051
2012-07-05 18:26:26,265 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 72.213090
2012-07-05 18:26:26,766 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 73.182714
2012-07-05 18:26:27,267 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 73.672215
2012-07-05 18:26:27,769 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 74.082945
2012-07-05 18:26:28,270 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 74.474921
2012-07-05 18:26:28,771 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 74.790002
2012-07-05 18:26:29,274 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 75.125714
2012-07-05 18:26:29,775 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 75.483931
2012-07-05 18:26:30,276 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 75.808389
2012-07-05 18:26:30,777 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 76.067206
2012-07-05 18:26:31,279 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 76.404793
2012-07-05 18:26:31,780 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 76.920550
2012-07-05 18:26:32,282 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 77.263763
2012-07-05 18:26:32,783 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 77.516954
2012-07-05 18:26:33,284 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 78.047715
2012-07-05 18:26:33,785 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 78.640368
2012-07-05 18:26:34,287 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 79.054849
2012-07-05 18:26:34,788 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 79.390560
2012-07-05 18:26:35,289 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 79.730023
2012-07-05 18:26:35,791 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 80.041353
2012-07-05 18:26:36,292 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 80.388317
2012-07-05 18:26:36,793 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 80.763414
2012-07-05 18:26:37,295 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 81.329809
2012-07-05 18:26:37,796 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 81.969349
2012-07-05 18:26:38,297 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 82.608888
2012-07-05 18:26:38,799 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 83.248428
2012-07-05 18:26:39,300 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 83.884216
2012-07-05 18:26:39,801 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 84.525631
2012-07-05 18:26:40,303 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 85.163295
2012-07-05 18:26:40,804 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 85.804710
2012-07-05 18:26:41,305 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 86.442374
2012-07-05 18:26:41,807 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 87.081913
2012-07-05 18:26:42,308 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 87.702698
2012-07-05 18:26:42,809 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 88.340362
2012-07-05 18:26:43,310 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 88.974275
2012-07-05 18:26:43,812 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 89.533169
2012-07-05 18:26:44,313 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 90.097689
2012-07-05 18:26:44,814 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 90.703470
2012-07-05 18:26:45,316 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 91.331756
2012-07-05 18:26:45,817 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 91.971296
2012-07-05 18:26:46,062 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 92.284541
2012-07-05 18:26:46,063 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 92.284541
2012-07-05 18:26:46,097 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 92.284541
2012-07-05 18:26:46,161 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 92.284541
2012-07-05 18:26:46,662 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 92.709938
2012-07-05 18:26:47,163 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 93.170102
2012-07-05 18:26:47,664 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 93.677687
2012-07-05 18:26:48,166 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 94.238456
2012-07-05 18:26:48,667 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 94.797350
2012-07-05 18:26:49,168 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 95.421885
2012-07-05 18:26:49,670 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 95.840118
2012-07-05 18:26:50,171 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 96.427144
2012-07-05 18:26:50,672 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 96.959781
2012-07-05 18:26:51,174 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 97.287990
2012-07-05 18:26:51,675 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 97.664962
2012-07-05 18:26:52,176 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 98.115078
2012-07-05 18:26:52,678 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 98.752742
2012-07-05 18:26:53,179 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 99.394157
2012-07-05 18:26:53,654 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 100.000000
2012-07-05 18:26:54,810 DEBUG: install progress dpkg-exec 0.000000
2012-07-05 18:26:56,438 DEBUG: install progress patch 0.000000
2012-07-05 18:26:56,546 DEBUG: install progress patch 2.857140
2012-07-05 18:26:57,013 DEBUG: install progress patch 5.714290
2012-07-05 18:26:57,128 DEBUG: install progress patch 8.571430
2012-07-05 18:26:57,503 DEBUG: install progress dkms 8.571430
2012-07-05 18:26:57,604 DEBUG: install progress dkms 11.428600
2012-07-05 18:26:58,029 DEBUG: install progress dkms 14.285700
2012-07-05 18:26:58,118 DEBUG: install progress dkms 17.142900
2012-07-05 18:26:58,473 DEBUG: install progress fakeroot 17.142900
2012-07-05 18:26:58,574 DEBUG: install progress fakeroot 20.000000
2012-07-05 18:26:58,883 DEBUG: install progress fakeroot 22.857100
2012-07-05 18:26:58,966 DEBUG: install progress fakeroot 25.714300
2012-07-05 18:26:59,469 DEBUG: install progress libc6-i386 25.714300
2012-07-05 18:26:59,570 DEBUG: install progress libc6-i386 28.571400
2012-07-05 18:27:00,360 DEBUG: install progress libc6-i386 31.428600
2012-07-05 18:27:00,467 DEBUG: install progress libc6-i386 34.285700
2012-07-05 18:27:01,772 DEBUG: install progress lib32gcc1 34.285700
2012-07-05 18:27:01,873 DEBUG: install progress lib32gcc1 37.142900
2012-07-05 18:27:02,051 DEBUG: install progress lib32gcc1 40.000000
2012-07-05 18:27:02,134 DEBUG: install progress lib32gcc1 42.857100
2012-07-05 18:27:02,711 DEBUG: install progress fglrx-updates 42.857100
2012-07-05 18:27:02,712 DEBUG: install progress fglrx-updates 45.714300
2012-07-05 18:27:07,511 DEBUG: install progress fglrx-updates 48.571400
2012-07-05 18:27:07,617 DEBUG: install progress fglrx-updates 51.428600
2012-07-05 18:27:07,883 DEBUG: install progress fglrx-amdcccle-updates 51.428600
2012-07-05 18:27:07,984 DEBUG: install progress fglrx-amdcccle-updates 54.285700
2012-07-05 18:27:08,462 DEBUG: install progress fglrx-amdcccle-updates 57.142900
2012-07-05 18:27:08,526 DEBUG: install progress fglrx-amdcccle-updates 60.000000
2012-07-05 18:27:08,601 DEBUG: install progress man-db 60.000000
2012-07-05 18:27:12,014 DEBUG: install progress ureadahead 60.000000
2012-07-05 18:27:12,365 DEBUG: install progress dpkg-exec 60.000000
2012-07-05 18:27:12,402 DEBUG: install progress patch 60.000000
2012-07-05 18:27:12,472 DEBUG: install progress patch 62.857100
2012-07-05 18:27:12,539 DEBUG: install progress patch 65.714300
2012-07-05 18:27:12,607 DEBUG: install progress dkms 65.714300
2012-07-05 18:27:13,770 DEBUG: install progress dkms 68.571400
2012-07-05 18:27:13,845 DEBUG: install progress dkms 71.428600
2012-07-05 18:27:13,922 DEBUG: install progress fakeroot 71.428600
2012-07-05 18:27:13,990 DEBUG: install progress fakeroot 74.285700
2012-07-05 18:27:14,489 DEBUG: install progress fakeroot 77.142900
2012-07-05 18:27:14,572 DEBUG: install progress libc6-i386 77.142900
2012-07-05 18:27:14,716 DEBUG: install progress libc6-i386 80.000000
2012-07-05 18:27:14,860 DEBUG: install progress libc6-i386 82.857100
2012-07-05 18:27:15,046 DEBUG: install progress lib32gcc1 82.857100
2012-07-05 18:27:15,113 DEBUG: install progress lib32gcc1 85.714300
2012-07-05 18:27:15,249 DEBUG: install progress lib32gcc1 88.571400
2012-07-05 18:27:15,333 DEBUG: install progress fglrx-updates 88.571400
2012-07-05 18:27:15,673 DEBUG: install progress fglrx-updates 91.428600
2012-07-05 18:27:48,579 DEBUG: install progress fglrx-updates 94.285700
2012-07-05 18:27:48,959 DEBUG: install progress bamfdaemon 94.285700
2012-07-05 18:27:49,295 DEBUG: install progress fglrx-amdcccle-updates 94.285700
2012-07-05 18:27:49,404 DEBUG: install progress fglrx-amdcccle-updates 97.142900
2012-07-05 18:27:49,523 DEBUG: install progress fglrx-amdcccle-updates 100.000000
2012-07-05 18:27:49,633 DEBUG: install progress libc-bin 100.000000
2012-07-05 18:27:49,945 DEBUG: install progress initramfs-tools 100.000000
2012-07-05 18:28:06,897 DEBUG: Selecting previously unselected package patch.
(Reading database ... 143241 files and directories currently installed.)
Unpacking patch (from .../patch_2.6.1-3_amd64.deb) ...
Selecting previously unselected package dkms.
Unpacking dkms (from .../dkms_2.2.0.3-1ubuntu3_all.deb) ...
Selecting previously unselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.18.2-1_amd64.deb) ...
Selecting previously unselected package libc6-i386.
Unpacking libc6-i386 (from .../libc6-i386_2.15-0ubuntu10_amd64.deb) ...
Selecting previously unselected package lib32gcc1.
Unpacking lib32gcc1 (from .../lib32gcc1_1%3a4.6.3-1ubuntu5_amd64.deb) ...
Selecting previously unselected package fglrx-updates.
Unpacking fglrx-updates (from .../fglrx-updates_2%3a8.960-0ubuntu1_amd64.deb) ...
Selecting previously unselected package fglrx-amdcccle-updates.
Unpacking fglrx-amdcccle-updates (from .../fglrx-amdcccle-updates_2%3a8.960-0ubuntu1_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up patch (2.6.1-3) ...
Setting up dkms (2.2.0.3-1ubuntu3) ...
Setting up fakeroot (1.18.2-1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode.
Setting up libc6-i386 (2.15-0ubuntu10) ...
Setting up lib32gcc1 (1:4.6.3-1ubuntu5) ...
Setting up fglrx-updates (2:8.960-0ubuntu1) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl32.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl32.icd (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: using /usr/lib/fglrx/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
Loading new fglrx-updates-8.960 DKMS files...
First Installation: checking all kernels...
Building only for 3.2.0-23-generic
Building for architecture x86_64
Building initial module for 3.2.0-23-generic
Done.

fglrx_updates:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-23-generic/updates/dkms/

depmod.......

DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Setting up fglrx-amdcccle-updates (2:8.960-0ubuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-23-generic

2012-07-05 18:28:07,110 WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver
2012-07-05 18:28:30,026 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:28:30,027 DEBUG: fglrx_updates is not the alternative in use
2012-07-05 18:28:30,066 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:28:30,066 DEBUG: fglrx_updates is not the alternative in use
2012-07-05 18:28:40,827 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:28:40,827 DEBUG: fglrx_updates is not the alternative in use
2012-07-05 18:28:40,865 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:28:40,866 DEBUG: fglrx_updates is not the alternative in use
2012-07-05 18:28:40,934 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:28:40,935 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-07-05 18:28:41,006 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:28:41,007 DEBUG: fglrx_updates is not the alternative in use
2012-07-05 18:28:41,050 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:28:41,051 DEBUG: fglrx_updates is not the alternative in use
2012-07-05 18:28:41,153 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:28:41,153 DEBUG: fglrx_updates is not the alternative in use
2012-07-05 18:28:41,191 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:28:41,192 DEBUG: fglrx_updates is not the alternative in use
2012-07-05 18:28:41,255 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:28:41,255 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-07-05 18:28:43,622 DEBUG: Shutting down
2012-07-05 18:45:37,115 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f72cf8>
2012-07-05 18:45:42,505 DEBUG: reading modalias file /lib/modules/3.2.0-26-generic/modules.alias
2012-07-05 18:45:42,651 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-07-05 18:45:42,658 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-07-05 18:45:42,768 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2012-07-05 18:45:42,825 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2012-07-05 18:45:42,825 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2012-07-05 18:45:42,889 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2012-07-05 18:45:42,890 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-07-05 18:45:42,963 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2012-07-05 18:45:42,964 DEBUG: fglrx.available: falling back to default
2012-07-05 18:45:43,171 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2012-07-05 18:45:43,180 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-07-05 18:45:43,191 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-07-05 18:45:43,192 DEBUG: fglrx.available: falling back to default
2012-07-05 18:45:43,228 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-07-05 18:45:43,228 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-07-05 18:45:43,342 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-07-05 18:45:43,343 DEBUG: Firmware for DVB cards not available
2012-07-05 18:45:43,343 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-07-05 18:45:43,359 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-07-05 18:45:43,370 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-07-05 18:45:43,374 DEBUG: nvidia.available: falling back to default
2012-07-05 18:45:43,400 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-07-05 18:45:43,400 DEBUG: NVIDIA accelerated graphics driver not available
2012-07-05 18:45:43,404 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-07-05 18:45:43,414 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-07-05 18:45:43,414 DEBUG: nvidia.available: falling back to default
2012-07-05 18:45:43,491 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-07-05 18:45:43,500 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-07-05 18:45:43,508 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2012-07-05 18:45:43,509 DEBUG: nvidia.available: falling back to default
2012-07-05 18:45:43,584 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-07-05 18:45:43,594 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-07-05 18:45:43,605 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2012-07-05 18:45:43,607 DEBUG: nvidia.available: falling back to default
2012-07-05 18:45:43,645 DEBUG: XorgDriverHandler(nvidia_173_updates, nvidia-173-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-07-05 18:45:43,646 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-07-05 18:45:43,654 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-07-05 18:45:43,665 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-07-05 18:45:43,667 DEBUG: nvidia.available: falling back to default
2012-07-05 18:45:43,705 DEBUG: XorgDriverHandler(nvidia_173, nvidia-173, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-07-05 18:45:43,706 DEBUG: NVIDIA accelerated graphics driver not available
2012-07-05 18:45:43,712 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2012-07-05 18:45:43,720 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2012-07-05 18:45:43,721 DEBUG: nvidia.available: falling back to default
2012-07-05 18:45:43,759 DEBUG: XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-07-05 18:45:43,759 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-07-05 18:45:43,760 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-07-05 18:45:43,770 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-07-05 18:45:43,771 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-07-05 18:45:43,771 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-07-05 18:45:43,772 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-07-05 18:45:43,782 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-07-05 18:45:43,817 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-07-05 18:45:43,818 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-07-05 18:45:43,818 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2012-07-05 18:45:43,831 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2012-07-05 18:45:43,843 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2012-07-05 18:45:43,894 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2012-07-05 18:45:43,895 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-07-05 18:45:43,926 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-07-05 18:45:43,958 DEBUG: Software modem not available
2012-07-05 18:45:43,958 DEBUG: all custom handlers loaded
2012-07-05 18:45:43,958 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f72cf8> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-07-05 18:45:43,959 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f72cf8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2012-07-05 18:45:43,973 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-05 18:45:44,116 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:45:44,116 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f72cf8> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-07-05 18:45:44,116 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f72cf8> about HardwareID('modalias', 'acpi:PNP0103:')
2012-07-05 18:45:44,116 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f72cf8> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001458sd0000E000bc02sc00i00')
2012-07-05 18:45:44,126 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2012-07-05 18:45:44,126 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:45:44,126 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f72cf8> about HardwareID('modalias', 'platform:pcspkr')
2012-07-05 18:45:44,127 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2012-07-05 18:45:44,127 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:45:44,127 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2012-07-05 18:45:44,127 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:45:44,127 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f72cf8> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-07-05 18:45:44,140 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f72cf8> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-07-05 18:45:44,140 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-05 18:45:44,140 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:45:44,140 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-07-05 18:45:44,140 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:45:44,140 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f72cf8> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-07-05 18:45:44,140 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f72cf8> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2012-07-05 18:45:44,141 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f72cf8> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-07-05 18:45:44,141 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f72cf8> about HardwareID('modalias', 'wmi:ABBC0F6A-8EA1-11D1-00A0-C90629100000')
2012-07-05 18:45:44,141 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f72cf8> about HardwareID('modalias', 'pci:v00001002d00009501sv0000174Bsd0000E620bc03sc00i00')
2012-07-05 18:45:44,408 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2012-07-05 18:45:44,408 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:45:44,408 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates'}
2012-07-05 18:45:44,503 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:45:44,504 DEBUG: fglrx_updates is not the alternative in use
2012-07-05 18:45:44,408 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-07-05 18:45:44,516 DEBUG: fglrx.available: falling back to default
2012-07-05 18:45:44,572 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:45:44,572 DEBUG: fglrx_updates is not the alternative in use
2012-07-05 18:45:44,544 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-07-05 18:45:44,573 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2012-07-05 18:45:44,604 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:45:44,605 DEBUG: fglrx_updates is not the alternative in use
2012-07-05 18:45:44,573 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-07-05 18:45:44,616 DEBUG: fglrx.available: falling back to default
2012-07-05 18:45:44,658 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:45:44,658 DEBUG: fglrx_updates is not the alternative in use
2012-07-05 18:45:44,640 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-07-05 18:45:44,659 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2012-07-05 18:45:44,683 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:45:44,683 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-07-05 18:45:44,659 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-07-05 18:45:44,691 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-07-05 18:45:44,703 DEBUG: fglrx.available: falling back to default
2012-07-05 18:45:44,764 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:45:44,765 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-07-05 18:45:44,737 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-07-05 18:45:44,765 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f72cf8> about HardwareID('modalias', 'pci:v00001002d00004383sv00001458sd0000A002bc04sc03i00')
2012-07-05 18:45:44,777 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-07-05 18:45:44,778 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:45:44,778 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-07-05 18:45:44,778 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:45:44,779 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f72cf8> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-07-05 18:45:44,779 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f72cf8> about HardwareID('modalias', 'acpi:PNP0800:')
2012-07-05 18:45:44,779 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f72cf8> about HardwareID('modalias', 'acpi:PNP0000:')
2012-07-05 18:45:44,779 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f72cf8> about HardwareID('modalias', 'pci:v00001002d0000AA18sv0000174Bsd0000AA18bc04sc03i00')
2012-07-05 18:45:44,786 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-07-05 18:45:44,786 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:45:44,786 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-07-05 18:45:44,786 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:45:44,786 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f72cf8> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001458sd00005002bc01sc01i8a')
2012-07-05 18:45:44,790 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pata_atiixp'}
2012-07-05 18:45:44,790 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_atiixp', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:45:44,790 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f72cf8> about HardwareID('modalias', 'acpi:PNP0100:')
2012-07-05 18:45:44,790 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f72cf8> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2012-07-05 18:45:44,801 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f72cf8> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2012-07-05 18:45:44,801 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f72cf8> about HardwareID('modalias', 'usb:v0461p4EBCd0104dc00dsc00dp00ic03isc01ip01')
2012-07-05 18:45:44,803 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-07-05 18:45:44,803 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:45:44,803 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2012-07-05 18:45:44,803 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:45:44,803 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f72cf8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2012-07-05 18:45:44,803 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-05 18:45:44,803 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:45:44,803 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f72cf8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-07-05 18:45:44,803 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-05 18:45:44,804 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:45:44,804 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f72cf8> about HardwareID('modalias', 'input:b0003v0461p4EBCe0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8C,8E,96,98,9E,9F,A1,A3,A4,A5,A6,AD,B0,B1,B2,B3,B4,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2012-07-05 18:45:44,804 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-05 18:45:44,804 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:45:44,804 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-07-05 18:45:44,804 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:45:44,804 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f72cf8> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2012-07-05 18:45:44,804 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f72cf8> about HardwareID('modalias', 'input:b0003v046DpC05Be0111-e0,1,2,4,k110,111,112,113,114,115,116,117,r0,1,6,8,am4,lsfw')
2012-07-05 18:45:44,804 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-05 18:45:44,804 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:45:44,805 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-07-05 18:45:44,805 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:45:44,805 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f72cf8> about HardwareID('modalias', 'dmi:bvnAwardSoftwareInternational,Inc.:bvrF10:bd03/22/2011:svnGigabyteTechnologyCo.,Ltd.:pnGA-MA770T-UD3:pvr:rvnGigabyteTechnologyCo.,Ltd.:rnGA-MA770T-UD3:rvr:cvnGigabyteTechnologyCo.,Ltd.:ct3:cvr:')
2012-07-05 18:45:44,818 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f72cf8> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-07-05 18:45:44,818 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f72cf8> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2012-07-05 18:45:44,818 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'amd64_edac_mod'}
2012-07-05 18:45:44,818 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'amd64_edac_mod', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:45:44,818 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f72cf8> about HardwareID('modalias', 'input:b0003v0461p4EBCe0110-e0,1,4,k71,72,73,74,80,8C,8E,8F,90,9B,9C,9E,9F,A1,A3,A4,A5,A6,AB,AC,AD,D9,ram4,lsfw')
2012-07-05 18:45:44,818 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-05 18:45:44,818 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:45:44,818 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-07-05 18:45:44,818 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:45:44,818 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f72cf8> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-07-05 18:45:44,819 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f72cf8> about HardwareID('modalias', 'usb:v1B1Cp0AB1d0100dc00dsc00dp00ic08isc06ip50')
2012-07-05 18:45:44,819 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uas'}
2012-07-05 18:45:44,819 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uas', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:45:44,819 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f72cf8> about HardwareID('modalias', 'pci:v00001002d00004396sv00001458sd00005004bc0Csc03i20')
2012-07-05 18:45:44,823 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f72cf8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-07-05 18:45:44,823 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-05 18:45:44,823 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:45:44,823 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f72cf8> about HardwareID('modalias', 'pci:v00001002d00004390sv00001458sd0000B002bc01sc06i01')
2012-07-05 18:45:44,827 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f72cf8> about HardwareID('modalias', 'usb:v0461p4EBCd0104dc00dsc00dp00ic03isc00ip00')
2012-07-05 18:45:44,827 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-07-05 18:45:44,827 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:45:44,827 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f72cf8> about HardwareID('modalias', 'pci:v00001002d00005957sv00001002sd00005957bc06sc00i00')
2012-07-05 18:45:44,830 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f72cf8> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-07-05 18:45:44,831 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f72cf8> about HardwareID('modalias', 'usb:v046DpC05Bd5400dc00dsc00dp00ic03isc01ip02')
2012-07-05 18:45:44,852 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-07-05 18:45:44,852 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:45:44,852 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2012-07-05 18:45:44,852 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:45:44,852 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f72cf8> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2012-07-05 18:45:44,853 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'k10temp'}
2012-07-05 18:45:44,853 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k10temp', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:45:44,853 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f72cf8> about HardwareID('modalias', 'pci:v00001002d00004385sv00001458sd00004385bc0Csc05i00')
2012-07-05 18:45:44,856 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4'}
2012-07-05 18:45:44,856 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:45:44,856 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco'}
2012-07-05 18:45:44,857 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:45:44,857 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f72cf8> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-07-05 18:45:44,860 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f72cf8> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2012-07-05 18:45:44,867 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-07-05 18:45:44,867 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:45:44,867 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f72cf8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2012-07-05 18:45:44,867 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-05 18:45:44,867 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:45:44,867 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f72cf8> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001002sd0000439Dbc06sc01i00')
2012-07-05 18:45:44,871 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f72cf8> about HardwareID('modalias', 'acpi:PNP0200:')
2012-07-05 18:45:44,871 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x22f1290> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-07-05 18:45:44,871 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x22f1290> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2012-07-05 18:45:44,871 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x22f1290> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-07-05 18:45:44,871 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x22f1290> about HardwareID('modalias', 'acpi:PNP0103:')
2012-07-05 18:45:44,871 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x22f1290> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001458sd0000E000bc02sc00i00')
2012-07-05 18:45:44,871 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x22f1290> about HardwareID('modalias', 'platform:pcspkr')
2012-07-05 18:45:44,871 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x22f1290> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-07-05 18:45:44,871 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x22f1290> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-07-05 18:45:44,871 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x22f1290> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-07-05 18:45:44,871 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x22f1290> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2012-07-05 18:45:44,871 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x22f1290> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-07-05 18:45:44,871 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x22f1290> about HardwareID('modalias', 'wmi:ABBC0F6A-8EA1-11D1-00A0-C90629100000')
2012-07-05 18:45:44,871 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x22f1290> about HardwareID('modalias', 'pci:v00001002d00009501sv0000174Bsd0000E620bc03sc00i00')
2012-07-05 18:45:44,872 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x22f1290> about HardwareID('modalias', 'pci:v00001002d00004383sv00001458sd0000A002bc04sc03i00')
2012-07-05 18:45:44,872 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x22f1290> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-07-05 18:45:44,872 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x22f1290> about HardwareID('modalias', 'acpi:PNP0800:')
2012-07-05 18:45:44,872 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x22f1290> about HardwareID('modalias', 'acpi:PNP0000:')
2012-07-05 18:45:44,872 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x22f1290> about HardwareID('modalias', 'pci:v00001002d0000AA18sv0000174Bsd0000AA18bc04sc03i00')
2012-07-05 18:45:44,872 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x22f1290> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001458sd00005002bc01sc01i8a')
2012-07-05 18:45:44,872 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x22f1290> about HardwareID('modalias', 'acpi:PNP0100:')
2012-07-05 18:45:44,872 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x22f1290> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2012-07-05 18:45:44,872 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x22f1290> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2012-07-05 18:45:44,872 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x22f1290> about HardwareID('modalias', 'usb:v0461p4EBCd0104dc00dsc00dp00ic03isc01ip01')
2012-07-05 18:45:44,872 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x22f1290> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2012-07-05 18:45:44,872 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x22f1290> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-07-05 18:45:44,872 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x22f1290> about HardwareID('modalias', 'input:b0003v0461p4EBCe0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8C,8E,96,98,9E,9F,A1,A3,A4,A5,A6,AD,B0,B1,B2,B3,B4,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2012-07-05 18:45:44,872 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x22f1290> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2012-07-05 18:45:44,872 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x22f1290> about HardwareID('modalias', 'input:b0003v046DpC05Be0111-e0,1,2,4,k110,111,112,113,114,115,116,117,r0,1,6,8,am4,lsfw')
2012-07-05 18:45:44,872 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x22f1290> about HardwareID('modalias', 'dmi:bvnAwardSoftwareInternational,Inc.:bvrF10:bd03/22/2011:svnGigabyteTechnologyCo.,Ltd.:pnGA-MA770T-UD3:pvr:rvnGigabyteTechnologyCo.,Ltd.:rnGA-MA770T-UD3:rvr:cvnGigabyteTechnologyCo.,Ltd.:ct3:cvr:')
2012-07-05 18:45:44,872 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x22f1290> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-07-05 18:45:44,872 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x22f1290> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2012-07-05 18:45:44,873 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x22f1290> about HardwareID('modalias', 'input:b0003v0461p4EBCe0110-e0,1,4,k71,72,73,74,80,8C,8E,8F,90,9B,9C,9E,9F,A1,A3,A4,A5,A6,AB,AC,AD,D9,ram4,lsfw')
2012-07-05 18:45:44,873 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x22f1290> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-07-05 18:45:44,873 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x22f1290> about HardwareID('modalias', 'usb:v1B1Cp0AB1d0100dc00dsc00dp00ic08isc06ip50')
2012-07-05 18:45:44,873 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x22f1290> about HardwareID('modalias', 'pci:v00001002d00004396sv00001458sd00005004bc0Csc03i20')
2012-07-05 18:45:44,873 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x22f1290> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-07-05 18:45:44,873 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x22f1290> about HardwareID('modalias', 'pci:v00001002d00004390sv00001458sd0000B002bc01sc06i01')
2012-07-05 18:45:44,873 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x22f1290> about HardwareID('modalias', 'usb:v0461p4EBCd0104dc00dsc00dp00ic03isc00ip00')
2012-07-05 18:45:44,873 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x22f1290> about HardwareID('modalias', 'pci:v00001002d00005957sv00001002sd00005957bc06sc00i00')
2012-07-05 18:45:44,873 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x22f1290> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-07-05 18:45:44,873 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x22f1290> about HardwareID('modalias', 'usb:v046DpC05Bd5400dc00dsc00dp00ic03isc01ip02')
2012-07-05 18:45:44,873 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x22f1290> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2012-07-05 18:45:44,873 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x22f1290> about HardwareID('modalias', 'pci:v00001002d00004385sv00001458sd00004385bc0Csc05i00')
2012-07-05 18:45:44,873 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x22f1290> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-07-05 18:45:44,873 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x22f1290> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2012-07-05 18:45:44,873 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x22f1290> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2012-07-05 18:45:44,873 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x22f1290> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001002sd0000439Dbc06sc01i00')
2012-07-05 18:45:44,873 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x22f1290> about HardwareID('modalias', 'acpi:PNP0200:')
2012-07-05 18:45:44,963 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:45:44,963 DEBUG: fglrx_updates is not the alternative in use
2012-07-05 18:45:44,986 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:45:44,987 DEBUG: fglrx_updates is not the alternative in use
2012-07-05 18:45:45,051 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:45:45,051 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-07-05 18:45:45,185 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:45:45,185 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-07-05 18:45:45,281 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:45:45,281 DEBUG: fglrx_updates is not the alternative in use
2012-07-05 18:45:45,304 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:45:45,304 DEBUG: fglrx_updates is not the alternative in use
2012-07-05 18:45:45,392 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:45:45,392 DEBUG: fglrx_updates is not the alternative in use
2012-07-05 18:45:45,434 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:45:45,435 DEBUG: fglrx_updates is not the alternative in use
2012-07-05 18:45:45,499 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:45:45,499 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-07-05 18:45:45,617 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:45:45,618 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-07-05 18:47:43,149 DEBUG: Shutting down
2012-07-05 18:47:47,833 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x20e8d40>
2012-07-05 18:47:49,793 DEBUG: reading modalias file /lib/modules/3.2.0-26-generic/modules.alias
2012-07-05 18:47:49,876 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-07-05 18:47:49,876 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-07-05 18:47:49,938 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2012-07-05 18:47:49,947 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2012-07-05 18:47:49,948 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2012-07-05 18:47:49,986 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2012-07-05 18:47:49,987 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-07-05 18:47:50,014 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2012-07-05 18:47:50,015 DEBUG: fglrx.available: falling back to default
2012-07-05 18:47:50,146 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2012-07-05 18:47:50,154 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-07-05 18:47:50,165 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-07-05 18:47:50,166 DEBUG: fglrx.available: falling back to default
2012-07-05 18:47:50,244 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-07-05 18:47:50,244 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-07-05 18:47:50,298 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-07-05 18:47:50,299 DEBUG: Firmware for DVB cards not available
2012-07-05 18:47:50,299 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-07-05 18:47:50,315 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-07-05 18:47:50,327 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-07-05 18:47:50,330 DEBUG: nvidia.available: falling back to default
2012-07-05 18:47:50,368 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-07-05 18:47:50,369 DEBUG: NVIDIA accelerated graphics driver not available
2012-07-05 18:47:50,377 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-07-05 18:47:50,389 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-07-05 18:47:50,390 DEBUG: nvidia.available: falling back to default
2012-07-05 18:47:50,468 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-07-05 18:47:50,476 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-07-05 18:47:50,488 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2012-07-05 18:47:50,489 DEBUG: nvidia.available: falling back to default
2012-07-05 18:47:50,575 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-07-05 18:47:50,583 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-07-05 18:47:50,595 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2012-07-05 18:47:50,597 DEBUG: nvidia.available: falling back to default
2012-07-05 18:47:50,635 DEBUG: XorgDriverHandler(nvidia_173_updates, nvidia-173-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-07-05 18:47:50,636 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-07-05 18:47:50,644 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-07-05 18:47:50,657 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-07-05 18:47:50,658 DEBUG: nvidia.available: falling back to default
2012-07-05 18:47:50,676 DEBUG: XorgDriverHandler(nvidia_173, nvidia-173, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-07-05 18:47:50,676 DEBUG: NVIDIA accelerated graphics driver not available
2012-07-05 18:47:50,679 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2012-07-05 18:47:50,685 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2012-07-05 18:47:50,686 DEBUG: nvidia.available: falling back to default
2012-07-05 18:47:50,709 DEBUG: XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-07-05 18:47:50,709 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-07-05 18:47:50,709 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-07-05 18:47:50,718 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-07-05 18:47:50,719 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-07-05 18:47:50,719 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-07-05 18:47:50,719 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-07-05 18:47:50,729 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-07-05 18:47:50,772 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-07-05 18:47:50,773 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-07-05 18:47:50,773 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2012-07-05 18:47:50,786 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2012-07-05 18:47:50,798 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2012-07-05 18:47:50,861 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2012-07-05 18:47:50,861 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-07-05 18:47:50,881 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-07-05 18:47:50,890 DEBUG: Software modem not available
2012-07-05 18:47:50,890 DEBUG: all custom handlers loaded
2012-07-05 18:47:50,890 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x20e8d40> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-07-05 18:47:50,891 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x20e8d40> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2012-07-05 18:47:50,903 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-05 18:47:50,986 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:47:50,986 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x20e8d40> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-07-05 18:47:50,986 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x20e8d40> about HardwareID('modalias', 'acpi:PNP0103:')
2012-07-05 18:47:50,987 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x20e8d40> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001458sd0000E000bc02sc00i00')
2012-07-05 18:47:50,996 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2012-07-05 18:47:50,996 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:47:50,996 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x20e8d40> about HardwareID('modalias', 'platform:pcspkr')
2012-07-05 18:47:50,997 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2012-07-05 18:47:50,997 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:47:50,997 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2012-07-05 18:47:50,997 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:47:50,997 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x20e8d40> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-07-05 18:47:51,009 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x20e8d40> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-07-05 18:47:51,009 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-05 18:47:51,009 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:47:51,009 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-07-05 18:47:51,009 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:47:51,009 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x20e8d40> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-07-05 18:47:51,009 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x20e8d40> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2012-07-05 18:47:51,010 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x20e8d40> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-07-05 18:47:51,010 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x20e8d40> about HardwareID('modalias', 'wmi:ABBC0F6A-8EA1-11D1-00A0-C90629100000')
2012-07-05 18:47:51,010 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x20e8d40> about HardwareID('modalias', 'pci:v00001002d00009501sv0000174Bsd0000E620bc03sc00i00')
2012-07-05 18:47:51,281 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2012-07-05 18:47:51,281 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:47:51,281 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates'}
2012-07-05 18:47:51,304 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:47:51,304 DEBUG: fglrx_updates is not the alternative in use
2012-07-05 18:47:51,281 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-07-05 18:47:51,312 DEBUG: fglrx.available: falling back to default
2012-07-05 18:47:51,376 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:47:51,377 DEBUG: fglrx_updates is not the alternative in use
2012-07-05 18:47:51,345 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-07-05 18:47:51,377 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2012-07-05 18:47:51,409 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:47:51,409 DEBUG: fglrx_updates is not the alternative in use
2012-07-05 18:47:51,378 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-07-05 18:47:51,421 DEBUG: fglrx.available: falling back to default
2012-07-05 18:47:51,486 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:47:51,487 DEBUG: fglrx_updates is not the alternative in use
2012-07-05 18:47:51,463 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-07-05 18:47:51,487 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2012-07-05 18:47:51,518 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:47:51,518 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-07-05 18:47:51,488 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-07-05 18:47:51,527 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-07-05 18:47:51,538 DEBUG: fglrx.available: falling back to default
2012-07-05 18:47:51,609 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:47:51,610 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-07-05 18:47:51,578 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-07-05 18:47:51,610 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x20e8d40> about HardwareID('modalias', 'pci:v00001002d00004383sv00001458sd0000A002bc04sc03i00')
2012-07-05 18:47:51,622 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-07-05 18:47:51,622 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:47:51,623 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-07-05 18:47:51,623 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:47:51,623 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x20e8d40> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-07-05 18:47:51,623 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x20e8d40> about HardwareID('modalias', 'acpi:PNP0800:')
2012-07-05 18:47:51,624 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x20e8d40> about HardwareID('modalias', 'acpi:PNP0000:')
2012-07-05 18:47:51,624 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x20e8d40> about HardwareID('modalias', 'pci:v00001002d0000AA18sv0000174Bsd0000AA18bc04sc03i00')
2012-07-05 18:47:51,627 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-07-05 18:47:51,628 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:47:51,628 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-07-05 18:47:51,628 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:47:51,628 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x20e8d40> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001458sd00005002bc01sc01i8a')
2012-07-05 18:47:51,631 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pata_atiixp'}
2012-07-05 18:47:51,631 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_atiixp', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:47:51,631 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x20e8d40> about HardwareID('modalias', 'acpi:PNP0100:')
2012-07-05 18:47:51,631 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x20e8d40> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2012-07-05 18:47:51,642 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x20e8d40> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2012-07-05 18:47:51,643 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x20e8d40> about HardwareID('modalias', 'usb:v0461p4EBCd0104dc00dsc00dp00ic03isc01ip01')
2012-07-05 18:47:51,644 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-07-05 18:47:51,644 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:47:51,644 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2012-07-05 18:47:51,644 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:47:51,644 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x20e8d40> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2012-07-05 18:47:51,644 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-05 18:47:51,645 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:47:51,645 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x20e8d40> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-07-05 18:47:51,645 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-05 18:47:51,645 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:47:51,645 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x20e8d40> about HardwareID('modalias', 'input:b0003v0461p4EBCe0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8C,8E,96,98,9E,9F,A1,A3,A4,A5,A6,AD,B0,B1,B2,B3,B4,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2012-07-05 18:47:51,645 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-05 18:47:51,645 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:47:51,645 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-07-05 18:47:51,645 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:47:51,645 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x20e8d40> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2012-07-05 18:47:51,646 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x20e8d40> about HardwareID('modalias', 'input:b0003v046DpC05Be0111-e0,1,2,4,k110,111,112,113,114,115,116,117,r0,1,6,8,am4,lsfw')
2012-07-05 18:47:51,646 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-05 18:47:51,646 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:47:51,646 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-07-05 18:47:51,646 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:47:51,646 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x20e8d40> about HardwareID('modalias', 'dmi:bvnAwardSoftwareInternational,Inc.:bvrF10:bd03/22/2011:svnGigabyteTechnologyCo.,Ltd.:pnGA-MA770T-UD3:pvr:rvnGigabyteTechnologyCo.,Ltd.:rnGA-MA770T-UD3:rvr:cvnGigabyteTechnologyCo.,Ltd.:ct3:cvr:')
2012-07-05 18:47:51,659 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x20e8d40> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-07-05 18:47:51,659 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x20e8d40> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2012-07-05 18:47:51,659 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'amd64_edac_mod'}
2012-07-05 18:47:51,659 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'amd64_edac_mod', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:47:51,659 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x20e8d40> about HardwareID('modalias', 'input:b0003v0461p4EBCe0110-e0,1,4,k71,72,73,74,80,8C,8E,8F,90,9B,9C,9E,9F,A1,A3,A4,A5,A6,AB,AC,AD,D9,ram4,lsfw')
2012-07-05 18:47:51,659 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-05 18:47:51,660 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:47:51,660 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-07-05 18:47:51,660 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:47:51,660 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x20e8d40> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-07-05 18:47:51,660 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x20e8d40> about HardwareID('modalias', 'usb:v1B1Cp0AB1d0100dc00dsc00dp00ic08isc06ip50')
2012-07-05 18:47:51,661 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uas'}
2012-07-05 18:47:51,661 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uas', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:47:51,661 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x20e8d40> about HardwareID('modalias', 'pci:v00001002d00004396sv00001458sd00005004bc0Csc03i20')
2012-07-05 18:47:51,664 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x20e8d40> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-07-05 18:47:51,665 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-05 18:47:51,665 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:47:51,665 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x20e8d40> about HardwareID('modalias', 'pci:v00001002d00004390sv00001458sd0000B002bc01sc06i01')
2012-07-05 18:47:51,668 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x20e8d40> about HardwareID('modalias', 'usb:v0461p4EBCd0104dc00dsc00dp00ic03isc00ip00')
2012-07-05 18:47:51,668 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-07-05 18:47:51,668 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:47:51,669 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x20e8d40> about HardwareID('modalias', 'pci:v00001002d00005957sv00001002sd00005957bc06sc00i00')
2012-07-05 18:47:51,672 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x20e8d40> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-07-05 18:47:51,672 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x20e8d40> about HardwareID('modalias', 'usb:v046DpC05Bd5400dc00dsc00dp00ic03isc01ip02')
2012-07-05 18:47:51,694 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-07-05 18:47:51,694 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:47:51,694 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2012-07-05 18:47:51,694 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:47:51,694 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x20e8d40> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2012-07-05 18:47:51,694 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'k10temp'}
2012-07-05 18:47:51,694 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k10temp', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:47:51,694 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x20e8d40> about HardwareID('modalias', 'pci:v00001002d00004385sv00001458sd00004385bc0Csc05i00')
2012-07-05 18:47:51,698 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4'}
2012-07-05 18:47:51,698 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:47:51,698 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco'}
2012-07-05 18:47:51,698 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:47:51,698 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x20e8d40> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-07-05 18:47:51,701 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x20e8d40> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2012-07-05 18:47:51,708 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-07-05 18:47:51,708 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:47:51,708 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x20e8d40> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2012-07-05 18:47:51,708 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-05 18:47:51,709 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:47:51,709 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x20e8d40> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001002sd0000439Dbc06sc01i00')
2012-07-05 18:47:51,712 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x20e8d40> about HardwareID('modalias', 'acpi:PNP0200:')
2012-07-05 18:47:51,712 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24622d8> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-07-05 18:47:51,712 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24622d8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2012-07-05 18:47:51,712 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24622d8> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-07-05 18:47:51,712 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24622d8> about HardwareID('modalias', 'acpi:PNP0103:')
2012-07-05 18:47:51,712 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24622d8> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001458sd0000E000bc02sc00i00')
2012-07-05 18:47:51,712 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24622d8> about HardwareID('modalias', 'platform:pcspkr')
2012-07-05 18:47:51,712 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24622d8> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-07-05 18:47:51,712 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24622d8> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-07-05 18:47:51,712 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24622d8> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-07-05 18:47:51,713 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24622d8> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2012-07-05 18:47:51,713 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24622d8> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-07-05 18:47:51,713 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24622d8> about HardwareID('modalias', 'wmi:ABBC0F6A-8EA1-11D1-00A0-C90629100000')
2012-07-05 18:47:51,713 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24622d8> about HardwareID('modalias', 'pci:v00001002d00009501sv0000174Bsd0000E620bc03sc00i00')
2012-07-05 18:47:51,713 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24622d8> about HardwareID('modalias', 'pci:v00001002d00004383sv00001458sd0000A002bc04sc03i00')
2012-07-05 18:47:51,713 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24622d8> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-07-05 18:47:51,713 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24622d8> about HardwareID('modalias', 'acpi:PNP0800:')
2012-07-05 18:47:51,713 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24622d8> about HardwareID('modalias', 'acpi:PNP0000:')
2012-07-05 18:47:51,713 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24622d8> about HardwareID('modalias', 'pci:v00001002d0000AA18sv0000174Bsd0000AA18bc04sc03i00')
2012-07-05 18:47:51,713 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24622d8> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001458sd00005002bc01sc01i8a')
2012-07-05 18:47:51,713 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24622d8> about HardwareID('modalias', 'acpi:PNP0100:')
2012-07-05 18:47:51,713 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24622d8> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2012-07-05 18:47:51,713 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24622d8> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2012-07-05 18:47:51,713 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24622d8> about HardwareID('modalias', 'usb:v0461p4EBCd0104dc00dsc00dp00ic03isc01ip01')
2012-07-05 18:47:51,713 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24622d8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2012-07-05 18:47:51,713 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24622d8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-07-05 18:47:51,713 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24622d8> about HardwareID('modalias', 'input:b0003v0461p4EBCe0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8C,8E,96,98,9E,9F,A1,A3,A4,A5,A6,AD,B0,B1,B2,B3,B4,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2012-07-05 18:47:51,713 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24622d8> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2012-07-05 18:47:51,713 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24622d8> about HardwareID('modalias', 'input:b0003v046DpC05Be0111-e0,1,2,4,k110,111,112,113,114,115,116,117,r0,1,6,8,am4,lsfw')
2012-07-05 18:47:51,714 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24622d8> about HardwareID('modalias', 'dmi:bvnAwardSoftwareInternational,Inc.:bvrF10:bd03/22/2011:svnGigabyteTechnologyCo.,Ltd.:pnGA-MA770T-UD3:pvr:rvnGigabyteTechnologyCo.,Ltd.:rnGA-MA770T-UD3:rvr:cvnGigabyteTechnologyCo.,Ltd.:ct3:cvr:')
2012-07-05 18:47:51,714 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24622d8> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-07-05 18:47:51,714 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24622d8> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2012-07-05 18:47:51,714 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24622d8> about HardwareID('modalias', 'input:b0003v0461p4EBCe0110-e0,1,4,k71,72,73,74,80,8C,8E,8F,90,9B,9C,9E,9F,A1,A3,A4,A5,A6,AB,AC,AD,D9,ram4,lsfw')
2012-07-05 18:47:51,714 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24622d8> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-07-05 18:47:51,714 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24622d8> about HardwareID('modalias', 'usb:v1B1Cp0AB1d0100dc00dsc00dp00ic08isc06ip50')
2012-07-05 18:47:51,714 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24622d8> about HardwareID('modalias', 'pci:v00001002d00004396sv00001458sd00005004bc0Csc03i20')
2012-07-05 18:47:51,714 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24622d8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-07-05 18:47:51,714 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24622d8> about HardwareID('modalias', 'pci:v00001002d00004390sv00001458sd0000B002bc01sc06i01')
2012-07-05 18:47:51,714 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24622d8> about HardwareID('modalias', 'usb:v0461p4EBCd0104dc00dsc00dp00ic03isc00ip00')
2012-07-05 18:47:51,714 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24622d8> about HardwareID('modalias', 'pci:v00001002d00005957sv00001002sd00005957bc06sc00i00')
2012-07-05 18:47:51,714 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24622d8> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-07-05 18:47:51,714 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24622d8> about HardwareID('modalias', 'usb:v046DpC05Bd5400dc00dsc00dp00ic03isc01ip02')
2012-07-05 18:47:51,714 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24622d8> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2012-07-05 18:47:51,714 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24622d8> about HardwareID('modalias', 'pci:v00001002d00004385sv00001458sd00004385bc0Csc05i00')
2012-07-05 18:47:51,714 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24622d8> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-07-05 18:47:51,714 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24622d8> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2012-07-05 18:47:51,714 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24622d8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2012-07-05 18:47:51,714 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24622d8> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001002sd0000439Dbc06sc01i00')
2012-07-05 18:47:51,715 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x24622d8> about HardwareID('modalias', 'acpi:PNP0200:')
2012-07-05 18:47:51,785 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:47:51,785 DEBUG: fglrx_updates is not the alternative in use
2012-07-05 18:47:55,749 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:47:55,749 DEBUG: fglrx_updates is not the alternative in use
2012-07-05 18:47:58,520 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:47:58,521 DEBUG: fglrx_updates is not the alternative in use
2012-07-05 18:48:05,852 WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver
2012-07-05 18:48:38,827 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:48:38,828 DEBUG: fglrx_updates is not the alternative in use
2012-07-05 18:48:38,859 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:48:38,860 DEBUG: fglrx_updates is not the alternative in use
2012-07-05 18:48:43,210 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:48:43,211 DEBUG: fglrx_updates is not the alternative in use
2012-07-05 18:48:43,242 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:48:43,243 DEBUG: fglrx_updates is not the alternative in use
2012-07-05 18:48:43,304 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:48:43,305 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-07-05 18:48:43,466 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:48:43,466 DEBUG: fglrx_updates is not the alternative in use
2012-07-05 18:48:43,497 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:48:43,498 DEBUG: fglrx_updates is not the alternative in use
2012-07-05 18:48:43,590 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:48:43,590 DEBUG: fglrx_updates is not the alternative in use
2012-07-05 18:48:43,621 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:48:43,622 DEBUG: fglrx_updates is not the alternative in use
2012-07-05 18:48:43,678 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:48:43,678 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-07-05 18:48:47,234 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:48:47,235 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-07-05 18:48:49,114 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:48:49,115 DEBUG: fglrx_updates is not the alternative in use
2012-07-05 18:48:49,147 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:48:49,147 DEBUG: fglrx_updates is not the alternative in use
2012-07-05 18:48:49,963 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:48:49,964 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-07-05 18:48:53,445 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:48:53,446 DEBUG: fglrx_updates is not the alternative in use
2012-07-05 18:48:53,477 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:48:53,477 DEBUG: fglrx_updates is not the alternative in use
2012-07-05 18:48:58,984 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:48:58,985 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-07-05 18:49:00,249 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:49:00,250 DEBUG: fglrx_updates is not the alternative in use
2012-07-05 18:49:00,281 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:49:00,281 DEBUG: fglrx_updates is not the alternative in use
2012-07-05 18:49:00,969 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:49:00,970 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-07-05 18:49:02,186 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:49:02,187 DEBUG: fglrx_updates is not the alternative in use
2012-07-05 18:49:02,218 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:49:02,218 DEBUG: fglrx_updates is not the alternative in use
2012-07-05 18:49:02,867 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:49:02,867 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-07-05 18:49:05,643 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:49:05,644 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-07-05 18:49:07,133 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:49:07,133 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-07-05 18:49:07,407 DEBUG: Installing package: fglrx
2012-07-05 18:49:09,221 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 0.000000
2012-07-05 18:49:09,223 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 0.000000
2012-07-05 18:49:09,311 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 0.000000
2012-07-05 18:49:09,345 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 0.000000
2012-07-05 18:49:09,387 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 0.003617
2012-07-05 18:49:09,888 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 0.400926
2012-07-05 18:49:10,390 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 0.774397
2012-07-05 18:49:10,891 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 1.149854
2012-07-05 18:49:11,393 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 1.813360
2012-07-05 18:49:11,894 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 2.403364
2012-07-05 18:49:12,396 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 2.985421
2012-07-05 18:49:12,897 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 3.579398
2012-07-05 18:49:13,399 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 4.205160
2012-07-05 18:49:13,900 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 4.739541
2012-07-05 18:49:14,401 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 5.556011
2012-07-05 18:49:14,903 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 6.229449
2012-07-05 18:49:15,404 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 6.906861
2012-07-05 18:49:15,905 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 7.584273
2012-07-05 18:49:16,407 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 8.259698
2012-07-05 18:49:16,908 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 8.831915
2012-07-05 18:49:17,409 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 9.324487
2012-07-05 18:49:17,910 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 9.781392
2012-07-05 18:49:18,412 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 10.164795
2012-07-05 18:49:18,913 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 10.478669
2012-07-05 18:49:19,415 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 10.818369
2012-07-05 18:49:19,916 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 11.406386
2012-07-05 18:49:20,417 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 12.083798
2012-07-05 18:49:20,919 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 12.721479
2012-07-05 18:49:21,420 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 13.353200
2012-07-05 18:49:21,921 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 13.911419
2012-07-05 18:49:22,422 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 14.447786
2012-07-05 18:49:22,924 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 15.031831
2012-07-05 18:49:23,425 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 15.653619
2012-07-05 18:49:23,926 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 16.331031
2012-07-05 18:49:24,428 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 17.002483
2012-07-05 18:49:24,929 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 17.675922
2012-07-05 18:49:25,430 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 18.343401
2012-07-05 18:49:25,931 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 18.871822
2012-07-05 18:49:26,433 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 19.215495
2012-07-05 18:49:26,934 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 19.573073
2012-07-05 18:49:27,435 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 19.896880
2012-07-05 18:49:27,936 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 20.236579
2012-07-05 18:49:28,438 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 20.715336
2012-07-05 18:49:28,939 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 21.136484
2012-07-05 18:49:29,440 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 21.537766
2012-07-05 18:49:29,941 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 21.885411
2012-07-05 18:49:30,443 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 22.264841
2012-07-05 18:49:30,944 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 22.817101
2012-07-05 18:49:31,445 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 23.494513
2012-07-05 18:49:31,947 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 24.138153
2012-07-05 18:49:32,448 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 24.706305
2012-07-05 18:49:32,949 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 25.286376
2012-07-05 18:49:33,451 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 25.721430
2012-07-05 18:49:33,952 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 26.188268
2012-07-05 18:49:34,453 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 26.601469
2012-07-05 18:49:34,955 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 26.968980
2012-07-05 18:49:35,456 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 27.362316
2012-07-05 18:49:35,957 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 27.910602
2012-07-05 18:49:36,459 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 28.586028
2012-07-05 18:49:36,960 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 29.265426
2012-07-05 18:49:37,461 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 29.940851
2012-07-05 18:49:37,962 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 30.608331
2012-07-05 18:49:38,464 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 31.208267
2012-07-05 18:49:38,965 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 31.728742
2012-07-05 18:49:39,466 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 32.275042
2012-07-05 18:49:39,967 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 32.874979
2012-07-05 18:49:40,469 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 33.494781
2012-07-05 18:49:40,970 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 34.130475
2012-07-05 18:49:41,471 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 34.639031
2012-07-05 18:49:41,972 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 35.141626
2012-07-05 18:49:42,474 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 35.588599
2012-07-05 18:49:42,975 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 36.075303
2012-07-05 18:49:43,476 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 36.581872
2012-07-05 18:49:43,977 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 36.886873
2012-07-05 18:49:44,479 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 37.499655
2012-07-05 18:49:44,980 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 38.155215
2012-07-05 18:49:45,481 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 38.822694
2012-07-05 18:49:45,983 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 39.498120
2012-07-05 18:49:46,484 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 40.175532
2012-07-05 18:49:46,985 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 40.850957
2012-07-05 18:49:47,487 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 41.528369
2012-07-05 18:49:47,988 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 42.120359
2012-07-05 18:49:48,489 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 42.752081
2012-07-05 18:49:48,991 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 43.411614
2012-07-05 18:49:49,492 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 44.083066
2012-07-05 18:49:50,020 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 44.782330
2012-07-05 18:49:50,521 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 45.459742
2012-07-05 18:49:51,022 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 46.137153
2012-07-05 18:49:51,524 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 46.812579
2012-07-05 18:49:52,025 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 47.454233
2012-07-05 18:49:52,527 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 47.954842
2012-07-05 18:49:53,028 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 48.318380
2012-07-05 18:49:53,529 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 48.576631
2012-07-05 18:49:54,031 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 48.844814
2012-07-05 18:49:54,532 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 49.426872
2012-07-05 18:49:55,033 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 50.104284
2012-07-05 18:49:55,535 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 50.767790
2012-07-05 18:49:56,036 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 51.443215
2012-07-05 18:49:56,537 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 52.063017
2012-07-05 18:49:57,039 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 52.774201
2012-07-05 18:49:57,540 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 53.195348
2012-07-05 18:49:58,042 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 53.525115
2012-07-05 18:49:58,543 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 53.904545
2012-07-05 18:49:59,044 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 54.401181
2012-07-05 18:49:59,545 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 54.901790
2012-07-05 18:50:00,046 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 55.676543
2012-07-05 18:50:00,547 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 56.351968
2012-07-05 18:50:01,049 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 57.027394
2012-07-05 18:50:01,550 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 57.702819
2012-07-05 18:50:02,051 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 58.380231
2012-07-05 18:50:02,552 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 59.057643
2012-07-05 18:50:03,054 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 59.669498
2012-07-05 18:50:03,555 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 60.162162
2012-07-05 18:50:04,056 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 60.680650
2012-07-05 18:50:04,558 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 61.103784
2012-07-05 18:50:05,059 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 61.429577
2012-07-05 18:50:05,560 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 61.761330
2012-07-05 18:50:06,062 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 62.077191
2012-07-05 18:50:06,563 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 62.448675
2012-07-05 18:50:07,064 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 62.865850
2012-07-05 18:50:07,566 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 63.467773
2012-07-05 18:50:08,067 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 64.210741
2012-07-05 18:50:08,568 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 64.884179
2012-07-05 18:50:09,069 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 65.551658
2012-07-05 18:50:09,571 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 66.229070
2012-07-05 18:50:10,072 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 66.904496
2012-07-05 18:50:10,573 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 67.581908
2012-07-05 18:50:11,075 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 68.255346
2012-07-05 18:50:11,576 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 68.928785
2012-07-05 18:50:12,077 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 69.596264
2012-07-05 18:50:12,578 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 70.140578
2012-07-05 18:50:13,079 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 70.722635
2012-07-05 18:50:13,581 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 71.153716
2012-07-05 18:50:14,082 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 71.529173
2012-07-05 18:50:14,583 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 71.928468
2012-07-05 18:50:15,085 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 72.335710
2012-07-05 18:50:15,586 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 72.764804
2012-07-05 18:50:16,087 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 73.094570
2012-07-05 18:50:16,589 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 73.479960
2012-07-05 18:50:17,090 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 73.781915
2012-07-05 18:50:17,591 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 74.129560
2012-07-05 18:50:18,093 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 74.493098
2012-07-05 18:50:18,594 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 74.757308
2012-07-05 18:50:19,095 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 75.053304
2012-07-05 18:50:19,596 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 75.414855
2012-07-05 18:50:20,098 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 75.830043
2012-07-05 18:50:20,599 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 76.207486
2012-07-05 18:50:21,100 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 76.549172
2012-07-05 18:50:21,602 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 76.896817
2012-07-05 18:50:22,103 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 77.476889
2012-07-05 18:50:22,604 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 78.108610
2012-07-05 18:50:23,106 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 78.690668
2012-07-05 18:50:23,607 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 79.191277
2012-07-05 18:50:24,108 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 79.711752
2012-07-05 18:50:24,610 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 80.250105
2012-07-05 18:50:25,111 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 80.776540
2012-07-05 18:50:25,612 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 81.151997
2012-07-05 18:50:26,114 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 81.525467
2012-07-05 18:50:26,615 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 81.916817
2012-07-05 18:50:27,116 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 82.522713
2012-07-05 18:50:27,618 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 83.198138
2012-07-05 18:50:28,119 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 83.837806
2012-07-05 18:50:28,620 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 84.302657
2012-07-05 18:50:29,122 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 84.751617
2012-07-05 18:50:29,623 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 85.240307
2012-07-05 18:50:30,124 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 85.901826
2012-07-05 18:50:30,626 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 86.551426
2012-07-05 18:50:31,127 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 87.185134
2012-07-05 18:50:31,628 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 87.848640
2012-07-05 18:50:32,129 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 88.510160
2012-07-05 18:50:32,631 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 89.187572
2012-07-05 18:50:33,132 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 89.862997
2012-07-05 18:50:33,633 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 90.540409
2012-07-05 18:50:34,135 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 91.182063
2012-07-05 18:50:34,636 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 91.789946
2012-07-05 18:50:34,665 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 91.827449
2012-07-05 18:50:34,670 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 91.827449
2012-07-05 18:50:34,707 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 91.827449
2012-07-05 18:50:34,746 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 91.827449
2012-07-05 18:50:35,247 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 92.194606
2012-07-05 18:50:35,748 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 92.536292
2012-07-05 18:50:36,250 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 92.856126
2012-07-05 18:50:36,751 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 93.426264
2012-07-05 18:50:37,252 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 93.970578
2012-07-05 18:50:37,753 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 94.548662
2012-07-05 18:50:38,255 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 95.124760
2012-07-05 18:50:38,756 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 95.752509
2012-07-05 18:50:39,257 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 96.386217
2012-07-05 18:50:39,759 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 96.847095
2012-07-05 18:50:40,260 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 97.311947
2012-07-05 18:50:40,761 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 97.782758
2012-07-05 18:50:41,263 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 98.134376
2012-07-05 18:50:41,764 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 98.527712
2012-07-05 18:50:42,265 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 99.030308
2012-07-05 18:50:42,767 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 99.707720
2012-07-05 18:50:42,987 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:9050L> 100.000000
2012-07-05 18:50:44,127 DEBUG: install progress dpkg-exec 0.000000
2012-07-05 18:50:46,339 DEBUG: install progress fglrx-amdcccle-updates 0.000000
2012-07-05 18:50:46,429 DEBUG: install progress fglrx-amdcccle-updates 6.250000
2012-07-05 18:50:46,430 DEBUG: install progress fglrx-amdcccle-updates 12.500000
2012-07-05 18:50:46,668 DEBUG: install progress fglrx-amdcccle-updates 18.750000
2012-07-05 18:50:47,146 DEBUG: install progress fglrx-updates 18.750000
2012-07-05 18:50:47,247 DEBUG: install progress fglrx-updates 25.000000
2012-07-05 18:51:27,137 DEBUG: install progress fglrx-updates 31.250000
2012-07-05 18:51:28,037 DEBUG: install progress fglrx-updates 37.500000
2012-07-05 18:51:28,232 DEBUG: install progress bamfdaemon 37.500000
2012-07-05 18:51:28,460 DEBUG: install progress ureadahead 37.500000
2012-07-05 18:51:28,704 DEBUG: install progress initramfs-tools 37.500000
2012-07-05 18:51:42,315 DEBUG: install progress libc-bin 37.500000
2012-07-05 18:51:42,800 DEBUG: install progress dpkg-exec 37.500000
2012-07-05 18:51:43,424 DEBUG: install progress fglrx 37.500000
2012-07-05 18:51:43,525 DEBUG: install progress fglrx 43.750000
2012-07-05 18:51:48,131 DEBUG: install progress fglrx 50.000000
2012-07-05 18:51:48,249 DEBUG: install progress fglrx 56.250000
2012-07-05 18:51:48,524 DEBUG: install progress fglrx-amdcccle 56.250000
2012-07-05 18:51:48,625 DEBUG: install progress fglrx-amdcccle 62.500000
2012-07-05 18:51:49,146 DEBUG: install progress fglrx-amdcccle 68.750000
2012-07-05 18:51:49,260 DEBUG: install progress fglrx-amdcccle 75.000000
2012-07-05 18:51:49,386 DEBUG: install progress ureadahead 75.000000
2012-07-05 18:51:49,768 DEBUG: install progress dpkg-exec 75.000000
2012-07-05 18:51:49,806 DEBUG: install progress fglrx 75.000000
2012-07-05 18:51:50,257 DEBUG: install progress fglrx 81.250000
2012-07-05 18:52:14,112 DEBUG: install progress fglrx 87.500000
2012-07-05 18:52:14,518 DEBUG: install progress bamfdaemon 87.500000
2012-07-05 18:52:14,771 DEBUG: install progress fglrx-amdcccle 87.500000
2012-07-05 18:52:14,872 DEBUG: install progress fglrx-amdcccle 93.750000
2012-07-05 18:52:14,982 DEBUG: install progress fglrx-amdcccle 100.000000
2012-07-05 18:52:15,083 DEBUG: install progress initramfs-tools 100.000000
2012-07-05 18:52:28,939 DEBUG: install progress libc-bin 100.000000
2012-07-05 18:52:30,545 DEBUG: (Reading database ... 170379 files and directories currently installed.)
Removing fglrx-amdcccle-updates ...
Removing fglrx-updates ...
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
update-alternatives: using /usr/lib/pxpress/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-alternatives: using /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-26-generic
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Selecting previously unselected package fglrx.
(Reading database ... 170108 files and directories currently installed.)
Unpacking fglrx (from .../fglrx_2%3a8.960-0ubuntu1_amd64.deb) ...
Selecting previously unselected package fglrx-amdcccle.
Unpacking fglrx-amdcccle (from .../fglrx-amdcccle_2%3a8.960-0ubuntu1_amd64.deb) ...
Processing triggers for ureadahead ...
Setting up fglrx (2:8.960-0ubuntu1) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl32.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl32.icd (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken.
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl32.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl32.icd (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: using /usr/lib/fglrx/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
Loading new fglrx-8.960 DKMS files...
First Installation: checking all kernels...
Building only for 3.2.0-26-generic
Building for architecture x86_64
Building initial module for 3.2.0-26-generic
Done.

fglrx:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-26-generic/updates/dkms/

depmod....

DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Setting up fglrx-amdcccle (2:8.960-0ubuntu1) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-26-generic
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

2012-07-05 18:52:30,743 DEBUG: unbind/rebind on driver /sys/module/fglrx/drivers/pci:fglrx_pci: device 0000:01:00.0
2012-07-05 18:52:51,072 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:52:51,073 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-07-05 18:52:51,195 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:52:51,196 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-07-05 18:52:51,363 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:52:51,364 DEBUG: fglrx_updates is not the alternative in use
2012-07-05 18:52:51,402 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:52:51,403 DEBUG: fglrx_updates is not the alternative in use
2012-07-05 18:52:51,471 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:52:51,471 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-07-05 18:52:51,564 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:52:51,564 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-07-05 18:52:51,754 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:52:51,754 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-07-05 18:52:51,875 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:52:51,875 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-07-05 18:52:52,065 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:52:52,066 DEBUG: fglrx_updates is not the alternative in use
2012-07-05 18:52:52,104 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:52:52,105 DEBUG: fglrx_updates is not the alternative in use
2012-07-05 18:52:52,168 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:52:52,169 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-07-05 18:52:52,287 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:52:52,288 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-07-05 18:53:04,232 DEBUG: Shutting down
2012-07-05 18:58:52,867 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x2642d40>
2012-07-05 18:58:56,057 DEBUG: reading modalias file /lib/modules/3.2.0-26-generic/modules.alias
2012-07-05 18:58:56,196 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-07-05 18:58:56,204 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-07-05 18:58:56,289 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2012-07-05 18:58:56,351 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2012-07-05 18:58:56,352 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2012-07-05 18:58:56,409 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2012-07-05 18:58:56,410 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-07-05 18:58:56,474 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-07-05 18:58:56,485 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2012-07-05 18:58:56,486 DEBUG: fglrx.available: falling back to default
2012-07-05 18:58:56,653 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2012-07-05 18:58:56,664 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-07-05 18:58:56,665 DEBUG: fglrx.available: falling back to default
2012-07-05 18:58:56,728 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-07-05 18:58:56,729 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-07-05 18:58:56,838 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-07-05 18:58:56,839 DEBUG: Firmware for DVB cards not available
2012-07-05 18:58:56,839 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-07-05 18:58:56,853 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-07-05 18:58:56,860 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-07-05 18:58:56,863 DEBUG: nvidia.available: falling back to default
2012-07-05 18:58:56,901 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-07-05 18:58:56,901 DEBUG: NVIDIA accelerated graphics driver not available
2012-07-05 18:58:56,909 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-07-05 18:58:56,921 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-07-05 18:58:56,922 DEBUG: nvidia.available: falling back to default
2012-07-05 18:58:57,000 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-07-05 18:58:57,008 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-07-05 18:58:57,019 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2012-07-05 18:58:57,022 DEBUG: nvidia.available: falling back to default
2012-07-05 18:58:57,088 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-07-05 18:58:57,096 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-07-05 18:58:57,108 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2012-07-05 18:58:57,110 DEBUG: nvidia.available: falling back to default
2012-07-05 18:58:57,148 DEBUG: XorgDriverHandler(nvidia_173_updates, nvidia-173-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-07-05 18:58:57,148 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-07-05 18:58:57,156 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-07-05 18:58:57,168 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-07-05 18:58:57,169 DEBUG: nvidia.available: falling back to default
2012-07-05 18:58:57,208 DEBUG: XorgDriverHandler(nvidia_173, nvidia-173, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-07-05 18:58:57,208 DEBUG: NVIDIA accelerated graphics driver not available
2012-07-05 18:58:57,216 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2012-07-05 18:58:57,228 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2012-07-05 18:58:57,230 DEBUG: nvidia.available: falling back to default
2012-07-05 18:58:57,251 DEBUG: XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-07-05 18:58:57,251 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-07-05 18:58:57,251 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-07-05 18:58:57,371 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-07-05 18:58:57,372 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-07-05 18:58:57,373 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-07-05 18:58:57,373 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-07-05 18:58:57,394 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-07-05 18:58:57,435 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-07-05 18:58:57,435 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-07-05 18:58:57,437 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2012-07-05 18:58:57,446 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2012-07-05 18:58:57,451 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2012-07-05 18:58:57,481 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2012-07-05 18:58:57,481 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-07-05 18:58:57,508 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-07-05 18:58:57,546 DEBUG: Software modem not available
2012-07-05 18:58:57,547 DEBUG: all custom handlers loaded
2012-07-05 18:58:57,547 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2642d40> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-07-05 18:58:57,547 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2642d40> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2012-07-05 18:58:57,561 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-05 18:58:57,712 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:58:57,713 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2642d40> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-07-05 18:58:57,713 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2642d40> about HardwareID('modalias', 'acpi:PNP0103:')
2012-07-05 18:58:57,713 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2642d40> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001458sd0000E000bc02sc00i00')
2012-07-05 18:58:57,722 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2012-07-05 18:58:57,722 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:58:57,723 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2642d40> about HardwareID('modalias', 'platform:pcspkr')
2012-07-05 18:58:57,723 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2012-07-05 18:58:57,723 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:58:57,723 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2012-07-05 18:58:57,723 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:58:57,723 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2642d40> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-07-05 18:58:57,735 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2642d40> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-07-05 18:58:57,735 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-05 18:58:57,735 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:58:57,735 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-07-05 18:58:57,735 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:58:57,735 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2642d40> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-07-05 18:58:57,735 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2642d40> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2012-07-05 18:58:57,736 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2642d40> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-07-05 18:58:57,736 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2642d40> about HardwareID('modalias', 'wmi:ABBC0F6A-8EA1-11D1-00A0-C90629100000')
2012-07-05 18:58:57,736 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2642d40> about HardwareID('modalias', 'pci:v00001002d00009501sv0000174Bsd0000E620bc03sc00i00')
2012-07-05 18:58:58,003 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2012-07-05 18:58:58,003 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:58:58,003 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx'}
2012-07-05 18:58:58,115 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:58:58,115 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-07-05 18:58:58,003 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2012-07-05 18:58:58,260 DEBUG: fglrx.available: falling back to default
2012-07-05 18:58:58,293 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:58:58,293 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-07-05 18:58:58,276 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2012-07-05 18:58:58,372 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2012-07-05 18:58:58,397 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:58:58,397 DEBUG: fglrx_updates is not the alternative in use
2012-07-05 18:58:58,372 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-07-05 18:58:58,406 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-07-05 18:58:58,417 DEBUG: fglrx.available: falling back to default
2012-07-05 18:58:58,469 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:58:58,469 DEBUG: fglrx_updates is not the alternative in use
2012-07-05 18:58:58,454 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-07-05 18:58:58,469 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2012-07-05 18:58:58,482 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:58:58,482 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-07-05 18:58:58,469 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2012-07-05 18:58:58,569 DEBUG: fglrx.available: falling back to default
2012-07-05 18:58:58,631 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:58:58,632 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-07-05 18:58:58,601 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2012-07-05 18:58:58,722 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2642d40> about HardwareID('modalias', 'pci:v00001002d00004383sv00001458sd0000A002bc04sc03i00')
2012-07-05 18:58:58,730 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-07-05 18:58:58,730 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:58:58,730 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-07-05 18:58:58,730 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:58:58,730 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2642d40> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-07-05 18:58:58,730 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2642d40> about HardwareID('modalias', 'acpi:PNP0800:')
2012-07-05 18:58:58,730 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2642d40> about HardwareID('modalias', 'acpi:PNP0000:')
2012-07-05 18:58:58,731 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2642d40> about HardwareID('modalias', 'pci:v00001002d0000AA18sv0000174Bsd0000AA18bc04sc03i00')
2012-07-05 18:58:58,734 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-07-05 18:58:58,734 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:58:58,734 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-07-05 18:58:58,734 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:58:58,734 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2642d40> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001458sd00005002bc01sc01i8a')
2012-07-05 18:58:58,738 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pata_atiixp'}
2012-07-05 18:58:58,738 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_atiixp', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:58:58,738 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2642d40> about HardwareID('modalias', 'acpi:PNP0100:')
2012-07-05 18:58:58,738 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2642d40> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2012-07-05 18:58:58,749 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2642d40> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2012-07-05 18:58:58,749 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2642d40> about HardwareID('modalias', 'usb:v0461p4EBCd0104dc00dsc00dp00ic03isc01ip01')
2012-07-05 18:58:58,750 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-07-05 18:58:58,750 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:58:58,751 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2012-07-05 18:58:58,751 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:58:58,751 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2642d40> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2012-07-05 18:58:58,751 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-05 18:58:58,751 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:58:58,751 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2642d40> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-07-05 18:58:58,751 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-05 18:58:58,751 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:58:58,751 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2642d40> about HardwareID('modalias', 'input:b0003v0461p4EBCe0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8C,8E,96,98,9E,9F,A1,A3,A4,A5,A6,AD,B0,B1,B2,B3,B4,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2012-07-05 18:58:58,751 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-05 18:58:58,751 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:58:58,751 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-07-05 18:58:58,752 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:58:58,752 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2642d40> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2012-07-05 18:58:58,752 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2642d40> about HardwareID('modalias', 'input:b0003v046DpC05Be0111-e0,1,2,4,k110,111,112,113,114,115,116,117,r0,1,6,8,am4,lsfw')
2012-07-05 18:58:58,752 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-05 18:58:58,752 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:58:58,752 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-07-05 18:58:58,752 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:58:58,752 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2642d40> about HardwareID('modalias', 'dmi:bvnAwardSoftwareInternational,Inc.:bvrF10:bd03/22/2011:svnGigabyteTechnologyCo.,Ltd.:pnGA-MA770T-UD3:pvr:rvnGigabyteTechnologyCo.,Ltd.:rnGA-MA770T-UD3:rvr:cvnGigabyteTechnologyCo.,Ltd.:ct3:cvr:')
2012-07-05 18:58:58,765 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2642d40> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-07-05 18:58:58,765 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2642d40> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2012-07-05 18:58:58,765 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'amd64_edac_mod'}
2012-07-05 18:58:58,766 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'amd64_edac_mod', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:58:58,766 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2642d40> about HardwareID('modalias', 'input:b0003v0461p4EBCe0110-e0,1,4,k71,72,73,74,80,8C,8E,8F,90,9B,9C,9E,9F,A1,A3,A4,A5,A6,AB,AC,AD,D9,ram4,lsfw')
2012-07-05 18:58:58,766 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-05 18:58:58,766 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:58:58,766 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-07-05 18:58:58,766 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:58:58,766 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2642d40> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-07-05 18:58:58,766 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2642d40> about HardwareID('modalias', 'usb:v1B1Cp0AB1d0100dc00dsc00dp00ic08isc06ip50')
2012-07-05 18:58:58,767 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uas'}
2012-07-05 18:58:58,767 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uas', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:58:58,767 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2642d40> about HardwareID('modalias', 'pci:v00001002d00004396sv00001458sd00005004bc0Csc03i20')
2012-07-05 18:58:58,770 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2642d40> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-07-05 18:58:58,770 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-05 18:58:58,770 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:58:58,770 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2642d40> about HardwareID('modalias', 'pci:v00001002d00004390sv00001458sd0000B002bc01sc06i01')
2012-07-05 18:58:58,774 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2642d40> about HardwareID('modalias', 'usb:v0461p4EBCd0104dc00dsc00dp00ic03isc00ip00')
2012-07-05 18:58:58,774 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-07-05 18:58:58,774 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:58:58,774 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2642d40> about HardwareID('modalias', 'pci:v00001002d00005957sv00001002sd00005957bc06sc00i00')
2012-07-05 18:58:58,778 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2642d40> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-07-05 18:58:58,778 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2642d40> about HardwareID('modalias', 'usb:v046DpC05Bd5400dc00dsc00dp00ic03isc01ip02')
2012-07-05 18:58:58,799 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-07-05 18:58:58,799 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:58:58,799 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2012-07-05 18:58:58,799 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:58:58,799 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2642d40> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2012-07-05 18:58:58,800 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'k10temp'}
2012-07-05 18:58:58,800 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k10temp', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:58:58,800 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2642d40> about HardwareID('modalias', 'pci:v00001002d00004385sv00001458sd00004385bc0Csc05i00')
2012-07-05 18:58:58,803 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4'}
2012-07-05 18:58:58,803 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:58:58,803 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco'}
2012-07-05 18:58:58,804 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:58:58,804 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2642d40> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-07-05 18:58:58,807 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2642d40> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2012-07-05 18:58:58,814 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-07-05 18:58:58,814 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:58:58,814 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2642d40> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2012-07-05 18:58:58,814 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-05 18:58:58,814 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-05 18:58:58,814 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2642d40> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001002sd0000439Dbc06sc01i00')
2012-07-05 18:58:58,817 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2642d40> about HardwareID('modalias', 'acpi:PNP0200:')
2012-07-05 18:58:58,818 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29bc2d8> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-07-05 18:58:58,818 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29bc2d8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2012-07-05 18:58:58,818 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29bc2d8> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-07-05 18:58:58,818 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29bc2d8> about HardwareID('modalias', 'acpi:PNP0103:')
2012-07-05 18:58:58,818 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29bc2d8> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001458sd0000E000bc02sc00i00')
2012-07-05 18:58:58,818 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29bc2d8> about HardwareID('modalias', 'platform:pcspkr')
2012-07-05 18:58:58,818 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29bc2d8> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-07-05 18:58:58,818 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29bc2d8> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-07-05 18:58:58,818 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29bc2d8> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-07-05 18:58:58,818 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29bc2d8> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2012-07-05 18:58:58,818 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29bc2d8> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-07-05 18:58:58,818 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29bc2d8> about HardwareID('modalias', 'wmi:ABBC0F6A-8EA1-11D1-00A0-C90629100000')
2012-07-05 18:58:58,818 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29bc2d8> about HardwareID('modalias', 'pci:v00001002d00009501sv0000174Bsd0000E620bc03sc00i00')
2012-07-05 18:58:58,818 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29bc2d8> about HardwareID('modalias', 'pci:v00001002d00004383sv00001458sd0000A002bc04sc03i00')
2012-07-05 18:58:58,818 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29bc2d8> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-07-05 18:58:58,818 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29bc2d8> about HardwareID('modalias', 'acpi:PNP0800:')
2012-07-05 18:58:58,819 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29bc2d8> about HardwareID('modalias', 'acpi:PNP0000:')
2012-07-05 18:58:58,819 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29bc2d8> about HardwareID('modalias', 'pci:v00001002d0000AA18sv0000174Bsd0000AA18bc04sc03i00')
2012-07-05 18:58:58,819 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29bc2d8> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001458sd00005002bc01sc01i8a')
2012-07-05 18:58:58,819 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29bc2d8> about HardwareID('modalias', 'acpi:PNP0100:')
2012-07-05 18:58:58,819 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29bc2d8> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2012-07-05 18:58:58,819 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29bc2d8> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2012-07-05 18:58:58,819 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29bc2d8> about HardwareID('modalias', 'usb:v0461p4EBCd0104dc00dsc00dp00ic03isc01ip01')
2012-07-05 18:58:58,819 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29bc2d8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2012-07-05 18:58:58,819 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29bc2d8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-07-05 18:58:58,819 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29bc2d8> about HardwareID('modalias', 'input:b0003v0461p4EBCe0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8C,8E,96,98,9E,9F,A1,A3,A4,A5,A6,AD,B0,B1,B2,B3,B4,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2012-07-05 18:58:58,819 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29bc2d8> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2012-07-05 18:58:58,819 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29bc2d8> about HardwareID('modalias', 'input:b0003v046DpC05Be0111-e0,1,2,4,k110,111,112,113,114,115,116,117,r0,1,6,8,am4,lsfw')
2012-07-05 18:58:58,819 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29bc2d8> about HardwareID('modalias', 'dmi:bvnAwardSoftwareInternational,Inc.:bvrF10:bd03/22/2011:svnGigabyteTechnologyCo.,Ltd.:pnGA-MA770T-UD3:pvr:rvnGigabyteTechnologyCo.,Ltd.:rnGA-MA770T-UD3:rvr:cvnGigabyteTechnologyCo.,Ltd.:ct3:cvr:')
2012-07-05 18:58:58,819 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29bc2d8> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-07-05 18:58:58,819 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29bc2d8> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2012-07-05 18:58:58,819 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29bc2d8> about HardwareID('modalias', 'input:b0003v0461p4EBCe0110-e0,1,4,k71,72,73,74,80,8C,8E,8F,90,9B,9C,9E,9F,A1,A3,A4,A5,A6,AB,AC,AD,D9,ram4,lsfw')
2012-07-05 18:58:58,819 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29bc2d8> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-07-05 18:58:58,819 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29bc2d8> about HardwareID('modalias', 'usb:v1B1Cp0AB1d0100dc00dsc00dp00ic08isc06ip50')
2012-07-05 18:58:58,819 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29bc2d8> about HardwareID('modalias', 'pci:v00001002d00004396sv00001458sd00005004bc0Csc03i20')
2012-07-05 18:58:58,820 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29bc2d8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-07-05 18:58:58,820 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29bc2d8> about HardwareID('modalias', 'pci:v00001002d00004390sv00001458sd0000B002bc01sc06i01')
2012-07-05 18:58:58,820 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29bc2d8> about HardwareID('modalias', 'usb:v0461p4EBCd0104dc00dsc00dp00ic03isc00ip00')
2012-07-05 18:58:58,820 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29bc2d8> about HardwareID('modalias', 'pci:v00001002d00005957sv00001002sd00005957bc06sc00i00')
2012-07-05 18:58:58,820 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29bc2d8> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-07-05 18:58:58,820 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29bc2d8> about HardwareID('modalias', 'usb:v046DpC05Bd5400dc00dsc00dp00ic03isc01ip02')
2012-07-05 18:58:58,820 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29bc2d8> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2012-07-05 18:58:58,820 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29bc2d8> about HardwareID('modalias', 'pci:v00001002d00004385sv00001458sd00004385bc0Csc05i00')
2012-07-05 18:58:58,820 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29bc2d8> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-07-05 18:58:58,820 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29bc2d8> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2012-07-05 18:58:58,820 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29bc2d8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2012-07-05 18:58:58,820 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29bc2d8> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001002sd0000439Dbc06sc01i00')
2012-07-05 18:58:58,820 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29bc2d8> about HardwareID('modalias', 'acpi:PNP0200:')
2012-07-05 18:58:58,881 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:58:58,881 DEBUG: fglrx_updates is not the alternative in use
2012-07-05 18:58:58,986 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:58:58,986 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-07-05 18:58:59,161 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:58:59,161 DEBUG: fglrx_updates is not the alternative in use
2012-07-05 18:58:59,205 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:58:59,205 DEBUG: fglrx_updates is not the alternative in use
2012-07-05 18:58:59,249 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:58:59,250 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-07-05 18:59:02,824 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:59:02,826 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-07-05 18:59:04,040 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:59:04,040 DEBUG: fglrx_updates is not the alternative in use
2012-07-05 18:59:05,584 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:59:05,585 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-07-05 18:59:06,314 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:59:06,314 DEBUG: fglrx_updates is not the alternative in use
2012-07-05 18:59:23,376 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 18:59:23,376 DEBUG: fglrx_updates is not the alternative in use
2012-07-05 18:59:31,827 DEBUG: Installing package: fglrx-updates
2012-07-05 18:59:33,655 DEBUG: install progress dpkg-exec 0.000000
2012-07-05 18:59:35,983 DEBUG: install progress fglrx-amdcccle 0.000000
2012-07-05 18:59:36,084 DEBUG: install progress fglrx-amdcccle 6.250000
2012-07-05 18:59:36,104 DEBUG: install progress fglrx-amdcccle 12.500000
2012-07-05 18:59:36,384 DEBUG: install progress fglrx-amdcccle 18.750000
2012-07-05 18:59:36,862 DEBUG: install progress fglrx 18.750000
2012-07-05 18:59:36,963 DEBUG: install progress fglrx 25.000000
2012-07-05 19:00:02,917 DEBUG: install progress fglrx 31.250000
2012-07-05 19:00:03,960 DEBUG: install progress fglrx 37.500000
2012-07-05 19:00:04,147 DEBUG: install progress bamfdaemon 37.500000
2012-07-05 19:00:04,366 DEBUG: install progress ureadahead 37.500000
2012-07-05 19:00:04,594 DEBUG: install progress initramfs-tools 37.500000
2012-07-05 19:00:20,554 DEBUG: install progress libc-bin 37.500000
2012-07-05 19:00:21,000 DEBUG: install progress dpkg-exec 37.500000
2012-07-05 19:00:21,725 DEBUG: install progress fglrx-updates 37.500000
2012-07-05 19:00:21,826 DEBUG: install progress fglrx-updates 43.750000
2012-07-05 19:00:28,765 DEBUG: install progress fglrx-updates 50.000000
2012-07-05 19:00:28,850 DEBUG: install progress fglrx-updates 56.250000
2012-07-05 19:00:29,118 DEBUG: install progress fglrx-amdcccle-updates 56.250000
2012-07-05 19:00:29,218 DEBUG: install progress fglrx-amdcccle-updates 62.500000
2012-07-05 19:00:29,903 DEBUG: install progress fglrx-amdcccle-updates 68.750000
2012-07-05 19:00:30,009 DEBUG: install progress fglrx-amdcccle-updates 75.000000
2012-07-05 19:00:30,127 DEBUG: install progress ureadahead 75.000000
2012-07-05 19:00:30,520 DEBUG: install progress dpkg-exec 75.000000
2012-07-05 19:00:30,562 DEBUG: install progress fglrx-updates 75.000000
2012-07-05 19:00:30,998 DEBUG: install progress fglrx-updates 81.250000
2012-07-05 19:00:54,595 DEBUG: install progress fglrx-updates 87.500000
2012-07-05 19:00:55,043 DEBUG: install progress bamfdaemon 87.500000
2012-07-05 19:00:55,363 DEBUG: install progress fglrx-amdcccle-updates 87.500000
2012-07-05 19:00:55,490 DEBUG: install progress fglrx-amdcccle-updates 93.750000
2012-07-05 19:00:55,599 DEBUG: install progress fglrx-amdcccle-updates 100.000000
2012-07-05 19:00:55,718 DEBUG: install progress initramfs-tools 100.000000
2012-07-05 19:01:09,484 DEBUG: install progress libc-bin 100.000000
2012-07-05 19:01:11,090 DEBUG: (Reading database ... 170379 files and directories currently installed.)
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
update-alternatives: warning: not replacing /usr/lib/x86_64-linux-gnu/xorg/extra-modules with a link.
update-alternatives: removing manually selected alternative - switching i386-linux-gnu_gl_conf to auto mode
update-alternatives: using /usr/lib/pxpress/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-alternatives: using /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: not replacing /usr/lib/x86_64-linux-gnu/xorg/extra-modules with a link.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-26-generic
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Selecting previously unselected package fglrx-updates.
(Reading database ... 170109 files and directories currently installed.)
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
Building only for 3.2.0-26-generic
Building for architecture x86_64
Building initial module for 3.2.0-26-generic
Done.

fglrx_updates:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-26-generic/updates/dkms/

depmod....

DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Setting up fglrx-amdcccle-updates (2:8.960-0ubuntu1) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-26-generic
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

2012-07-05 19:01:11,351 WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver
2012-07-05 19:01:32,771 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 19:01:32,772 DEBUG: fglrx_updates is not the alternative in use
2012-07-05 19:01:32,791 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 19:01:32,792 DEBUG: fglrx_updates is not the alternative in use
2012-07-05 19:01:41,347 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 19:01:41,348 DEBUG: fglrx_updates is not the alternative in use
2012-07-05 19:01:41,385 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 19:01:41,386 DEBUG: fglrx_updates is not the alternative in use
2012-07-05 19:01:41,454 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 19:01:41,455 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-07-05 19:01:41,678 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 19:01:41,679 DEBUG: fglrx_updates is not the alternative in use
2012-07-05 19:01:41,716 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 19:01:41,716 DEBUG: fglrx_updates is not the alternative in use
2012-07-05 19:01:41,816 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 19:01:41,816 DEBUG: fglrx_updates is not the alternative in use
2012-07-05 19:01:41,854 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 19:01:41,855 DEBUG: fglrx_updates is not the alternative in use
2012-07-05 19:01:41,918 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-05 19:01:41,919 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking[/PHP]

---

### Post by msammels on 2012-07-05
Hi - are you able to set this manually via the nvidia-settings control panel?

---

### Post by filip007 on 2012-07-05
In ATi control panel, if i disable one output, i can get 1600x1200 but that's for 4:3 resolution. 

[IMG]http://shrani.si/f/3Z/hR/B87GcR2/ati.jpg[/IMG]

---

### Post by QIII on 2012-07-05
Jockey does not always work.  Same for fglrx-updates fglrx-amdcccle-updates.

You can try

```
sudo apt-get remove --purge fglrx-updates fglrx-amdcccle-updates
```

and then follow the instructions in the ATI wiki in my signature under

"Using the Ubuntu repositories (alternate command line method, including hardware acceleration)"

---

### Post by QIII on 2012-07-05
> **msammels said:**
> Hi - are you able to set this manually via the nvidia-settings control panel?

Again, msammels, I know you are trying to be helpful.  But that is not an NVIDIA card, so this will be of no use.

---

### Post by filip007 on 2012-07-05
Well DVI cable, did save the problem at resolution, but still, maybe that DVI-VGA adapter has limitations that i use. 
Before installing 3D driver, resolution was just fine, that's what i am trying to say.

No can do that command i was trying install the same second driver on the list, than looks like corruption happened and black screen and can't boot any more.

Clean install with DVI cable, and i will try to switch cable again at the end.:neutral:

---

### Post by QIII on 2012-07-05
When you reinstalled the fglrx driver, did you remember to do

```
sudo aticonfig --initial
```

---

### Post by filip007 on 2012-07-07
Well looks like i need to send this to AMD instead not here, ATI Binary driver failed to work as 1680x1500 when DVI-VGA adapter is used on HD3870, driver version 8.96.

I have than install ATI Binary from Ubuntu Center, that driver worked...not sure about 2D/3D frequencies do they work, can't find that in CP from Catalyst.

I remember now, in the past i was able to install main driver, that one has power management enabled...

---

