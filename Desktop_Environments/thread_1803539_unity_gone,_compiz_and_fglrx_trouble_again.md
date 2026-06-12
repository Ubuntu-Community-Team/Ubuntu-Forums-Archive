---
title: "unity gone, compiz and fglrx trouble again?"
date: 2011-07-13
forum: Desktop Environments
---

### Post by BCingyou on 2011-07-13
Hello all, I have been fighting the good fight, trying to use Ubuntu with an older ATI graphics card (Radeon 4650) on a desktop.  There have been some ups and downs but I finally had everything working with the latest version of Natty, including Unity.  

Recently I ran an update, restarted and got the classic desktop.  When I tried to re-apply unity (unity --reset) I got this error:

Compiz (opengl) - Fatal: glXCreateContext failed

I suspect trouble with the ATI card... again.  I use the proprietary driver (fglrx) but now it seems to be uninstalled.  When I go to reactive it in "additional drivers"... 

Sorry, installation of this driver failed.

Please have a look at the log file for details: /var/log/jockey.log

And when I look there... 

```
2011-07-13 12:12:20,280 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x918db4c>
2011-07-13 12:12:21,724 DEBUG: reading modalias file /lib/modules/2.6.38-10-generic-pae/modules.alias
2011-07-13 12:12:21,832 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2011-07-13 12:12:21,844 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-07-13 12:12:21,907 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-07-13 12:12:21,949 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2011-07-13 12:12:21,949 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-07-13 12:12:21,949 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-07-13 12:12:21,949 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-07-13 12:12:21,990 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-07-13 12:12:21,993 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-07-13 12:12:21,993 DEBUG: fglrx.available: falling back to default
2011-07-13 12:12:22,122 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-07-13 12:12:22,122 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2011-07-13 12:12:22,125 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2011-07-13 12:12:22,125 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2011-07-13 12:12:22,143 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2011-07-13 12:12:22,143 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-07-13 12:12:22,162 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-07-13 12:12:22,186 DEBUG: Software modem not available
2011-07-13 12:12:22,186 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-07-13 12:12:22,201 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-07-13 12:12:22,218 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-07-13 12:12:22,218 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-07-13 12:12:22,218 DEBUG: loading custom handler /usr/share/jockey/handlers/nouveau3d.py
2011-07-13 12:12:22,281 DEBUG: Instantiated Handler subclass __builtin__.Nouveau3DHandler from name Nouveau3DHandler
2011-07-13 12:12:22,281 DEBUG: Experimental 3D support for NVIDIA cards not available
2011-07-13 12:12:22,281 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-07-13 12:12:22,338 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-07-13 12:12:22,338 DEBUG: Firmware for DVB cards not available
2011-07-13 12:12:22,338 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-07-13 12:12:22,343 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2011-07-13 12:12:22,346 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2011-07-13 12:12:22,346 DEBUG: nvidia.available: falling back to default
2011-07-13 12:12:22,362 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI xorg-video-abi-8 does not match X.org video ABI xorg-video-abi-10
2011-07-13 12:12:22,363 DEBUG: NVIDIA accelerated graphics driver not available
2011-07-13 12:12:22,367 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-07-13 12:12:22,369 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2011-07-13 12:12:22,369 DEBUG: nvidia.available: falling back to default
2011-07-13 12:12:22,407 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-07-13 12:12:22,407 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 947, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2011-07-13 12:12:22,423 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-07-13 12:12:22,425 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-07-13 12:12:22,425 DEBUG: nvidia.available: falling back to default
2011-07-13 12:12:22,459 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-07-13 12:12:22,459 DEBUG: all custom handlers loaded
2011-07-13 12:12:22,459 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x918db4c> about HardwareID('modalias', 'pci:v00008086d00003A37sv00001043sd000082D4bc0Csc03i00')
2011-07-13 12:12:22,688 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x918db4c> about HardwareID('modalias', 'pci:v00008086d00003A30sv00001043sd000082D4bc0Csc05i00')
2011-07-13 12:12:22,805 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2011-07-13 12:12:22,805 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x918db4c> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-07-13 12:12:22,805 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x918db4c> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-07-13 12:12:22,805 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x918db4c> about HardwareID('modalias', 'pci:v00008086d00003A38sv00001043sd000082D4bc0Csc03i00')
2011-07-13 12:12:22,808 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x918db4c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-07-13 12:12:22,808 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x918db4c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2011-07-13 12:12:22,828 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x918db4c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-07-13 12:12:22,832 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-13 12:12:22,832 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x918db4c> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-07-13 12:12:22,832 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x918db4c> about HardwareID('modalias', 'platform:pcspkr')
2011-07-13 12:12:22,833 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2011-07-13 12:12:22,833 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2011-07-13 12:12:22,833 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x918db4c> about HardwareID('modalias', 'pci:v00008086d00003A3Asv00001043sd000082D4bc0Csc03i20')
2011-07-13 12:12:22,835 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x918db4c> about HardwareID('modalias', 'platform:eisa')
2011-07-13 12:12:22,836 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x918db4c> about HardwareID('modalias', 'pci:v00008086d00003A26sv00001043sd000082D4bc01sc01i85')
2011-07-13 12:12:22,838 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x918db4c> about HardwareID('modalias', 'pci:v00001002d00009490sv00001787sd00002268bc03sc00i00')
2011-07-13 12:12:23,105 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2011-07-13 12:12:23,108 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-07-13 12:12:23,110 DEBUG: fglrx.available: falling back to default
2011-07-13 12:12:23,987 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-07-13 12:12:23,129 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2011-07-13 12:12:23,987 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x918db4c> about HardwareID('modalias', 'pci:v00008086d00003A3Csv00001043sd000082D4bc0Csc03i20')
2011-07-13 12:12:23,990 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x918db4c> about HardwareID('modalias', 'acpi:PNP0000:')
2011-07-13 12:12:23,990 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x918db4c> about HardwareID('modalias', 'pci:v00008086d00002E20sv00001043sd000082D3bc06sc00i00')
2011-07-13 12:12:23,993 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x918db4c> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-07-13 12:12:23,993 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x918db4c> about HardwareID('modalias', 'pci:v00008086d00003A3Esv00001043sd000082FEbc04sc03i00')
2011-07-13 12:12:23,996 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-07-13 12:12:23,996 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x918db4c> about HardwareID('modalias', 'acpi:PNP0200:')
2011-07-13 12:12:23,996 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x918db4c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-07-13 12:12:23,997 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x918db4c> about HardwareID('modalias', 'usb:v05E3p0723d9451dc00dsc00dp00ic08isc06ip50')
2011-07-13 12:12:24,000 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2011-07-13 12:12:24,000 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uas', 'jockey_handler': 'KernelModuleHandler'}
2011-07-13 12:12:24,000 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2011-07-13 12:12:24,000 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x918db4c> about HardwareID('modalias', 'pci:v00008086d00003A34sv00001043sd000082D4bc0Csc03i00')
2011-07-13 12:12:24,003 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x918db4c> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2011-07-13 12:12:24,010 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2011-07-13 12:12:24,010 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x918db4c> about HardwareID('modalias', 'pci:v00008086d00003A20sv00001043sd000082D4bc01sc01i8f')
2011-07-13 12:12:24,013 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x918db4c> about HardwareID('modalias', 'input:b0003v1BCFp000Ae0111-e0,1,2,3,4,k110,111,112,113,114,r0,1,6,8,a28,m4,lsfw')
2011-07-13 12:12:24,013 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-13 12:12:24,013 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-07-13 12:12:24,013 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x918db4c> about HardwareID('modalias', 'pci:v00001969d00001026sv00001043sd00008226bc02sc00i00')
2011-07-13 12:12:24,016 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'atl1e', 'jockey_handler': 'KernelModuleHandler'}
2011-07-13 12:12:24,016 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x918db4c> about HardwareID('modalias', 'pci:v000011ABd00006121sv00001043sd000082E0bc01sc01i8f')
2011-07-13 12:12:24,038 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-07-13 12:12:24,038 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_marvell', 'jockey_handler': 'KernelModuleHandler'}
2011-07-13 12:12:24,038 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x918db4c> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr1611:bd11/26/2008:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnP5Q:rvrRev1.xx:cvnChassisManufacture:ct3:cvrChassisVersion:')
2011-07-13 12:12:24,050 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x918db4c> about HardwareID('modalias', 'acpi:PNP0800:')
2011-07-13 12:12:24,050 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x918db4c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2011-07-13 12:12:24,050 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'option', 'jockey_handler': 'KernelModuleHandler'}
2011-07-13 12:12:24,050 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x918db4c> about HardwareID('modalias', 'usb:v046DpC315d2800dc00dsc00dp00ic03isc01ip01')
2011-07-13 12:12:24,076 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-07-13 12:12:24,076 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2011-07-13 12:12:24,076 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x918db4c> about HardwareID('modalias', 'acpi:PNP0103:')
2011-07-13 12:12:24,076 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x918db4c> about HardwareID('modalias', 'acpi:PNP0501:')
2011-07-13 12:12:24,076 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x918db4c> about HardwareID('modalias', 'pci:v00008086d00003A16sv00001043sd000082D4bc06sc01i00')
2011-07-13 12:12:24,078 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2011-07-13 12:12:24,078 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x918db4c> about HardwareID('modalias', 'pci:v00008086d00003A39sv00001043sd000082D4bc0Csc03i00')
2011-07-13 12:12:24,081 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x918db4c> about HardwareID('modalias', 'pci:v000011C1d00005811sv00001043sd00008294bc0Csc00i10')
2011-07-13 12:12:24,082 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2011-07-13 12:12:24,082 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x918db4c> about HardwareID('modalias', 'pci:v00008086d00003A35sv00001043sd000082D4bc0Csc03i00')
2011-07-13 12:12:24,084 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x918db4c> about HardwareID('modalias', 'pci:v00001002d0000AA38sv00001787sd0000AA38bc04sc03i00')
2011-07-13 12:12:24,087 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-07-13 12:12:24,087 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-07-13 12:12:24,087 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x918db4c> about HardwareID('modalias', 'acpi:PNP0100:')
2011-07-13 12:12:24,087 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x918db4c> about HardwareID('modalias', 'usb:v1BCFp000Ad0612dc00dsc00dp00ic03isc01ip02')
2011-07-13 12:12:24,088 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-07-13 12:12:24,088 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-07-13 12:12:24,088 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x918db4c> about HardwareID('modalias', 'pci:v00008086d00003A36sv00001043sd000082D4bc0Csc03i00')
2011-07-13 12:12:24,090 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x918db4c> about HardwareID('modalias', 'platform:reg-dummy')
2011-07-13 12:12:24,091 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x918db4c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-07-13 12:12:24,091 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2011-07-13 12:12:24,091 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-07-13 12:12:24,091 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x918db4c> about HardwareID('modalias', 'pci:v00008086d0000244Esv00001043sd000082D4bc06sc04i01')
2011-07-13 12:12:24,093 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x918db4c> about HardwareID('modalias', 'input:b0003v046DpC315e0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2011-07-13 12:12:24,094 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-13 12:12:24,094 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x918db4c> about HardwareID('modalias', 'acpi:INT0800:')
2011-07-13 12:12:24,094 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x919840c> about HardwareID('modalias', 'pci:v00008086d00003A37sv00001043sd000082D4bc0Csc03i00')
2011-07-13 12:12:24,094 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x919840c> about HardwareID('modalias', 'pci:v00008086d00003A30sv00001043sd000082D4bc0Csc05i00')
2011-07-13 12:12:24,094 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x919840c> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-07-13 12:12:24,094 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x919840c> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-07-13 12:12:24,094 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x919840c> about HardwareID('modalias', 'pci:v00008086d00003A38sv00001043sd000082D4bc0Csc03i00')
2011-07-13 12:12:24,094 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x919840c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-07-13 12:12:24,094 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x919840c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2011-07-13 12:12:24,094 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x919840c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-07-13 12:12:24,094 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x919840c> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-07-13 12:12:24,094 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x919840c> about HardwareID('modalias', 'platform:pcspkr')
2011-07-13 12:12:24,094 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x919840c> about HardwareID('modalias', 'pci:v00008086d00003A3Asv00001043sd000082D4bc0Csc03i20')
2011-07-13 12:12:24,094 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x919840c> about HardwareID('modalias', 'platform:eisa')
2011-07-13 12:12:24,095 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x919840c> about HardwareID('modalias', 'pci:v00008086d00003A26sv00001043sd000082D4bc01sc01i85')
2011-07-13 12:12:24,095 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x919840c> about HardwareID('modalias', 'pci:v00001002d00009490sv00001787sd00002268bc03sc00i00')
2011-07-13 12:12:24,095 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x919840c> about HardwareID('modalias', 'pci:v00008086d00003A3Csv00001043sd000082D4bc0Csc03i20')
2011-07-13 12:12:24,095 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x919840c> about HardwareID('modalias', 'acpi:PNP0000:')
2011-07-13 12:12:24,095 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x919840c> about HardwareID('modalias', 'pci:v00008086d00002E20sv00001043sd000082D3bc06sc00i00')
2011-07-13 12:12:24,095 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x919840c> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-07-13 12:12:24,095 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x919840c> about HardwareID('modalias', 'pci:v00008086d00003A3Esv00001043sd000082FEbc04sc03i00')
2011-07-13 12:12:24,095 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x919840c> about HardwareID('modalias', 'acpi:PNP0200:')
2011-07-13 12:12:24,095 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x919840c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-07-13 12:12:24,095 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x919840c> about HardwareID('modalias', 'usb:v05E3p0723d9451dc00dsc00dp00ic08isc06ip50')
2011-07-13 12:12:24,095 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x919840c> about HardwareID('modalias', 'pci:v00008086d00003A34sv00001043sd000082D4bc0Csc03i00')
2011-07-13 12:12:24,095 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x919840c> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2011-07-13 12:12:24,095 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x919840c> about HardwareID('modalias', 'pci:v00008086d00003A20sv00001043sd000082D4bc01sc01i8f')
2011-07-13 12:12:24,095 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x919840c> about HardwareID('modalias', 'input:b0003v1BCFp000Ae0111-e0,1,2,3,4,k110,111,112,113,114,r0,1,6,8,a28,m4,lsfw')
2011-07-13 12:12:24,095 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x919840c> about HardwareID('modalias', 'pci:v00001969d00001026sv00001043sd00008226bc02sc00i00')
2011-07-13 12:12:24,096 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x919840c> about HardwareID('modalias', 'pci:v000011ABd00006121sv00001043sd000082E0bc01sc01i8f')
2011-07-13 12:12:24,096 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x919840c> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr1611:bd11/26/2008:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnP5Q:rvrRev1.xx:cvnChassisManufacture:ct3:cvrChassisVersion:')
2011-07-13 12:12:24,096 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x919840c> about HardwareID('modalias', 'acpi:PNP0800:')
2011-07-13 12:12:24,096 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x919840c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2011-07-13 12:12:24,096 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x919840c> about HardwareID('modalias', 'usb:v046DpC315d2800dc00dsc00dp00ic03isc01ip01')
2011-07-13 12:12:24,096 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x919840c> about HardwareID('modalias', 'acpi:PNP0103:')
2011-07-13 12:12:24,096 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x919840c> about HardwareID('modalias', 'acpi:PNP0501:')
2011-07-13 12:12:24,096 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x919840c> about HardwareID('modalias', 'pci:v00008086d00003A16sv00001043sd000082D4bc06sc01i00')
2011-07-13 12:12:24,096 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x919840c> about HardwareID('modalias', 'pci:v00008086d00003A39sv00001043sd000082D4bc0Csc03i00')
2011-07-13 12:12:24,096 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x919840c> about HardwareID('modalias', 'pci:v000011C1d00005811sv00001043sd00008294bc0Csc00i10')
2011-07-13 12:12:24,096 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x919840c> about HardwareID('modalias', 'pci:v00008086d00003A35sv00001043sd000082D4bc0Csc03i00')
2011-07-13 12:12:24,096 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x919840c> about HardwareID('modalias', 'pci:v00001002d0000AA38sv00001787sd0000AA38bc04sc03i00')
2011-07-13 12:12:24,096 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x919840c> about HardwareID('modalias', 'acpi:PNP0100:')
2011-07-13 12:12:24,096 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x919840c> about HardwareID('modalias', 'usb:v1BCFp000Ad0612dc00dsc00dp00ic03isc01ip02')
2011-07-13 12:12:24,096 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x919840c> about HardwareID('modalias', 'pci:v00008086d00003A36sv00001043sd000082D4bc0Csc03i00')
2011-07-13 12:12:24,097 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x919840c> about HardwareID('modalias', 'platform:reg-dummy')
2011-07-13 12:12:24,097 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x919840c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-07-13 12:12:24,097 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x919840c> about HardwareID('modalias', 'pci:v00008086d0000244Esv00001043sd000082D4bc06sc04i01')
2011-07-13 12:12:24,097 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x919840c> about HardwareID('modalias', 'input:b0003v046DpC315e0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2011-07-13 12:12:24,097 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x919840c> about HardwareID('modalias', 'acpi:INT0800:')
2011-07-13 12:12:24,220 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-07-13 12:12:24,333 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-07-13 12:12:24,362 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-07-13 12:12:33,017 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-07-13 12:12:36,990 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-07-13 12:12:36,991 WARNING: /sys/module/fglrx/drivers does not exist, cannot rebind fglrx driver
2011-07-13 12:12:36,991 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2011-07-13 12:13:00,407 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-07-13 12:13:00,422 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-07-13 12:13:03,210 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-07-13 12:13:03,225 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-07-13 12:13:03,263 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-07-13 12:13:03,279 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-07-13 12:13:03,309 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-07-13 12:13:03,324 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-07-13 12:13:05,081 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-07-13 12:13:05,097 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-07-13 12:13:33,665 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-07-13 12:13:33,680 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-07-13 12:13:34,071 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-07-13 12:13:34,071 WARNING: /sys/module/fglrx/drivers does not exist, cannot rebind fglrx driver
2011-07-13 12:13:34,071 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2011-07-13 12:13:49,327 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-07-13 12:13:49,342 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-07-13 12:14:45,960 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-07-13 12:14:45,975 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-07-13 12:14:46,000 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-07-13 12:14:46,015 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-07-13 12:14:46,074 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-07-13 12:14:46,092 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking

```

I'm baffled, please help!  Thanks in advance.

---

