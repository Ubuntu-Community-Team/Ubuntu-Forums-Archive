---
title: "Wrong screen resulution"
date: 2012-08-13
forum: Desktop Environments
---

### Post by wombawomba on 2012-08-13
Ubuntu 12.04 gnome. 

I can't get the resolution higher than 1280-720. 
The screen is 22" and has a resolution of 1920-1080. 
Ubuntu thinks the screen is a laptop screen. a box pop up whit that. 
the cabel is a blue vga. 

The resolution has been 1920-1080 for the last year but something happend last week and i don't no what.

---

### Post by cortman on 2012-08-13
> **wombawomba said:**
> Ubuntu 12.04 gnome. 

I can't get the resolution higher than 1280-720. 
The screen is 22" and has a resolution of 1920-1080. 
Ubuntu thinks the screen is a laptop screen. a box pop up whit that. 
the cabel is a blue vga. 

The resolution has been 1920-1080 for the last year but something happend last week and i don't no what.

What's the output of

```
xrandr
```

in a terminal?

---

### Post by gelliott on 2012-08-13
I'm seeing the same problem also. 12.04 is see my display as a laptop not a desktop PC 22" AOC monitor 

xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1280 x 1024, maximum 1280 x 1024
default connected 1280x1024+0+0 0mm x 0mm
   1280x1024       0.0* 
   1024x768        0.0  
   800x600         0.0  
   640x480         0.0

---

### Post by cortman on 2012-08-13
Hi, what's the output of

```

lspci | grep -i vga
lshw -C video
```

---

### Post by wombawomba on 2012-08-13
The menu bars at ubuntu is missing so I cant close anything. I don't know what the problem is but it can't be good... I cant open anything else that dosent are at the desktop...

But now the resolution is right.

xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 1920 x 1080, maximum 1920 x 1080
default connected 1920x1080+0+0 0mm x 0mm
   1920x1080      50.0*    51.0  
   1680x1050      52.0     53.0     54.0     55.0  
   1600x1024      56.0  
   1600x900       57.0  
   1440x900       58.0  
   1400x1050      59.0     60.0     61.0  
   1360x768       62.0     63.0  
   1280x1024      64.0     65.0  
   1280x960       66.0  
   1280x800       67.0  
   1280x720       68.0  
   1152x864       69.0     70.0     71.0     72.0  
   1024x768       73.0     74.0     75.0  
   1024x576       76.0  
   960x600        77.0  
   960x540        78.0  
   896x672        79.0  
   840x525        80.0     81.0     82.0     83.0  
   832x624        84.0  
   800x600        85.0     86.0     87.0     88.0     89.0     90.0  
   800x512        91.0  
   720x450        92.0  
   680x384        93.0     94.0  
   640x512        95.0     96.0  
   640x480        97.0     98.0     99.0    100.0    101.0  
   576x432       102.0    103.0    104.0    105.0  
   512x384       106.0    107.0    108.0  
   416x312       109.0  
   400x300       110.0    111.0    112.0    113.0  
   320x240       114.0    115.0    116.0  


~$ lspci | grep -i vga
00:10.0 VGA compatible controller: NVIDIA Corporation C73 [GeForce 7100 / nForce 630i] (rev a2)




lshw -C video
VARNING: du bör köra detta program som superanvändaren.
  *-display               
       beskrivning: VGA compatible controller
       produkt: C73 [GeForce 7100 / nForce 630i]
       tillverkare: NVIDIA Corporation
       physical id: 10
       bus info: pci@0000:00:10.0
       version: a2
       bredd: 64 bits
       klocka: 66MHz
       förmågor: vga_controller bus_master cap_list rom
       konfiguration: driver=nvidia latency=0
       resurser: irq:22 memory:e2000000-e2ffffff memory:d0000000-dfffffff memory:e3000000-e3ffffff memory:cff00000-cff1ffff
VARNING: utskrifter kan vara ofullständiga eller felaktiga. Du bör köra detta program som superanvändaren.

---

### Post by cortman on 2012-08-13
Sounds like a driver issue- you can use the Nvidia drivers by following [these instructions]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia").

---

### Post by gelliott on 2012-08-14
Here what I'm seeing
lspci | grep -i vga
02:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce 8400 GS] (rev a2)

lshw -c video
WARNING: you should run this program as super-user.
PCI (sysfs)  

  *-display UNCLAIMED     
       description: VGA compatible controller
       product: GT218 [GeForce 8400 GS]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:df000000-dfffffff memory:c0000000-cfffffff memory:dc000000-ddffffff ioport:ec00(size=128) memory:def80000-deffffff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

---

### Post by gelliott on 2012-08-14
When I tried the additional diver update

Sorry, installation of this driver failed.

Please have a look at the log file for details: /var/log/jockey.log 

The log
                                   2012-08-14 07:43:48,946 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f0d0c> 
 2012-08-14 07:43:52,242 DEBUG: reading modalias file /lib/modules/3.0.0-13-generic-pae/modules.alias 
 2012-08-14 07:43:52,370 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43 
 2012-08-14 07:43:52,376 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia 
 2012-08-14 07:43:52,453 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py 
 2012-08-14 07:43:52,494 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci 
  
 2012-08-14 07:43:52,494 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler 
 2012-08-14 07:43:52,494 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool 
 2012-08-14 07:43:52,494 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py 
 2012-08-14 07:43:52,544 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96 
  
 2012-08-14 07:43:52,548 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96 
 2012-08-14 07:43:52,549 DEBUG: nvidia.available: falling back to default 
 2012-08-14 07:43:52,751 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11 
 2012-08-14 07:43:52,752 DEBUG: NVIDIA accelerated graphics driver not available 
 2012-08-14 07:43:52,754 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current 
  
 2012-08-14 07:43:52,759 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent 
 2012-08-14 07:43:52,759 DEBUG: nvidia.available: falling back to default 
 2012-08-14 07:43:52,787 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool 
 2012-08-14 07:43:52,790 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates 
  
 2012-08-14 07:43:52,794 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates 
 2012-08-14 07:43:52,795 DEBUG: nvidia.available: falling back to default 
 2012-08-14 07:43:52,823 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool 
 2012-08-14 07:43:52,826 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates 
  
 2012-08-14 07:43:52,830 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates 
 2012-08-14 07:43:52,831 DEBUG: nvidia.available: falling back to default 
 2012-08-14 07:43:52,859 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool 
 2012-08-14 07:43:52,862 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173 
  
 2012-08-14 07:43:52,866 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173 
 2012-08-14 07:43:52,867 DEBUG: nvidia.available: falling back to default 
 2012-08-14 07:43:52,896 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool 
 2012-08-14 07:43:52,899 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates 
  
 2012-08-14 07:43:52,903 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates 
 2012-08-14 07:43:52,904 DEBUG: nvidia.available: falling back to default 
 2012-08-14 07:43:52,917 DEBUG: XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11 
 2012-08-14 07:43:52,917 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available 
 2012-08-14 07:43:52,917 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py 
 2012-08-14 07:43:52,921 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet 
  
 2012-08-14 07:43:52,921 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler 
 2012-08-14 07:43:52,965 DEBUG: VMWare Client Tools availability undetermined, adding to pool 
 2012-08-14 07:43:52,966 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py 
 2012-08-14 07:43:52,971 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr 
  
 2012-08-14 07:43:52,975 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver 
 2012-08-14 07:43:52,998 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available 
 2012-08-14 07:43:52,998 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py 
 2012-08-14 07:43:53,003 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates 
  
 2012-08-14 07:43:53,007 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate 
 2012-08-14 07:43:53,007 DEBUG: fglrx.available: falling back to default 
 2012-08-14 07:43:53,033 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool 
 2012-08-14 07:43:53,036 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx 
  
 2012-08-14 07:43:53,040 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver 
 2012-08-14 07:43:53,040 DEBUG: fglrx.available: falling back to default 
 2012-08-14 07:43:53,066 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool 
 2012-08-14 07:43:53,067 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py 
 2012-08-14 07:43:53,071 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl 
  
 2012-08-14 07:43:53,085 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler 
 2012-08-14 07:43:53,085 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool 
 2012-08-14 07:43:53,085 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py 
 2012-08-14 07:43:53,099 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem 
 2012-08-14 07:43:53,125 DEBUG: Software modem not available 
 2012-08-14 07:43:53,125 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py 
 2012-08-14 07:43:53,195 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler 
 2012-08-14 07:43:53,195 DEBUG: Firmware for DVB cards not available 
 2012-08-14 07:43:53,195 DEBUG: all custom handlers loaded 
 2012-08-14 07:43:53,195 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f0d0c> about HardwareID('modalias', 'pci:v000010DEd000003EBsv00001043sd000083A4bc0Csc05i00') 
 2012-08-14 07:43:53,479 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_nforce2'} 
 2012-08-14 07:43:53,613 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_nforce2', 'jockey_handler': 'KernelModuleHandler'} 
 2012-08-14 07:43:53,613 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f0d0c> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00') 
 2012-08-14 07:43:53,627 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'k10temp'} 
 2012-08-14 07:43:53,627 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k10temp', 'jockey_handler': 'KernelModuleHandler'} 
 2012-08-14 07:43:53,627 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f0d0c> about HardwareID('modalias', 'acpi:PNP0B00:') 
 2012-08-14 07:43:53,627 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f0d0c> about HardwareID('modalias', 'acpi:PNP0800:') 
 2012-08-14 07:43:53,627 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f0d0c> about HardwareID('modalias', 'pci:v000010DEd000003F5sv00001043sd000083A4bc05sc00i00') 
 2012-08-14 07:43:53,631 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f0d0c> about HardwareID('modalias', 'platform:eisa') 
 2012-08-14 07:43:53,632 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f0d0c> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00') 
 2012-08-14 07:43:53,652 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f0d0c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw') 
 2012-08-14 07:43:53,656 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'} 
 2012-08-14 07:43:53,656 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'} 
 2012-08-14 07:43:53,656 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f0d0c> about HardwareID('modalias', 'acpi:PNP0400:') 
 2012-08-14 07:43:53,656 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f0d0c> about HardwareID('modalias', 'platform:pcspkr') 
 2012-08-14 07:43:53,657 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'} 
 2012-08-14 07:43:53,657 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'} 
 2012-08-14 07:43:53,657 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'} 
 2012-08-14 07:43:53,657 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'} 
 2012-08-14 07:43:53,657 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f0d0c> about HardwareID('modalias', 'pci:v000010DEd000010C3sv00001682sd0000233Abc03sc00i00') 
 2012-08-14 07:43:53,661 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current', 'package': 'nvidia-current'} 
 2012-08-14 07:43:53,762 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf 
 2012-08-14 07:43:53,763 DEBUG: KMH enabled: False 
 2012-08-14 07:43:53,661 DEBUG: found match in handler pool xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver) 
 2012-08-14 07:43:53,765 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current 
  
 2012-08-14 07:43:53,771 DEBUG: nvidia.available: falling back to default 
 2012-08-14 07:43:53,796 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf 
 2012-08-14 07:43:53,796 DEBUG: KMH enabled: False 
 2012-08-14 07:43:53,785 DEBUG: got handler xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver) 
 2012-08-14 07:43:53,796 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current_updates', 'package': 'nvidia-current-updates'} 
 2012-08-14 07:43:53,806 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf 
 2012-08-14 07:43:53,806 DEBUG: nvidia_current_updates is not the alternative in use 
 2012-08-14 07:43:53,796 DEBUG: found match in handler pool xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates)) 
 2012-08-14 07:43:53,809 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates 
  
 2012-08-14 07:43:53,814 DEBUG: nvidia.available: falling back to default 
 2012-08-14 07:43:53,839 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf 
 2012-08-14 07:43:53,839 DEBUG: nvidia_current_updates is not the alternative in use 
 2012-08-14 07:43:53,828 DEBUG: got handler xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates)) 
 2012-08-14 07:43:53,839 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb'} 
 2012-08-14 07:43:53,839 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'} 
 2012-08-14 07:43:53,839 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nouveau'} 
 2012-08-14 07:43:53,839 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nouveau', 'jockey_handler': 'KernelModuleHandler'} 
 2012-08-14 07:43:53,840 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f0d0c> about HardwareID('modalias', 'platform:regulatory') 
 2012-08-14 07:43:53,840 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f0d0c> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00') 
 2012-08-14 07:43:53,840 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f0d0c> about HardwareID('modalias', 'pci:v000010DEd000003E2sv00001043sd000083A4bc05sc00i00') 
 2012-08-14 07:43:53,844 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f0d0c> about HardwareID('modalias', 'acpi:PNP0000:') 
 2012-08-14 07:43:53,844 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f0d0c> about HardwareID('modalias', 'acpi:PNP0100:') 
 2012-08-14 07:43:53,844 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f0d0c> about HardwareID('modalias', 'pci:v000010DEd000003E1sv00001043sd000083A4bc06sc01i00') 
 2012-08-14 07:43:53,848 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f0d0c> about HardwareID('modalias', 'acpi:PNP0C02:') 
 2012-08-14 07:43:53,848 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f0d0c> about HardwareID('modalias', 'acpi:PNP0C01:') 
 2012-08-14 07:43:53,848 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f0d0c> about HardwareID('modalias', 'acpi:PNP0C04:') 
 2012-08-14 07:43:53,848 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f0d0c> about HardwareID('modalias', 'acpi:PNP0501:') 
 2012-08-14 07:43:53,848 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f0d0c> about HardwareID('modalias', 'pci:v000010DEd000003ECsv00001043sd000083A4bc01sc01i8a') 
 2012-08-14 07:43:53,851 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pata_amd'} 
 2012-08-14 07:43:53,852 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_amd', 'jockey_handler': 'KernelModuleHandler'} 
 2012-08-14 07:43:53,852 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f0d0c> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00') 
 2012-08-14 07:43:53,852 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f0d0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,') 
 2012-08-14 07:43:53,852 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'} 
 2012-08-14 07:43:53,852 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'} 
 2012-08-14 07:43:53,852 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f0d0c> about HardwareID('modalias', 'pci:v000010DEd000003F0sv00001043sd00008290bc04sc03i00') 
 2012-08-14 07:43:53,856 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'} 
 2012-08-14 07:43:53,856 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'} 
 2012-08-14 07:43:53,856 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f0d0c> about HardwareID('modalias', 'pci:v000010DEd000003F3sv00001043sd000083A4bc06sc04i01') 
 2012-08-14 07:43:53,859 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f0d0c> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr1103:bd02/04/2010:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnM2N68-AMPlus:rvrRevX.0x:cvnChassisManufacture:ct3:cvrChassisVersion:') 
 2012-08-14 07:43:53,873 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f0d0c> about HardwareID('modalias', 'acpi:PNP0F03:PNP0F13:') 
 2012-08-14 07:43:53,873 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f0d0c> about HardwareID('modalias', 'usb:v050Dp0F51d0006dc00dsc00dp00ic03isc00ip00') 
 2012-08-14 07:43:53,888 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'} 
 2012-08-14 07:43:53,888 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'} 
 2012-08-14 07:43:53,888 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f0d0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00') 
 2012-08-14 07:43:53,888 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f0d0c> about HardwareID('modalias', 'acpi:PNP0103:') 
 2012-08-14 07:43:53,888 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f0d0c> about HardwareID('modalias', 'acpi:LNXSYSTM:') 
 2012-08-14 07:43:53,889 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f0d0c> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00') 
 2012-08-14 07:43:53,889 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f0d0c> about HardwareID('modalias', 'pci:v000010DEd000003F2sv00001043sd000083A4bc0Csc03i20') 
 2012-08-14 07:43:53,892 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f0d0c> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00') 
 2012-08-14 07:43:53,893 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f0d0c> about HardwareID('modalias', 'pci:v000010DEd000003EFsv00001043sd000083A4bc06sc80i00') 
 2012-08-14 07:43:53,896 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'forcedeth'} 
 2012-08-14 07:43:53,896 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'forcedeth', 'jockey_handler': 'KernelModuleHandler'} 
 2012-08-14 07:43:53,896 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f0d0c> about HardwareID('modalias', 'platform:reg-dummy') 
 2012-08-14 07:43:53,897 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f0d0c> about HardwareID('modalias', 'input:b0011v0002p0005e0000-e0,1,2,k110,111,112,r0,1,8,amlsfw') 
 2012-08-14 07:43:53,897 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'} 
 2012-08-14 07:43:53,897 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'} 
 2012-08-14 07:43:53,897 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f0d0c> about HardwareID('modalias', 'acpi:PNP0200:') 
 2012-08-14 07:43:53,897 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f0d0c> about HardwareID('modalias', 'usb:v0846p9040d0106dcFFdscFFdpFFicFFisc00ip00') 
 2012-08-14 07:43:53,904 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'carl9170'} 
 2012-08-14 07:43:53,904 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'carl9170', 'jockey_handler': 'KernelModuleHandler'} 
 2012-08-14 07:43:53,904 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f0d0c> about HardwareID('modalias', 'pci:v000010DEd000003F6sv00001043sd000083A4bc01sc01i85') 
 2012-08-14 07:43:53,908 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sata_nv'} 
 2012-08-14 07:43:53,908 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sata_nv', 'jockey_handler': 'KernelModuleHandler'} 
 2012-08-14 07:43:53,908 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f0d0c> about HardwareID('modalias', 'platform:Fixed MDIO bus') 
 2012-08-14 07:43:53,908 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f0d0c> about HardwareID('modalias', 'serio:ty01pr00id00ex00') 
 2012-08-14 07:43:53,917 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'} 
 2012-08-14 07:43:53,917 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'} 
 2012-08-14 07:43:53,917 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'} 
 2012-08-14 07:43:53,917 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'} 
 2012-08-14 07:43:53,917 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f0d0c> about HardwareID('modalias', 'pci:v000010DEd00000BE3sv00001682sd0000233Abc04sc03i00') 
 2012-08-14 07:43:53,920 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'} 
 2012-08-14 07:43:53,920 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'} 
 2012-08-14 07:43:53,920 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f0d0c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw') 
 2012-08-14 07:43:53,921 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'} 
 2012-08-14 07:43:53,921 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'} 
 2012-08-14 07:43:53,921 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71f0d0c> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:') 
 2012-08-14 07:43:53,921 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f186c> about HardwareID('modalias', 'pci:v000010DEd000003EBsv00001043sd000083A4bc0Csc05i00') 
 2012-08-14 07:43:53,921 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f186c> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00') 
 2012-08-14 07:43:53,921 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f186c> about HardwareID('modalias', 'acpi:PNP0B00:') 
 2012-08-14 07:43:53,921 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f186c> about HardwareID('modalias', 'acpi:PNP0800:') 
 2012-08-14 07:43:53,921 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f186c> about HardwareID('modalias', 'pci:v000010DEd000003F5sv00001043sd000083A4bc05sc00i00') 
 2012-08-14 07:43:53,921 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f186c> about HardwareID('modalias', 'platform:eisa') 
 2012-08-14 07:43:53,921 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f186c> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00') 
 2012-08-14 07:43:53,921 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f186c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw') 
 2012-08-14 07:43:53,921 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f186c> about HardwareID('modalias', 'acpi:PNP0400:') 
 2012-08-14 07:43:53,921 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f186c> about HardwareID('modalias', 'platform:pcspkr') 
 2012-08-14 07:43:53,921 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f186c> about HardwareID('modalias', 'pci:v000010DEd000010C3sv00001682sd0000233Abc03sc00i00') 
 2012-08-14 07:43:53,922 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f186c> about HardwareID('modalias', 'platform:regulatory') 
 2012-08-14 07:43:53,922 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f186c> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00') 
 2012-08-14 07:43:53,922 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f186c> about HardwareID('modalias', 'pci:v000010DEd000003E2sv00001043sd000083A4bc05sc00i00') 
 2012-08-14 07:43:53,922 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f186c> about HardwareID('modalias', 'acpi:PNP0000:') 
 2012-08-14 07:43:53,922 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f186c> about HardwareID('modalias', 'acpi:PNP0100:') 
 2012-08-14 07:43:53,922 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f186c> about HardwareID('modalias', 'pci:v000010DEd000003E1sv00001043sd000083A4bc06sc01i00') 
 2012-08-14 07:43:53,922 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f186c> about HardwareID('modalias', 'acpi:PNP0C02:') 
 2012-08-14 07:43:53,922 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f186c> about HardwareID('modalias', 'acpi:PNP0C01:') 
 2012-08-14 07:43:53,922 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f186c> about HardwareID('modalias', 'acpi:PNP0C04:') 
 2012-08-14 07:43:53,922 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f186c> about HardwareID('modalias', 'acpi:PNP0501:') 
 2012-08-14 07:43:53,922 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f186c> about HardwareID('modalias', 'pci:v000010DEd000003ECsv00001043sd000083A4bc01sc01i8a') 
 2012-08-14 07:43:53,922 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f186c> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00') 
 2012-08-14 07:43:53,922 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f186c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,') 
 2012-08-14 07:43:53,922 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f186c> about HardwareID('modalias', 'pci:v000010DEd000003F0sv00001043sd00008290bc04sc03i00') 
 2012-08-14 07:43:53,922 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f186c> about HardwareID('modalias', 'pci:v000010DEd000003F3sv00001043sd000083A4bc06sc04i01') 
 2012-08-14 07:43:53,923 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f186c> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr1103:bd02/04/2010:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnM2N68-AMPlus:rvrRevX.0x:cvnChassisManufacture:ct3:cvrChassisVersion:') 
 2012-08-14 07:43:53,923 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f186c> about HardwareID('modalias', 'acpi:PNP0F03:PNP0F13:') 
 2012-08-14 07:43:53,923 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f186c> about HardwareID('modalias', 'usb:v050Dp0F51d0006dc00dsc00dp00ic03isc00ip00') 
 2012-08-14 07:43:53,923 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f186c> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00') 
 2012-08-14 07:43:53,923 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f186c> about HardwareID('modalias', 'acpi:PNP0103:') 
 2012-08-14 07:43:53,923 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f186c> about HardwareID('modalias', 'acpi:LNXSYSTM:') 
 2012-08-14 07:43:53,923 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f186c> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00') 
 2012-08-14 07:43:53,923 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f186c> about HardwareID('modalias', 'pci:v000010DEd000003F2sv00001043sd000083A4bc0Csc03i20') 
 2012-08-14 07:43:53,923 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f186c> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00') 
 2012-08-14 07:43:53,923 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f186c> about HardwareID('modalias', 'pci:v000010DEd000003EFsv00001043sd000083A4bc06sc80i00') 
 2012-08-14 07:43:53,923 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f186c> about HardwareID('modalias', 'platform:reg-dummy') 
 2012-08-14 07:43:53,923 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f186c> about HardwareID('modalias', 'input:b0011v0002p0005e0000-e0,1,2,k110,111,112,r0,1,8,amlsfw') 
 2012-08-14 07:43:53,923 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f186c> about HardwareID('modalias', 'acpi:PNP0200:') 
 2012-08-14 07:43:53,923 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f186c> about HardwareID('modalias', 'usb:v0846p9040d0106dcFFdscFFdpFFicFFisc00ip00') 
 2012-08-14 07:43:53,923 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f186c> about HardwareID('modalias', 'pci:v000010DEd000003F6sv00001043sd000083A4bc01sc01i85') 
 2012-08-14 07:43:53,923 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f186c> about HardwareID('modalias', 'platform:Fixed MDIO bus') 
 2012-08-14 07:43:53,924 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f186c> about HardwareID('modalias', 'serio:ty01pr00id00ex00') 
 2012-08-14 07:43:53,924 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f186c> about HardwareID('modalias', 'pci:v000010DEd00000BE3sv00001682sd0000233Abc04sc03i00') 
 2012-08-14 07:43:53,924 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f186c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw') 
 2012-08-14 07:43:53,924 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f186c> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:') 
 2012-08-14 07:43:53,952 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf 
 2012-08-14 07:43:53,952 DEBUG: KMH enabled: False 
 2012-08-14 07:43:55,030 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf 
 2012-08-14 07:43:55,030 DEBUG: nvidia_current_updates is not the alternative in use 
 2012-08-14 07:43:56,025 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf 
 2012-08-14 07:43:56,025 DEBUG: KMH enabled: False 
 2012-08-14 07:43:56,053 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf 
 2012-08-14 07:43:56,053 DEBUG: KMH enabled: False 
 2012-08-14 07:43:56,074 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf 
 2012-08-14 07:43:56,074 DEBUG: nvidia_current_updates is not the alternative in use 
 2012-08-14 07:44:04,004 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf 
 2012-08-14 07:44:04,005 DEBUG: KMH enabled: False 
 2012-08-14 07:44:08,263 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf 
 2012-08-14 07:44:08,264 DEBUG: KMH enabled: False 
 2012-08-14 07:44:17,290 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current 
  
 2012-08-14 07:44:17,290 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting 
 2012-08-14 07:44:47,497 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf 
 2012-08-14 07:44:47,498 DEBUG: KMH enabled: False 
 2012-08-14 07:44:47,510 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf 
 2012-08-14 07:44:47,510 DEBUG: KMH enabled: False 
 2012-08-14 07:44:51,118 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf 
 2012-08-14 07:44:51,118 DEBUG: KMH enabled: False 
 2012-08-14 07:44:51,130 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf 
 2012-08-14 07:44:51,131 DEBUG: KMH enabled: False 
 2012-08-14 07:44:51,153 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf 
 2012-08-14 07:44:51,153 DEBUG: nvidia_current_updates is not the alternative in use 
 2012-08-14 07:44:51,179 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf 
 2012-08-14 07:44:51,180 DEBUG: KMH enabled: False 
 2012-08-14 07:44:51,192 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf 
 2012-08-14 07:44:51,192 DEBUG: KMH enabled: False 
 2012-08-14 07:44:51,223 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf 
 2012-08-14 07:44:51,223 DEBUG: KMH enabled: False 
 2012-08-14 07:44:51,235 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf 
 2012-08-14 07:44:51,235 DEBUG: KMH enabled: False 
 2012-08-14 07:44:51,255 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf 
 2012-08-14 07:44:51,255 DEBUG: nvidia_current_updates is not the alternative in use 
 2012-08-14 07:44:53,666 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf 
 2012-08-14 07:44:53,666 DEBUG: nvidia_current_updates is not the alternative in use 
 2012-08-14 07:45:01,892 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf 
 2012-08-14 07:45:01,892 DEBUG: KMH enabled: False 
 2012-08-14 07:45:01,905 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf 
 2012-08-14 07:45:01,905 DEBUG: KMH enabled: False 
 2012-08-14 07:45:07,034 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf 
 2012-08-14 07:45:07,035 DEBUG: nvidia_current_updates is not the alternative in use 
 2012-08-14 07:45:16,513 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf 
 2012-08-14 07:45:16,514 DEBUG: KMH enabled: False 
 2012-08-14 07:45:16,526 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf 
 2012-08-14 07:45:16,526 DEBUG: KMH enabled: False 
 2012-08-14 07:45:26,002 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf 
 2012-08-14 07:45:26,002 DEBUG: KMH enabled: False 
 2012-08-14 07:45:26,015 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf 
 2012-08-14 07:45:26,015 DEBUG: KMH enabled: False 
 2012-08-14 07:45:26,418 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current 
  
 2012-08-14 07:45:26,419 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting 
 2012-08-14 07:45:46,877 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf 
 2012-08-14 07:45:46,877 DEBUG: KMH enabled: False 
 2012-08-14 07:45:46,890 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf 
 2012-08-14 07:45:46,890 DEBUG: KMH enabled: False

---

### Post by cortman on 2012-08-14
Did you recently upgrade the kernel on your system? If you have multiple kernels you might try booting into an older one.

---

### Post by gelliott on 2012-08-15
id the normal updates, however when I upgraded to 12.04 I must have messed up the menu options, I'm only seeing one kernel + Windows in the menu.

Would a reload of 12.04 help??

---

