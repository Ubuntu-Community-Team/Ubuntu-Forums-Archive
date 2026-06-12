---
title: "Unwanted horizontal offset, 12.04"
date: 2012-04-30
forum: Desktop Environments
---

### Post by Sunships on 2012-04-30
Hi all,

I recently installed 12.04, and have found that following boot, my display is horizontally offset, so that much of the left hand side of my desktop is off-screen.

I have been able to adjust the horizontal offset on my monitor manually to make the whole desktop visible, but this means that the display is offset and partially off-screen during boot now instead, relative to the manual offset. This is annoying because it means I can't see things like the GRUB menu, etc.

How can I change this? Ideally I would like to remove/correct the offset in Ubuntu, so I can reset the manual offset I have set on my monitor. I have checked the app for my graphics card, but it doesn't have any function for correcting horizontal offset. Is there another application or setting I can use for this? 

Thanks for your help, and for reading.

---

### Post by mips on 2012-04-30
What gfx card and driver are you using?
What make & model monitor are you using?
What refresh rates do you have specified?
What resolution are you running at?

---

### Post by Sunships on 2012-04-30
Argh, I was hoping it would be an easy tweak to fix :p I am at work right now, but when I get home tonight I will answer all of your queries, mips. Thanks for your response, and for coming to my rescue!

---

### Post by jywarren on 2012-04-30
Tracking a similar issue here: [http://ubuntuforums.org/showthread.php?p=11891011#post11891011](http://ubuntuforums.org/showthread.php?p=11891011#post11891011)

---

### Post by Sunships on 2012-04-30
Thanks jywarren! I will follow with interest. In the meantime, here are my answers for mips' questions:

```
What gfx card and driver are you using?
```
Graphics card: GeForce GTX 460
Driver is the "NVIDIA accelerated graphics driver (version current)", recommended by the Additional Drivers tool.

```
What make & model monitor are you using?
```
Make: UMC, Model: UMC-Q19L04L01G-788

```
What refresh rates do you have specified?
```
The refresh rate, according the NVIDIA X Server Settings tool is set to "Auto". The other options are 60 Hz and 75 Hz.

```
What resolution are you running at?
```
1440x900

Thanks for your help!

---

### Post by Sunships on 2012-05-01
bump - still looking for any help or advice on things to try to fix this.

---

### Post by squilookle on 2012-05-01
What flavour are you using, because i did hit a similar issue in Kubuntu 12.04 (Beta1) but not in Ubuntu or Xubuntu. 

I never solved it though, I just manually reset the monitor like you did and put up with the screen being offset the other way at boot - booting was sufficiently quick that it didn't bother me.

---

### Post by Sunships on 2012-05-01
> **squilookle said:**
> What flavour are you using, because i did hit a similar issue in Kubuntu 12.04 (Beta1) but not in Ubuntu or Xubuntu. 

I never solved it though, I just manually reset the monitor like you did and put up with the screen being offset the other way at boot - booting was sufficiently quick that it didn't bother me.

Hi squilookle, I'm using vanilla Ubuntu 12.04. I downloaded on the day of release, last Thursday. It's true, it's not a massive issue, but it does mean the GRUB menu is not visible during boot, which is a problem for other people who come to use the machine.

---

### Post by squilookle on 2012-05-01
It was annoying. In the end, I chose not to stay with Kubuntu and didn't have the same issue with vanilla Ubuntu. 

Not sure if it helps or is related, but I'm also using an NVidia GeForce card, although I'm not sure of the exact model off the top of my head and I'm not at that computer right now. 

Good luck.

---

### Post by Sunships on 2012-05-04
Still looking for a solution for this, if anyone can help :)

---

### Post by mips on 2012-05-04
Does this also happen if you uninstall the nividia drivers?
I know nvidia release a new driver in the last day or so.

---

### Post by Sunships on 2012-05-04
> **mips said:**
> Does this also happen if you uninstall the nividia drivers?
I know nvidia release a new driver in the last day or so.

Hm, I'll try this. Last time I reinstalled a graphics driver it killed my installation, though! I'll do a fresh install on a separate partition and use that to test the different drivers, so I don't mess up my current set-up :)

Thanks mips!

---

### Post by Sunships on 2012-05-06
Alright, so before I reinstalled I re-set my monitor offset so I could see the whole of my screen during boot - turns out I don't have a GRUB menu anymore and hadn't really noticed due to the offset. Since I wasn't really sure what's going on with that, and will leave that to another thread, I decided to just live dangerously and install the "(post-release updates) (current version updates)" NVIDIA driver, which is the only other option on the Additional Drivers list. 

However....I received an error message saying it couldn't install and I should look at /var/log/jockey to find out why - I'm not sure where to start analysing this file, or if it has any relevant information.

Thanks again for your help guys.

TL: DR - tried the other NVIDIA driver but it wouldn't install. Error log below.

```
2012-05-06 09:06:15,975 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x1de8ea8>
2012-05-06 09:06:17,608 DEBUG: reading modalias file /lib/modules/3.2.0-24-generic/modules.alias
2012-05-06 09:06:17,691 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-05-06 09:06:17,701 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-05-06 09:06:17,775 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-05-06 09:06:17,837 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-05-06 09:06:17,838 DEBUG: Firmware for DVB cards not available
2012-05-06 09:06:17,838 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-05-06 09:06:17,841 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-05-06 09:06:17,853 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-05-06 09:06:17,853 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-05-06 09:06:17,853 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-05-06 09:06:17,869 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-05-06 09:06:17,872 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2012-05-06 09:06:17,872 DEBUG: fglrx.available: falling back to default
2012-05-06 09:06:17,967 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2012-05-06 09:06:17,970 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-05-06 09:06:17,973 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-05-06 09:06:17,974 DEBUG: fglrx.available: falling back to default
2012-05-06 09:06:17,996 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-05-06 09:06:17,996 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-05-06 09:06:18,001 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-05-06 09:06:18,004 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-05-06 09:06:18,005 DEBUG: nvidia.available: falling back to default
2012-05-06 09:06:18,016 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-05-06 09:06:18,016 DEBUG: NVIDIA accelerated graphics driver not available
2012-05-06 09:06:18,022 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-05-06 09:06:18,023 DEBUG: nvidia.available: falling back to default
2012-05-06 09:06:18,044 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-05-06 09:06:18,047 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-05-06 09:06:18,050 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2012-05-06 09:06:18,051 DEBUG: nvidia.available: falling back to default
2012-05-06 09:06:18,074 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-05-06 09:06:18,076 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-05-06 09:06:18,080 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2012-05-06 09:06:18,080 DEBUG: nvidia.available: falling back to default
2012-05-06 09:06:18,091 DEBUG: XorgDriverHandler(nvidia_173_updates, nvidia-173-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-05-06 09:06:18,091 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-05-06 09:06:18,094 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-05-06 09:06:18,097 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-05-06 09:06:18,097 DEBUG: nvidia.available: falling back to default
2012-05-06 09:06:18,108 DEBUG: XorgDriverHandler(nvidia_173, nvidia-173, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-05-06 09:06:18,108 DEBUG: NVIDIA accelerated graphics driver not available
2012-05-06 09:06:18,111 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2012-05-06 09:06:18,114 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2012-05-06 09:06:18,115 DEBUG: nvidia.available: falling back to default
2012-05-06 09:06:18,125 DEBUG: XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-05-06 09:06:18,126 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-05-06 09:06:18,126 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2012-05-06 09:06:18,130 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2012-05-06 09:06:18,133 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2012-05-06 09:06:18,152 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2012-05-06 09:06:18,152 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2012-05-06 09:06:18,155 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2012-05-06 09:06:18,156 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2012-05-06 09:06:18,166 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2012-05-06 09:06:18,167 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-05-06 09:06:18,179 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-05-06 09:06:18,194 DEBUG: Software modem not available
2012-05-06 09:06:18,194 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-05-06 09:06:18,198 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-05-06 09:06:18,198 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-05-06 09:06:18,198 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-05-06 09:06:18,198 DEBUG: all custom handlers loaded
2012-05-06 09:06:18,198 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1de8ea8> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-05-06 09:06:18,198 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1de8ea8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2012-05-06 09:06:18,202 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-06 09:06:18,314 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:06:18,314 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1de8ea8> about HardwareID('modalias', 'acpi:PNP0501:')
2012-05-06 09:06:18,314 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1de8ea8> about HardwareID('modalias', 'acpi:PNP0000:')
2012-05-06 09:06:18,314 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1de8ea8> about HardwareID('modalias', 'pci:v00001033d00000194sv00001043sd00008413bc0Csc03i30')
2012-05-06 09:06:18,316 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1de8ea8> about HardwareID('modalias', 'platform:pcspkr')
2012-05-06 09:06:18,316 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2012-05-06 09:06:18,317 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:06:18,317 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2012-05-06 09:06:18,317 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:06:18,317 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1de8ea8> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp01ic09isc00ip00')
2012-05-06 09:06:18,327 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1de8ea8> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-05-06 09:06:18,327 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-06 09:06:18,327 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:06:18,327 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-05-06 09:06:18,327 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:06:18,327 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1de8ea8> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-05-06 09:06:18,327 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1de8ea8> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2012-05-06 09:06:18,327 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1de8ea8> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-05-06 09:06:18,328 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1de8ea8> about HardwareID('modalias', 'wmi:ABBC0F6A-8EA1-11D1-00A0-C90629100000')
2012-05-06 09:06:18,328 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1de8ea8> about HardwareID('modalias', 'pci:v00001022d00009601sv00001043sd0000843Ebc06sc00i00')
2012-05-06 09:06:18,337 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1de8ea8> about HardwareID('modalias', 'pci:v00001002d00004396sv00001043sd00008443bc0Csc03i20')
2012-05-06 09:06:18,550 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1de8ea8> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-05-06 09:06:18,550 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1de8ea8> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-05-06 09:06:18,550 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1de8ea8> about HardwareID('modalias', 'acpi:PNP0100:')
2012-05-06 09:06:18,550 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1de8ea8> about HardwareID('modalias', 'pci:v000010DEd00000E22sv00001462sd00002322bc03sc00i00')
2012-05-06 09:06:18,721 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb'}
2012-05-06 09:06:18,721 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:06:18,721 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nouveau'}
2012-05-06 09:06:18,721 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nouveau', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:06:18,721 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current'}
2012-05-06 09:06:18,793 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-05-06 09:06:18,912 DEBUG: KMH enabled: True
2012-05-06 09:06:18,722 DEBUG: found match in handler pool xorg:nvidia_current([NvidiaDriverCurrent, nonfree, enabled] NVIDIA accelerated graphics driver)
2012-05-06 09:06:18,998 DEBUG: nvidia.available: falling back to default
2012-05-06 09:06:19,019 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-05-06 09:06:19,101 DEBUG: KMH enabled: True
2012-05-06 09:06:19,010 DEBUG: got handler xorg:nvidia_current([NvidiaDriverCurrent, nonfree, enabled] NVIDIA accelerated graphics driver)
2012-05-06 09:06:19,183 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current', 'package': 'nvidia-current'}
2012-05-06 09:06:19,192 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-05-06 09:06:19,274 DEBUG: KMH enabled: True
2012-05-06 09:06:19,183 DEBUG: found match in handler pool xorg:nvidia_current([NvidiaDriverCurrent, nonfree, enabled] NVIDIA accelerated graphics driver)
2012-05-06 09:06:19,362 DEBUG: nvidia.available: falling back to default
2012-05-06 09:06:19,383 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-05-06 09:06:19,466 DEBUG: KMH enabled: True
2012-05-06 09:06:19,374 DEBUG: got handler xorg:nvidia_current([NvidiaDriverCurrent, nonfree, enabled] NVIDIA accelerated graphics driver)
2012-05-06 09:06:19,551 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current_updates', 'package': 'nvidia-current-updates'}
2012-05-06 09:06:19,560 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-05-06 09:06:19,560 DEBUG: nvidia_current_updates is not the alternative in use
2012-05-06 09:06:19,551 DEBUG: found match in handler pool xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2012-05-06 09:06:19,563 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-05-06 09:06:19,567 DEBUG: nvidia.available: falling back to default
2012-05-06 09:06:19,587 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-05-06 09:06:19,587 DEBUG: nvidia_current_updates is not the alternative in use
2012-05-06 09:06:19,578 DEBUG: got handler xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2012-05-06 09:06:19,587 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1de8ea8> about HardwareID('modalias', 'pci:v00001002d00004390sv00001043sd00008443bc01sc06i01')
2012-05-06 09:06:19,590 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1de8ea8> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-05-06 09:06:19,590 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1de8ea8> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2012-05-06 09:06:19,590 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1de8ea8> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001043sd00008443bc06sc01i00')
2012-05-06 09:06:19,593 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1de8ea8> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2012-05-06 09:06:19,593 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1de8ea8> about HardwareID('modalias', 'usb:v04D9p1203d0270dc00dsc00dp00ic03isc00ip00')
2012-05-06 09:06:19,593 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-05-06 09:06:19,593 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:06:19,593 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1de8ea8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2012-05-06 09:06:19,593 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-06 09:06:19,594 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:06:19,594 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1de8ea8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-05-06 09:06:19,594 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-06 09:06:19,594 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:06:19,594 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1de8ea8> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2012-05-06 09:06:19,600 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-05-06 09:06:19,600 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:06:19,600 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1de8ea8> about HardwareID('modalias', 'input:b0003v04D9p1203e0111-e0,1,4,k71,72,73,74,80,8C,8E,8F,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,AB,AC,AD,D9,ram4,lsfw')
2012-05-06 09:06:19,600 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-06 09:06:19,600 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:06:19,600 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-05-06 09:06:19,600 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:06:19,600 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1de8ea8> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-05-06 09:06:19,600 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1de8ea8> about HardwareID('modalias', 'pci:v00001002d00004383sv00001043sd0000841Bbc04sc03i00')
2012-05-06 09:06:19,603 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-05-06 09:06:19,603 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:06:19,603 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-05-06 09:06:19,603 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:06:19,603 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1de8ea8> about HardwareID('modalias', 'input:b0003v04D9p1203e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2012-05-06 09:06:19,603 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-06 09:06:19,603 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:06:19,603 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-05-06 09:06:19,603 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:06:19,603 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1de8ea8> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr1404:bd05/28/2010:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnM4A88TD-MEVO:rvrRevX.0x:cvnChassisManufacture:ct3:cvrChassisVersion:')
2012-05-06 09:06:19,614 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1de8ea8> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2012-05-06 09:06:19,614 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'amd64_edac_mod'}
2012-05-06 09:06:19,614 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'amd64_edac_mod', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:06:19,614 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1de8ea8> about HardwareID('modalias', 'acpi:PNP0400:')
2012-05-06 09:06:19,614 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1de8ea8> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-05-06 09:06:19,617 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1de8ea8> about HardwareID('modalias', 'input:b0003v1241p1166e0110-e0,1,2,4,k110,111,112,113,114,r0,1,8,am4,lsfw')
2012-05-06 09:06:19,617 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-06 09:06:19,617 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:06:19,617 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-05-06 09:06:19,617 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:06:19,617 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1de8ea8> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-05-06 09:06:19,617 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1de8ea8> about HardwareID('modalias', 'usb:v1D6Bp0003d0302dc09dsc00dp03ic09isc00ip00')
2012-05-06 09:06:19,618 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1de8ea8> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-05-06 09:06:19,618 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1de8ea8> about HardwareID('modalias', 'pci:v00001106d00000415sv00001043sd0000838Fbc01sc01i85')
2012-05-06 09:06:19,632 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pata_via'}
2012-05-06 09:06:19,632 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_via', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:06:19,632 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1de8ea8> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2012-05-06 09:06:19,632 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'k10temp'}
2012-05-06 09:06:19,632 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k10temp', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:06:19,632 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1de8ea8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-05-06 09:06:19,632 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-06 09:06:19,632 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:06:19,632 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1de8ea8> about HardwareID('modalias', 'pci:v00001106d00003403sv00001043sd00008374bc0Csc00i10')
2012-05-06 09:06:19,632 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci'}
2012-05-06 09:06:19,633 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:06:19,633 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1de8ea8> about HardwareID('modalias', 'acpi:PNP0800:')
2012-05-06 09:06:19,633 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1de8ea8> about HardwareID('modalias', 'usb:v1241p1166d0270dc00dsc00dp00ic03isc01ip02')
2012-05-06 09:06:19,633 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-05-06 09:06:19,633 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:06:19,633 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2012-05-06 09:06:19,633 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:06:19,633 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1de8ea8> about HardwareID('modalias', 'pci:v000010DEd00000BEBsv00001462sd00002322bc04sc03i00')
2012-05-06 09:06:19,636 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-05-06 09:06:19,636 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:06:19,636 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1de8ea8> about HardwareID('modalias', 'acpi:PNP0200:')
2012-05-06 09:06:19,636 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1de8ea8> about HardwareID('modalias', 'usb:v04D9p1203d0270dc00dsc00dp00ic03isc01ip01')
2012-05-06 09:06:19,636 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-05-06 09:06:19,636 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:06:19,636 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2012-05-06 09:06:19,636 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:06:19,636 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1de8ea8> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2012-05-06 09:06:19,636 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1de8ea8> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001043sd00008432bc02sc00i00')
2012-05-06 09:06:19,642 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2012-05-06 09:06:19,642 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:06:19,642 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1de8ea8> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001043sd00008443bc01sc01i8a')
2012-05-06 09:06:19,645 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pata_atiixp'}
2012-05-06 09:06:19,645 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_atiixp', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:06:19,645 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1de8ea8> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-05-06 09:06:19,645 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-05-06 09:06:19,645 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:06:19,645 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2012-05-06 09:06:19,645 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:06:19,645 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1de8ea8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2012-05-06 09:06:19,646 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-06 09:06:19,646 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:06:19,646 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1de8ea8> about HardwareID('modalias', 'pci:v00001002d00004385sv00000000sd00000000bc0Csc05i00')
2012-05-06 09:06:19,648 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4'}
2012-05-06 09:06:19,648 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:06:19,648 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco'}
2012-05-06 09:06:19,648 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:06:19,649 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1de8ea8> about HardwareID('modalias', 'acpi:PNP0103:')
2012-05-06 09:06:19,649 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2153830> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-05-06 09:06:19,649 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2153830> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2012-05-06 09:06:19,649 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2153830> about HardwareID('modalias', 'acpi:PNP0501:')
2012-05-06 09:06:19,649 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2153830> about HardwareID('modalias', 'acpi:PNP0000:')
2012-05-06 09:06:19,649 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2153830> about HardwareID('modalias', 'pci:v00001033d00000194sv00001043sd00008413bc0Csc03i30')
2012-05-06 09:06:19,649 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2153830> about HardwareID('modalias', 'platform:pcspkr')
2012-05-06 09:06:19,649 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2153830> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp01ic09isc00ip00')
2012-05-06 09:06:19,649 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2153830> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-05-06 09:06:19,649 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2153830> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-05-06 09:06:19,649 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2153830> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2012-05-06 09:06:19,649 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2153830> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-05-06 09:06:19,649 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2153830> about HardwareID('modalias', 'wmi:ABBC0F6A-8EA1-11D1-00A0-C90629100000')
2012-05-06 09:06:19,649 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2153830> about HardwareID('modalias', 'pci:v00001022d00009601sv00001043sd0000843Ebc06sc00i00')
2012-05-06 09:06:19,649 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2153830> about HardwareID('modalias', 'pci:v00001002d00004396sv00001043sd00008443bc0Csc03i20')
2012-05-06 09:06:19,649 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2153830> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-05-06 09:06:19,649 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2153830> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-05-06 09:06:19,649 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2153830> about HardwareID('modalias', 'acpi:PNP0100:')
2012-05-06 09:06:19,649 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2153830> about HardwareID('modalias', 'pci:v000010DEd00000E22sv00001462sd00002322bc03sc00i00')
2012-05-06 09:06:19,649 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2153830> about HardwareID('modalias', 'pci:v00001002d00004390sv00001043sd00008443bc01sc06i01')
2012-05-06 09:06:19,649 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2153830> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-05-06 09:06:19,649 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2153830> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2012-05-06 09:06:19,650 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2153830> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001043sd00008443bc06sc01i00')
2012-05-06 09:06:19,650 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2153830> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2012-05-06 09:06:19,650 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2153830> about HardwareID('modalias', 'usb:v04D9p1203d0270dc00dsc00dp00ic03isc00ip00')
2012-05-06 09:06:19,650 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2153830> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2012-05-06 09:06:19,650 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2153830> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-05-06 09:06:19,650 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2153830> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2012-05-06 09:06:19,650 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2153830> about HardwareID('modalias', 'input:b0003v04D9p1203e0111-e0,1,4,k71,72,73,74,80,8C,8E,8F,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,AB,AC,AD,D9,ram4,lsfw')
2012-05-06 09:06:19,650 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2153830> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-05-06 09:06:19,650 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2153830> about HardwareID('modalias', 'pci:v00001002d00004383sv00001043sd0000841Bbc04sc03i00')
2012-05-06 09:06:19,650 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2153830> about HardwareID('modalias', 'input:b0003v04D9p1203e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2012-05-06 09:06:19,650 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2153830> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr1404:bd05/28/2010:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnM4A88TD-MEVO:rvrRevX.0x:cvnChassisManufacture:ct3:cvrChassisVersion:')
2012-05-06 09:06:19,650 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2153830> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2012-05-06 09:06:19,650 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2153830> about HardwareID('modalias', 'acpi:PNP0400:')
2012-05-06 09:06:19,650 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2153830> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-05-06 09:06:19,650 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2153830> about HardwareID('modalias', 'input:b0003v1241p1166e0110-e0,1,2,4,k110,111,112,113,114,r0,1,8,am4,lsfw')
2012-05-06 09:06:19,650 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2153830> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-05-06 09:06:19,650 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2153830> about HardwareID('modalias', 'usb:v1D6Bp0003d0302dc09dsc00dp03ic09isc00ip00')
2012-05-06 09:06:19,650 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2153830> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-05-06 09:06:19,650 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2153830> about HardwareID('modalias', 'pci:v00001106d00000415sv00001043sd0000838Fbc01sc01i85')
2012-05-06 09:06:19,650 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2153830> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2012-05-06 09:06:19,650 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2153830> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-05-06 09:06:19,650 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2153830> about HardwareID('modalias', 'pci:v00001106d00003403sv00001043sd00008374bc0Csc00i10')
2012-05-06 09:06:19,651 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2153830> about HardwareID('modalias', 'acpi:PNP0800:')
2012-05-06 09:06:19,651 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2153830> about HardwareID('modalias', 'usb:v1241p1166d0270dc00dsc00dp00ic03isc01ip02')
2012-05-06 09:06:19,651 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2153830> about HardwareID('modalias', 'pci:v000010DEd00000BEBsv00001462sd00002322bc04sc03i00')
2012-05-06 09:06:19,651 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2153830> about HardwareID('modalias', 'acpi:PNP0200:')
2012-05-06 09:06:19,651 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2153830> about HardwareID('modalias', 'usb:v04D9p1203d0270dc00dsc00dp00ic03isc01ip01')
2012-05-06 09:06:19,651 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2153830> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2012-05-06 09:06:19,651 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2153830> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001043sd00008432bc02sc00i00')
2012-05-06 09:06:19,651 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2153830> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001043sd00008443bc01sc01i8a')
2012-05-06 09:06:19,651 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2153830> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-05-06 09:06:19,651 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2153830> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2012-05-06 09:06:19,651 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2153830> about HardwareID('modalias', 'pci:v00001002d00004385sv00000000sd00000000bc0Csc05i00')
2012-05-06 09:06:19,651 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2153830> about HardwareID('modalias', 'acpi:PNP0103:')
2012-05-06 09:06:19,684 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-05-06 09:06:19,769 DEBUG: KMH enabled: True
2012-05-06 09:06:21,109 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-05-06 09:06:21,192 DEBUG: KMH enabled: True
2012-05-06 09:06:21,380 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-05-06 09:06:21,380 DEBUG: nvidia_current_updates is not the alternative in use
2012-05-06 09:06:22,491 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-05-06 09:06:22,491 DEBUG: nvidia_current_updates is not the alternative in use
2012-05-06 09:06:22,517 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-05-06 09:06:22,600 DEBUG: KMH enabled: True
2012-05-06 09:06:22,789 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-05-06 09:06:22,872 DEBUG: KMH enabled: True
2012-05-06 09:06:23,070 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-05-06 09:06:23,154 DEBUG: KMH enabled: True
2012-05-06 09:06:23,341 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-05-06 09:06:23,426 DEBUG: KMH enabled: True
2012-05-06 09:06:34,554 DEBUG: Shutting down
2012-05-06 09:06:36,385 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x159eea8>
2012-05-06 09:06:37,982 DEBUG: reading modalias file /lib/modules/3.2.0-24-generic/modules.alias
2012-05-06 09:06:38,047 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-05-06 09:06:38,047 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-05-06 09:06:38,085 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-05-06 09:06:38,100 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-05-06 09:06:38,100 DEBUG: Firmware for DVB cards not available
2012-05-06 09:06:38,100 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-05-06 09:06:38,103 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-05-06 09:06:38,115 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-05-06 09:06:38,115 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-05-06 09:06:38,116 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-05-06 09:06:38,120 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-05-06 09:06:38,123 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2012-05-06 09:06:38,123 DEBUG: fglrx.available: falling back to default
2012-05-06 09:06:38,189 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2012-05-06 09:06:38,191 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-05-06 09:06:38,195 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-05-06 09:06:38,195 DEBUG: fglrx.available: falling back to default
2012-05-06 09:06:38,217 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-05-06 09:06:38,217 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-05-06 09:06:38,222 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-05-06 09:06:38,225 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-05-06 09:06:38,226 DEBUG: nvidia.available: falling back to default
2012-05-06 09:06:38,237 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-05-06 09:06:38,238 DEBUG: NVIDIA accelerated graphics driver not available
2012-05-06 09:06:38,244 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-05-06 09:06:38,244 DEBUG: nvidia.available: falling back to default
2012-05-06 09:06:38,266 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-05-06 09:06:38,269 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-05-06 09:06:38,272 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2012-05-06 09:06:38,272 DEBUG: nvidia.available: falling back to default
2012-05-06 09:06:38,295 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-05-06 09:06:38,297 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-05-06 09:06:38,301 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2012-05-06 09:06:38,301 DEBUG: nvidia.available: falling back to default
2012-05-06 09:06:38,312 DEBUG: XorgDriverHandler(nvidia_173_updates, nvidia-173-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-05-06 09:06:38,312 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-05-06 09:06:38,315 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-05-06 09:06:38,318 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-05-06 09:06:38,319 DEBUG: nvidia.available: falling back to default
2012-05-06 09:06:38,330 DEBUG: XorgDriverHandler(nvidia_173, nvidia-173, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-05-06 09:06:38,330 DEBUG: NVIDIA accelerated graphics driver not available
2012-05-06 09:06:38,332 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2012-05-06 09:06:38,336 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2012-05-06 09:06:38,336 DEBUG: nvidia.available: falling back to default
2012-05-06 09:06:38,347 DEBUG: XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-05-06 09:06:38,347 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-05-06 09:06:38,347 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2012-05-06 09:06:38,351 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2012-05-06 09:06:38,355 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2012-05-06 09:06:38,374 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2012-05-06 09:06:38,375 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2012-05-06 09:06:38,377 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2012-05-06 09:06:38,377 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2012-05-06 09:06:38,388 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2012-05-06 09:06:38,389 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-05-06 09:06:38,401 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-05-06 09:06:38,406 DEBUG: Software modem not available
2012-05-06 09:06:38,406 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-05-06 09:06:38,410 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-05-06 09:06:38,410 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-05-06 09:06:38,410 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-05-06 09:06:38,410 DEBUG: all custom handlers loaded
2012-05-06 09:06:38,410 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x159eea8> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-05-06 09:06:38,410 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x159eea8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2012-05-06 09:06:38,413 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-06 09:06:38,471 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:06:38,471 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x159eea8> about HardwareID('modalias', 'acpi:PNP0501:')
2012-05-06 09:06:38,471 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x159eea8> about HardwareID('modalias', 'acpi:PNP0000:')
2012-05-06 09:06:38,471 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x159eea8> about HardwareID('modalias', 'pci:v00001033d00000194sv00001043sd00008413bc0Csc03i30')
2012-05-06 09:06:38,473 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x159eea8> about HardwareID('modalias', 'platform:pcspkr')
2012-05-06 09:06:38,474 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2012-05-06 09:06:38,474 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:06:38,474 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2012-05-06 09:06:38,474 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:06:38,474 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x159eea8> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp01ic09isc00ip00')
2012-05-06 09:06:38,484 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x159eea8> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-05-06 09:06:38,484 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-06 09:06:38,484 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:06:38,484 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-05-06 09:06:38,484 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:06:38,484 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x159eea8> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-05-06 09:06:38,484 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x159eea8> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2012-05-06 09:06:38,485 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x159eea8> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-05-06 09:06:38,485 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x159eea8> about HardwareID('modalias', 'wmi:ABBC0F6A-8EA1-11D1-00A0-C90629100000')
2012-05-06 09:06:38,485 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x159eea8> about HardwareID('modalias', 'pci:v00001022d00009601sv00001043sd0000843Ebc06sc00i00')
2012-05-06 09:06:38,494 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x159eea8> about HardwareID('modalias', 'pci:v00001002d00004396sv00001043sd00008443bc0Csc03i20')
2012-05-06 09:06:38,708 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x159eea8> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-05-06 09:06:38,708 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x159eea8> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-05-06 09:06:38,708 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x159eea8> about HardwareID('modalias', 'acpi:PNP0100:')
2012-05-06 09:06:38,708 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x159eea8> about HardwareID('modalias', 'pci:v000010DEd00000E22sv00001462sd00002322bc03sc00i00')
2012-05-06 09:06:38,880 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb'}
2012-05-06 09:06:38,880 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:06:38,880 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nouveau'}
2012-05-06 09:06:38,880 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nouveau', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:06:38,880 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current'}
2012-05-06 09:06:38,890 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-05-06 09:06:38,972 DEBUG: KMH enabled: True
2012-05-06 09:06:38,880 DEBUG: found match in handler pool xorg:nvidia_current([NvidiaDriverCurrent, nonfree, enabled] NVIDIA accelerated graphics driver)
2012-05-06 09:06:39,061 DEBUG: nvidia.available: falling back to default
2012-05-06 09:06:39,082 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-05-06 09:06:39,165 DEBUG: KMH enabled: True
2012-05-06 09:06:39,073 DEBUG: got handler xorg:nvidia_current([NvidiaDriverCurrent, nonfree, enabled] NVIDIA accelerated graphics driver)
2012-05-06 09:06:39,247 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current', 'package': 'nvidia-current'}
2012-05-06 09:06:39,257 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-05-06 09:06:39,340 DEBUG: KMH enabled: True
2012-05-06 09:06:39,247 DEBUG: found match in handler pool xorg:nvidia_current([NvidiaDriverCurrent, nonfree, enabled] NVIDIA accelerated graphics driver)
2012-05-06 09:06:39,426 DEBUG: nvidia.available: falling back to default
2012-05-06 09:06:39,447 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-05-06 09:06:39,530 DEBUG: KMH enabled: True
2012-05-06 09:06:39,438 DEBUG: got handler xorg:nvidia_current([NvidiaDriverCurrent, nonfree, enabled] NVIDIA accelerated graphics driver)
2012-05-06 09:06:39,615 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current_updates', 'package': 'nvidia-current-updates'}
2012-05-06 09:06:39,626 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-05-06 09:06:39,626 DEBUG: nvidia_current_updates is not the alternative in use
2012-05-06 09:06:39,615 DEBUG: found match in handler pool xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2012-05-06 09:06:39,628 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-05-06 09:06:39,632 DEBUG: nvidia.available: falling back to default
2012-05-06 09:06:39,653 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-05-06 09:06:39,653 DEBUG: nvidia_current_updates is not the alternative in use
2012-05-06 09:06:39,643 DEBUG: got handler xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2012-05-06 09:06:39,653 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x159eea8> about HardwareID('modalias', 'pci:v00001002d00004390sv00001043sd00008443bc01sc06i01')
2012-05-06 09:06:39,656 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x159eea8> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-05-06 09:06:39,656 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x159eea8> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2012-05-06 09:06:39,657 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x159eea8> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001043sd00008443bc06sc01i00')
2012-05-06 09:06:39,659 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x159eea8> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2012-05-06 09:06:39,659 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x159eea8> about HardwareID('modalias', 'usb:v04D9p1203d0270dc00dsc00dp00ic03isc00ip00')
2012-05-06 09:06:39,659 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-05-06 09:06:39,659 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:06:39,660 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x159eea8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2012-05-06 09:06:39,660 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-06 09:06:39,660 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:06:39,660 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x159eea8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-05-06 09:06:39,660 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-06 09:06:39,660 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:06:39,660 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x159eea8> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2012-05-06 09:06:39,666 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-05-06 09:06:39,666 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:06:39,666 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x159eea8> about HardwareID('modalias', 'input:b0003v04D9p1203e0111-e0,1,4,k71,72,73,74,80,8C,8E,8F,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,AB,AC,AD,D9,ram4,lsfw')
2012-05-06 09:06:39,666 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-06 09:06:39,666 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:06:39,666 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-05-06 09:06:39,666 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:06:39,666 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x159eea8> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-05-06 09:06:39,666 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x159eea8> about HardwareID('modalias', 'pci:v00001002d00004383sv00001043sd0000841Bbc04sc03i00')
2012-05-06 09:06:39,669 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-05-06 09:06:39,669 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:06:39,669 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-05-06 09:06:39,669 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:06:39,669 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x159eea8> about HardwareID('modalias', 'input:b0003v04D9p1203e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2012-05-06 09:06:39,669 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-06 09:06:39,669 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:06:39,669 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-05-06 09:06:39,669 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:06:39,669 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x159eea8> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr1404:bd05/28/2010:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnM4A88TD-MEVO:rvrRevX.0x:cvnChassisManufacture:ct3:cvrChassisVersion:')
2012-05-06 09:06:39,680 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x159eea8> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2012-05-06 09:06:39,680 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'amd64_edac_mod'}
2012-05-06 09:06:39,680 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'amd64_edac_mod', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:06:39,680 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x159eea8> about HardwareID('modalias', 'acpi:PNP0400:')
2012-05-06 09:06:39,681 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x159eea8> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-05-06 09:06:39,683 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x159eea8> about HardwareID('modalias', 'input:b0003v1241p1166e0110-e0,1,2,4,k110,111,112,113,114,r0,1,8,am4,lsfw')
2012-05-06 09:06:39,683 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-06 09:06:39,683 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:06:39,683 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-05-06 09:06:39,683 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:06:39,683 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x159eea8> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-05-06 09:06:39,684 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x159eea8> about HardwareID('modalias', 'usb:v1D6Bp0003d0302dc09dsc00dp03ic09isc00ip00')
2012-05-06 09:06:39,684 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x159eea8> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-05-06 09:06:39,684 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x159eea8> about HardwareID('modalias', 'pci:v00001106d00000415sv00001043sd0000838Fbc01sc01i85')
2012-05-06 09:06:39,698 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pata_via'}
2012-05-06 09:06:39,698 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_via', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:06:39,698 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x159eea8> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2012-05-06 09:06:39,698 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'k10temp'}
2012-05-06 09:06:39,698 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k10temp', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:06:39,698 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x159eea8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-05-06 09:06:39,698 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-06 09:06:39,698 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:06:39,698 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x159eea8> about HardwareID('modalias', 'pci:v00001106d00003403sv00001043sd00008374bc0Csc00i10')
2012-05-06 09:06:39,699 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci'}
2012-05-06 09:06:39,699 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:06:39,699 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x159eea8> about HardwareID('modalias', 'acpi:PNP0800:')
2012-05-06 09:06:39,699 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x159eea8> about HardwareID('modalias', 'usb:v1241p1166d0270dc00dsc00dp00ic03isc01ip02')
2012-05-06 09:06:39,699 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-05-06 09:06:39,699 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:06:39,699 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2012-05-06 09:06:39,699 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:06:39,699 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x159eea8> about HardwareID('modalias', 'pci:v000010DEd00000BEBsv00001462sd00002322bc04sc03i00')
2012-05-06 09:06:39,702 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-05-06 09:06:39,702 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:06:39,702 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x159eea8> about HardwareID('modalias', 'acpi:PNP0200:')
2012-05-06 09:06:39,702 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x159eea8> about HardwareID('modalias', 'usb:v04D9p1203d0270dc00dsc00dp00ic03isc01ip01')
2012-05-06 09:06:39,702 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-05-06 09:06:39,702 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:06:39,702 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2012-05-06 09:06:39,702 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:06:39,702 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x159eea8> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2012-05-06 09:06:39,703 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x159eea8> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001043sd00008432bc02sc00i00')
2012-05-06 09:06:39,708 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2012-05-06 09:06:39,709 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:06:39,709 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x159eea8> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001043sd00008443bc01sc01i8a')
2012-05-06 09:06:39,711 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pata_atiixp'}
2012-05-06 09:06:39,711 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_atiixp', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:06:39,711 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x159eea8> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-05-06 09:06:39,711 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-05-06 09:06:39,712 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:06:39,712 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2012-05-06 09:06:39,712 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:06:39,712 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x159eea8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2012-05-06 09:06:39,712 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-06 09:06:39,712 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:06:39,712 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x159eea8> about HardwareID('modalias', 'pci:v00001002d00004385sv00000000sd00000000bc0Csc05i00')
2012-05-06 09:06:39,714 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4'}
2012-05-06 09:06:39,715 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:06:39,715 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco'}
2012-05-06 09:06:39,715 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:06:39,715 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x159eea8> about HardwareID('modalias', 'acpi:PNP0103:')
2012-05-06 09:06:39,715 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1909830> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-05-06 09:06:39,715 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1909830> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2012-05-06 09:06:39,715 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1909830> about HardwareID('modalias', 'acpi:PNP0501:')
2012-05-06 09:06:39,715 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1909830> about HardwareID('modalias', 'acpi:PNP0000:')
2012-05-06 09:06:39,715 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1909830> about HardwareID('modalias', 'pci:v00001033d00000194sv00001043sd00008413bc0Csc03i30')
2012-05-06 09:06:39,715 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1909830> about HardwareID('modalias', 'platform:pcspkr')
2012-05-06 09:06:39,715 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1909830> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp01ic09isc00ip00')
2012-05-06 09:06:39,715 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1909830> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-05-06 09:06:39,715 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1909830> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-05-06 09:06:39,715 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1909830> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2012-05-06 09:06:39,715 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1909830> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-05-06 09:06:39,715 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1909830> about HardwareID('modalias', 'wmi:ABBC0F6A-8EA1-11D1-00A0-C90629100000')
2012-05-06 09:06:39,715 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1909830> about HardwareID('modalias', 'pci:v00001022d00009601sv00001043sd0000843Ebc06sc00i00')
2012-05-06 09:06:39,715 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1909830> about HardwareID('modalias', 'pci:v00001002d00004396sv00001043sd00008443bc0Csc03i20')
2012-05-06 09:06:39,715 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1909830> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-05-06 09:06:39,715 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1909830> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-05-06 09:06:39,715 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1909830> about HardwareID('modalias', 'acpi:PNP0100:')
2012-05-06 09:06:39,715 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1909830> about HardwareID('modalias', 'pci:v000010DEd00000E22sv00001462sd00002322bc03sc00i00')
2012-05-06 09:06:39,716 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1909830> about HardwareID('modalias', 'pci:v00001002d00004390sv00001043sd00008443bc01sc06i01')
2012-05-06 09:06:39,716 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1909830> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-05-06 09:06:39,716 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1909830> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2012-05-06 09:06:39,716 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1909830> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001043sd00008443bc06sc01i00')
2012-05-06 09:06:39,716 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1909830> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2012-05-06 09:06:39,716 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1909830> about HardwareID('modalias', 'usb:v04D9p1203d0270dc00dsc00dp00ic03isc00ip00')
2012-05-06 09:06:39,716 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1909830> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2012-05-06 09:06:39,716 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1909830> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-05-06 09:06:39,716 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1909830> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2012-05-06 09:06:39,716 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1909830> about HardwareID('modalias', 'input:b0003v04D9p1203e0111-e0,1,4,k71,72,73,74,80,8C,8E,8F,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,AB,AC,AD,D9,ram4,lsfw')
2012-05-06 09:06:39,716 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1909830> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-05-06 09:06:39,716 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1909830> about HardwareID('modalias', 'pci:v00001002d00004383sv00001043sd0000841Bbc04sc03i00')
2012-05-06 09:06:39,716 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1909830> about HardwareID('modalias', 'input:b0003v04D9p1203e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2012-05-06 09:06:39,716 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1909830> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr1404:bd05/28/2010:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnM4A88TD-MEVO:rvrRevX.0x:cvnChassisManufacture:ct3:cvrChassisVersion:')
2012-05-06 09:06:39,716 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1909830> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2012-05-06 09:06:39,716 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1909830> about HardwareID('modalias', 'acpi:PNP0400:')
2012-05-06 09:06:39,716 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1909830> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-05-06 09:06:39,716 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1909830> about HardwareID('modalias', 'input:b0003v1241p1166e0110-e0,1,2,4,k110,111,112,113,114,r0,1,8,am4,lsfw')
2012-05-06 09:06:39,716 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1909830> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-05-06 09:06:39,716 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1909830> about HardwareID('modalias', 'usb:v1D6Bp0003d0302dc09dsc00dp03ic09isc00ip00')
2012-05-06 09:06:39,716 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1909830> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-05-06 09:06:39,716 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1909830> about HardwareID('modalias', 'pci:v00001106d00000415sv00001043sd0000838Fbc01sc01i85')
2012-05-06 09:06:39,717 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1909830> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2012-05-06 09:06:39,717 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1909830> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-05-06 09:06:39,717 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1909830> about HardwareID('modalias', 'pci:v00001106d00003403sv00001043sd00008374bc0Csc00i10')
2012-05-06 09:06:39,717 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1909830> about HardwareID('modalias', 'acpi:PNP0800:')
2012-05-06 09:06:39,717 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1909830> about HardwareID('modalias', 'usb:v1241p1166d0270dc00dsc00dp00ic03isc01ip02')
2012-05-06 09:06:39,717 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1909830> about HardwareID('modalias', 'pci:v000010DEd00000BEBsv00001462sd00002322bc04sc03i00')
2012-05-06 09:06:39,717 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1909830> about HardwareID('modalias', 'acpi:PNP0200:')
2012-05-06 09:06:39,717 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1909830> about HardwareID('modalias', 'usb:v04D9p1203d0270dc00dsc00dp00ic03isc01ip01')
2012-05-06 09:06:39,717 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1909830> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2012-05-06 09:06:39,717 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1909830> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001043sd00008432bc02sc00i00')
2012-05-06 09:06:39,717 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1909830> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001043sd00008443bc01sc01i8a')
2012-05-06 09:06:39,717 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1909830> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-05-06 09:06:39,717 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1909830> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2012-05-06 09:06:39,717 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1909830> about HardwareID('modalias', 'pci:v00001002d00004385sv00000000sd00000000bc0Csc05i00')
2012-05-06 09:06:39,717 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1909830> about HardwareID('modalias', 'acpi:PNP0103:')
2012-05-06 09:06:39,727 DEBUG: Shutting down
2012-05-06 09:10:14,360 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ccaea8>
2012-05-06 09:10:17,145 DEBUG: reading modalias file /lib/modules/3.2.0-24-generic/modules.alias
2012-05-06 09:10:17,236 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-05-06 09:10:17,245 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-05-06 09:10:17,319 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-05-06 09:10:17,374 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-05-06 09:10:17,374 DEBUG: Firmware for DVB cards not available
2012-05-06 09:10:17,374 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-05-06 09:10:17,377 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-05-06 09:10:17,389 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-05-06 09:10:17,390 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-05-06 09:10:17,390 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-05-06 09:10:17,422 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-05-06 09:10:17,425 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2012-05-06 09:10:17,425 DEBUG: fglrx.available: falling back to default
2012-05-06 09:10:17,578 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2012-05-06 09:10:17,581 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-05-06 09:10:17,584 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-05-06 09:10:17,584 DEBUG: fglrx.available: falling back to default
2012-05-06 09:10:17,606 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-05-06 09:10:17,606 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-05-06 09:10:17,621 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-05-06 09:10:17,624 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-05-06 09:10:17,625 DEBUG: nvidia.available: falling back to default
2012-05-06 09:10:17,636 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-05-06 09:10:17,636 DEBUG: NVIDIA accelerated graphics driver not available
2012-05-06 09:10:17,642 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-05-06 09:10:17,642 DEBUG: nvidia.available: falling back to default
2012-05-06 09:10:17,664 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-05-06 09:10:17,666 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-05-06 09:10:17,670 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2012-05-06 09:10:17,670 DEBUG: nvidia.available: falling back to default
2012-05-06 09:10:17,692 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-05-06 09:10:17,694 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-05-06 09:10:17,697 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2012-05-06 09:10:17,698 DEBUG: nvidia.available: falling back to default
2012-05-06 09:10:17,709 DEBUG: XorgDriverHandler(nvidia_173_updates, nvidia-173-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-05-06 09:10:17,709 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-05-06 09:10:17,711 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-05-06 09:10:17,715 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-05-06 09:10:17,715 DEBUG: nvidia.available: falling back to default
2012-05-06 09:10:17,726 DEBUG: XorgDriverHandler(nvidia_173, nvidia-173, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-05-06 09:10:17,726 DEBUG: NVIDIA accelerated graphics driver not available
2012-05-06 09:10:17,729 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2012-05-06 09:10:17,732 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2012-05-06 09:10:17,732 DEBUG: nvidia.available: falling back to default
2012-05-06 09:10:17,743 DEBUG: XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-05-06 09:10:17,743 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-05-06 09:10:17,743 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2012-05-06 09:10:17,747 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2012-05-06 09:10:17,751 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2012-05-06 09:10:17,770 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2012-05-06 09:10:17,770 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2012-05-06 09:10:17,772 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2012-05-06 09:10:17,773 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2012-05-06 09:10:17,784 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2012-05-06 09:10:17,784 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-05-06 09:10:17,796 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-05-06 09:10:17,813 DEBUG: Software modem not available
2012-05-06 09:10:17,813 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-05-06 09:10:17,816 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-05-06 09:10:17,817 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-05-06 09:10:17,817 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-05-06 09:10:17,817 DEBUG: all custom handlers loaded
2012-05-06 09:10:17,817 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ccaea8> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-05-06 09:10:17,817 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ccaea8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2012-05-06 09:10:17,820 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-06 09:10:17,899 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:10:17,899 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ccaea8> about HardwareID('modalias', 'acpi:PNP0501:')
2012-05-06 09:10:17,899 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ccaea8> about HardwareID('modalias', 'acpi:PNP0000:')
2012-05-06 09:10:17,899 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ccaea8> about HardwareID('modalias', 'pci:v00001033d00000194sv00001043sd00008413bc0Csc03i30')
2012-05-06 09:10:17,902 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ccaea8> about HardwareID('modalias', 'platform:pcspkr')
2012-05-06 09:10:17,902 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2012-05-06 09:10:17,902 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:10:17,902 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2012-05-06 09:10:17,902 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:10:17,902 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ccaea8> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp01ic09isc00ip00')
2012-05-06 09:10:17,912 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ccaea8> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-05-06 09:10:17,912 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-06 09:10:17,912 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:10:17,912 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-05-06 09:10:17,912 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:10:17,913 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ccaea8> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-05-06 09:10:17,913 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ccaea8> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2012-05-06 09:10:17,913 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ccaea8> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-05-06 09:10:17,913 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ccaea8> about HardwareID('modalias', 'wmi:ABBC0F6A-8EA1-11D1-00A0-C90629100000')
2012-05-06 09:10:17,913 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ccaea8> about HardwareID('modalias', 'pci:v00001022d00009601sv00001043sd0000843Ebc06sc00i00')
2012-05-06 09:10:17,922 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ccaea8> about HardwareID('modalias', 'pci:v00001002d00004396sv00001043sd00008443bc0Csc03i20')
2012-05-06 09:10:18,134 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ccaea8> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-05-06 09:10:18,134 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ccaea8> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-05-06 09:10:18,134 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ccaea8> about HardwareID('modalias', 'acpi:PNP0100:')
2012-05-06 09:10:18,135 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ccaea8> about HardwareID('modalias', 'pci:v000010DEd00000E22sv00001462sd00002322bc03sc00i00')
2012-05-06 09:10:18,305 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb'}
2012-05-06 09:10:18,305 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:10:18,305 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nouveau'}
2012-05-06 09:10:18,305 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nouveau', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:10:18,305 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current'}
2012-05-06 09:10:18,370 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-05-06 09:10:18,489 DEBUG: KMH enabled: True
2012-05-06 09:10:18,305 DEBUG: found match in handler pool xorg:nvidia_current([NvidiaDriverCurrent, nonfree, enabled] NVIDIA accelerated graphics driver)
2012-05-06 09:10:18,576 DEBUG: nvidia.available: falling back to default
2012-05-06 09:10:18,596 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-05-06 09:10:18,680 DEBUG: KMH enabled: True
2012-05-06 09:10:18,587 DEBUG: got handler xorg:nvidia_current([NvidiaDriverCurrent, nonfree, enabled] NVIDIA accelerated graphics driver)
2012-05-06 09:10:18,764 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current', 'package': 'nvidia-current'}
2012-05-06 09:10:18,774 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-05-06 09:10:18,857 DEBUG: KMH enabled: True
2012-05-06 09:10:18,765 DEBUG: found match in handler pool xorg:nvidia_current([NvidiaDriverCurrent, nonfree, enabled] NVIDIA accelerated graphics driver)
2012-05-06 09:10:18,947 DEBUG: nvidia.available: falling back to default
2012-05-06 09:10:18,967 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-05-06 09:10:19,049 DEBUG: KMH enabled: True
2012-05-06 09:10:18,958 DEBUG: got handler xorg:nvidia_current([NvidiaDriverCurrent, nonfree, enabled] NVIDIA accelerated graphics driver)
2012-05-06 09:10:19,131 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current_updates', 'package': 'nvidia-current-updates'}
2012-05-06 09:10:19,141 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-05-06 09:10:19,141 DEBUG: nvidia_current_updates is not the alternative in use
2012-05-06 09:10:19,132 DEBUG: found match in handler pool xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2012-05-06 09:10:19,144 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-05-06 09:10:19,147 DEBUG: nvidia.available: falling back to default
2012-05-06 09:10:19,168 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-05-06 09:10:19,168 DEBUG: nvidia_current_updates is not the alternative in use
2012-05-06 09:10:19,159 DEBUG: got handler xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2012-05-06 09:10:19,168 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ccaea8> about HardwareID('modalias', 'pci:v00001002d00004390sv00001043sd00008443bc01sc06i01')
2012-05-06 09:10:19,171 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ccaea8> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-05-06 09:10:19,171 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ccaea8> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2012-05-06 09:10:19,171 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ccaea8> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001043sd00008443bc06sc01i00')
2012-05-06 09:10:19,174 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ccaea8> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2012-05-06 09:10:19,174 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ccaea8> about HardwareID('modalias', 'usb:v04D9p1203d0270dc00dsc00dp00ic03isc00ip00')
2012-05-06 09:10:19,174 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-05-06 09:10:19,174 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:10:19,174 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ccaea8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2012-05-06 09:10:19,174 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-06 09:10:19,175 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:10:19,175 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ccaea8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-05-06 09:10:19,175 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-06 09:10:19,175 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:10:19,175 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ccaea8> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2012-05-06 09:10:19,180 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-05-06 09:10:19,181 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:10:19,181 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ccaea8> about HardwareID('modalias', 'input:b0003v04D9p1203e0111-e0,1,4,k71,72,73,74,80,8C,8E,8F,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,AB,AC,AD,D9,ram4,lsfw')
2012-05-06 09:10:19,181 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-06 09:10:19,181 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:10:19,181 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-05-06 09:10:19,181 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:10:19,181 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ccaea8> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-05-06 09:10:19,181 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ccaea8> about HardwareID('modalias', 'pci:v00001002d00004383sv00001043sd0000841Bbc04sc03i00')
2012-05-06 09:10:19,183 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-05-06 09:10:19,184 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:10:19,184 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-05-06 09:10:19,184 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:10:19,184 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ccaea8> about HardwareID('modalias', 'input:b0003v04D9p1203e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2012-05-06 09:10:19,184 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-06 09:10:19,184 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:10:19,184 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-05-06 09:10:19,184 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:10:19,184 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ccaea8> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr1404:bd05/28/2010:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnM4A88TD-MEVO:rvrRevX.0x:cvnChassisManufacture:ct3:cvrChassisVersion:')
2012-05-06 09:10:19,195 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ccaea8> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2012-05-06 09:10:19,195 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'amd64_edac_mod'}
2012-05-06 09:10:19,195 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'amd64_edac_mod', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:10:19,195 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ccaea8> about HardwareID('modalias', 'acpi:PNP0400:')
2012-05-06 09:10:19,195 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ccaea8> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-05-06 09:10:19,198 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ccaea8> about HardwareID('modalias', 'input:b0003v1241p1166e0110-e0,1,2,4,k110,111,112,113,114,r0,1,8,am4,lsfw')
2012-05-06 09:10:19,198 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-06 09:10:19,198 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:10:19,198 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-05-06 09:10:19,198 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:10:19,198 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ccaea8> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-05-06 09:10:19,198 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ccaea8> about HardwareID('modalias', 'usb:v1D6Bp0003d0302dc09dsc00dp03ic09isc00ip00')
2012-05-06 09:10:19,198 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ccaea8> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-05-06 09:10:19,199 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ccaea8> about HardwareID('modalias', 'pci:v00001106d00000415sv00001043sd0000838Fbc01sc01i85')
2012-05-06 09:10:19,212 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pata_via'}
2012-05-06 09:10:19,212 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_via', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:10:19,212 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ccaea8> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2012-05-06 09:10:19,213 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'k10temp'}
2012-05-06 09:10:19,213 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k10temp', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:10:19,213 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ccaea8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-05-06 09:10:19,213 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-06 09:10:19,213 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:10:19,213 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ccaea8> about HardwareID('modalias', 'pci:v00001106d00003403sv00001043sd00008374bc0Csc00i10')
2012-05-06 09:10:19,213 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci'}
2012-05-06 09:10:19,213 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:10:19,213 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ccaea8> about HardwareID('modalias', 'acpi:PNP0800:')
2012-05-06 09:10:19,213 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ccaea8> about HardwareID('modalias', 'usb:v1241p1166d0270dc00dsc00dp00ic03isc01ip02')
2012-05-06 09:10:19,214 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-05-06 09:10:19,214 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:10:19,214 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2012-05-06 09:10:19,214 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:10:19,214 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ccaea8> about HardwareID('modalias', 'pci:v000010DEd00000BEBsv00001462sd00002322bc04sc03i00')
2012-05-06 09:10:19,216 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-05-06 09:10:19,216 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:10:19,216 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ccaea8> about HardwareID('modalias', 'acpi:PNP0200:')
2012-05-06 09:10:19,216 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ccaea8> about HardwareID('modalias', 'usb:v04D9p1203d0270dc00dsc00dp00ic03isc01ip01')
2012-05-06 09:10:19,217 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-05-06 09:10:19,217 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:10:19,217 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2012-05-06 09:10:19,217 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:10:19,217 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ccaea8> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2012-05-06 09:10:19,217 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ccaea8> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001043sd00008432bc02sc00i00')
2012-05-06 09:10:19,223 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2012-05-06 09:10:19,223 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:10:19,223 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ccaea8> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001043sd00008443bc01sc01i8a')
2012-05-06 09:10:19,225 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pata_atiixp'}
2012-05-06 09:10:19,226 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_atiixp', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:10:19,226 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ccaea8> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-05-06 09:10:19,226 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-05-06 09:10:19,226 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:10:19,226 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2012-05-06 09:10:19,226 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:10:19,226 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ccaea8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2012-05-06 09:10:19,226 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-06 09:10:19,226 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:10:19,226 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ccaea8> about HardwareID('modalias', 'pci:v00001002d00004385sv00000000sd00000000bc0Csc05i00')
2012-05-06 09:10:19,229 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4'}
2012-05-06 09:10:19,229 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:10:19,229 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco'}
2012-05-06 09:10:19,229 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco', 'jockey_handler': 'KernelModuleHandler'}
2012-05-06 09:10:19,229 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ccaea8> about HardwareID('modalias', 'acpi:PNP0103:')
2012-05-06 09:10:19,229 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2035830> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-05-06 09:10:19,229 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2035830> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2012-05-06 09:10:19,229 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2035830> about HardwareID('modalias', 'acpi:PNP0501:')
2012-05-06 09:10:19,229 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2035830> about HardwareID('modalias', 'acpi:PNP0000:')
2012-05-06 09:10:19,229 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2035830> about HardwareID('modalias', 'pci:v00001033d00000194sv00001043sd00008413bc0Csc03i30')
2012-05-06 09:10:19,229 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2035830> about HardwareID('modalias', 'platform:pcspkr')
2012-05-06 09:10:19,229 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2035830> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp01ic09isc00ip00')
2012-05-06 09:10:19,229 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2035830> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-05-06 09:10:19,229 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2035830> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-05-06 09:10:19,229 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2035830> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2012-05-06 09:10:19,229 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2035830> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-05-06 09:10:19,229 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2035830> about HardwareID('modalias', 'wmi:ABBC0F6A-8EA1-11D1-00A0-C90629100000')
2012-05-06 09:10:19,230 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2035830> about HardwareID('modalias', 'pci:v00001022d00009601sv00001043sd0000843Ebc06sc00i00')
2012-05-06 09:10:19,230 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2035830> about HardwareID('modalias', 'pci:v00001002d00004396sv00001043sd00008443bc0Csc03i20')
2012-05-06 09:10:19,230 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2035830> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-05-06 09:10:19,230 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2035830> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-05-06 09:10:19,230 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2035830> about HardwareID('modalias', 'acpi:PNP0100:')
2012-05-06 09:10:19,230 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2035830> about HardwareID('modalias', 'pci:v000010DEd00000E22sv00001462sd00002322bc03sc00i00')
2012-05-06 09:10:19,230 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2035830> about HardwareID('modalias', 'pci:v00001002d00004390sv00001043sd00008443bc01sc06i01')
2012-05-06 09:10:19,230 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2035830> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-05-06 09:10:19,230 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2035830> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2012-05-06 09:10:19,230 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2035830> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001043sd00008443bc06sc01i00')
2012-05-06 09:10:19,230 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2035830> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2012-05-06 09:10:19,230 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2035830> about HardwareID('modalias', 'usb:v04D9p1203d0270dc00dsc00dp00ic03isc00ip00')
2012-05-06 09:10:19,230 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2035830> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2012-05-06 09:10:19,230 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2035830> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-05-06 09:10:19,230 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2035830> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2012-05-06 09:10:19,230 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2035830> about HardwareID('modalias', 'input:b0003v04D9p1203e0111-e0,1,4,k71,72,73,74,80,8C,8E,8F,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,AB,AC,AD,D9,ram4,lsfw')
2012-05-06 09:10:19,230 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2035830> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-05-06 09:10:19,230 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2035830> about HardwareID('modalias', 'pci:v00001002d00004383sv00001043sd0000841Bbc04sc03i00')
2012-05-06 09:10:19,230 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2035830> about HardwareID('modalias', 'input:b0003v04D9p1203e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2012-05-06 09:10:19,230 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2035830> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr1404:bd05/28/2010:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnM4A88TD-MEVO:rvrRevX.0x:cvnChassisManufacture:ct3:cvrChassisVersion:')
2012-05-06 09:10:19,230 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2035830> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2012-05-06 09:10:19,230 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2035830> about HardwareID('modalias', 'acpi:PNP0400:')
2012-05-06 09:10:19,231 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2035830> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-05-06 09:10:19,231 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2035830> about HardwareID('modalias', 'input:b0003v1241p1166e0110-e0,1,2,4,k110,111,112,113,114,r0,1,8,am4,lsfw')
2012-05-06 09:10:19,231 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2035830> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-05-06 09:10:19,231 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2035830> about HardwareID('modalias', 'usb:v1D6Bp0003d0302dc09dsc00dp03ic09isc00ip00')
2012-05-06 09:10:19,231 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2035830> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-05-06 09:10:19,231 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2035830> about HardwareID('modalias', 'pci:v00001106d00000415sv00001043sd0000838Fbc01sc01i85')
2012-05-06 09:10:19,231 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2035830> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2012-05-06 09:10:19,231 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2035830> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-05-06 09:10:19,231 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2035830> about HardwareID('modalias', 'pci:v00001106d00003403sv00001043sd00008374bc0Csc00i10')
2012-05-06 09:10:19,231 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2035830> about HardwareID('modalias', 'acpi:PNP0800:')
2012-05-06 09:10:19,231 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2035830> about HardwareID('modalias', 'usb:v1241p1166d0270dc00dsc00dp00ic03isc01ip02')
2012-05-06 09:10:19,231 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2035830> about HardwareID('modalias', 'pci:v000010DEd00000BEBsv00001462sd00002322bc04sc03i00')
2012-05-06 09:10:19,231 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2035830> about HardwareID('modalias', 'acpi:PNP0200:')
2012-05-06 09:10:19,231 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2035830> about HardwareID('modalias', 'usb:v04D9p1203d0270dc00dsc00dp00ic03isc01ip01')
2012-05-06 09:10:19,231 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2035830> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2012-05-06 09:10:19,231 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2035830> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001043sd00008432bc02sc00i00')
2012-05-06 09:10:19,231 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2035830> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001043sd00008443bc01sc01i8a')
2012-05-06 09:10:19,231 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2035830> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-05-06 09:10:19,231 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2035830> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2012-05-06 09:10:19,231 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2035830> about HardwareID('modalias', 'pci:v00001002d00004385sv00000000sd00000000bc0Csc05i00')
2012-05-06 09:10:19,231 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2035830> about HardwareID('modalias', 'acpi:PNP0103:')
2012-05-06 09:10:19,294 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-05-06 09:10:19,376 DEBUG: KMH enabled: True
2012-05-06 09:10:20,781 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-05-06 09:10:20,781 DEBUG: nvidia_current_updates is not the alternative in use
2012-05-06 09:10:21,922 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-05-06 09:10:22,007 DEBUG: KMH enabled: True
2012-05-06 09:10:22,207 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-05-06 09:10:22,291 DEBUG: KMH enabled: True
2012-05-06 09:10:23,697 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-05-06 09:10:23,697 DEBUG: nvidia_current_updates is not the alternative in use
2012-05-06 09:10:24,841 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-05-06 09:10:24,842 DEBUG: nvidia_current_updates is not the alternative in use
2012-05-06 09:10:31,114 DEBUG: Installing package: nvidia-current-updates
2012-05-06 09:10:31,903 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 0.000029
2012-05-06 09:10:31,903 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 0.000029
2012-05-06 09:10:31,924 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 0.000029
2012-05-06 09:10:31,943 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 0.000029
2012-05-06 09:10:31,973 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 0.001922
2012-05-06 09:10:32,474 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 0.781648
2012-05-06 09:10:32,975 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 1.680028
2012-05-06 09:10:33,475 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 2.626837
2012-05-06 09:10:33,976 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 3.590598
2012-05-06 09:10:34,477 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 4.554358
2012-05-06 09:10:34,979 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 5.513276
2012-05-06 09:10:35,480 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 6.343853
2012-05-06 09:10:35,981 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 7.317300
2012-05-06 09:10:36,482 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 8.278639
2012-05-06 09:10:36,983 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 9.235135
2012-05-06 09:10:37,484 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 10.206160
2012-05-06 09:10:37,985 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 11.152970
2012-05-06 09:10:38,487 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 12.104622
2012-05-06 09:10:38,988 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 13.063540
2012-05-06 09:10:39,489 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 13.986135
2012-05-06 09:10:39,990 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 14.639942
2012-05-06 09:10:40,491 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 15.158145
2012-05-06 09:10:40,992 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 15.700563
2012-05-06 09:10:41,493 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 16.005673
2012-05-06 09:10:41,994 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 16.538405
2012-05-06 09:10:42,496 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 17.310866
2012-05-06 09:10:42,997 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 17.705572
2012-05-06 09:10:43,498 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 18.570051
2012-05-06 09:10:43,999 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 19.439372
2012-05-06 09:10:44,500 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 20.393447
2012-05-06 09:10:45,002 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 21.173173
2012-05-06 09:10:45,503 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 21.940791
2012-05-06 09:10:46,004 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 22.645450
2012-05-06 09:10:46,505 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 23.614053
2012-05-06 09:10:47,007 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 24.592343
2012-05-06 09:10:47,508 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 25.558525
2012-05-06 09:10:48,009 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 26.531971
2012-05-06 09:10:48,510 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 27.502996
2012-05-06 09:10:49,011 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 28.464335
2012-05-06 09:10:49,513 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 29.440203
2012-05-06 09:10:50,014 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 30.413650
2012-05-06 09:10:50,516 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 31.396782
2012-05-06 09:10:51,017 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 32.377493
2012-05-06 09:10:51,518 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 33.353361
2012-05-06 09:10:52,019 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 34.285642
2012-05-06 09:10:52,521 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 35.266353
2012-05-06 09:10:53,022 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 36.237378
2012-05-06 09:10:53,523 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 37.210825
2012-05-06 09:10:54,024 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 38.179428
2012-05-06 09:10:54,525 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 39.164982
2012-05-06 09:10:55,026 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 40.150536
2012-05-06 09:10:55,527 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 41.119140
2012-05-06 09:10:56,028 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 42.095008
2012-05-06 09:10:56,529 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 43.058768
2012-05-06 09:10:57,030 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 44.034636
2012-05-06 09:10:57,532 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 45.012926
2012-05-06 09:10:58,033 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 45.986372
2012-05-06 09:10:58,533 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 46.954976
2012-05-06 09:10:59,034 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 47.928422
2012-05-06 09:10:59,535 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 48.904290
2012-05-06 09:11:00,036 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 49.870472
2012-05-06 09:11:00,537 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 50.843918
2012-05-06 09:11:01,038 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 51.814943
2012-05-06 09:11:01,539 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 52.778704
2012-05-06 09:11:02,040 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 53.740043
2012-05-06 09:11:02,541 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 54.713489
2012-05-06 09:11:03,043 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 55.703886
2012-05-06 09:11:03,544 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 56.670068
2012-05-06 09:11:04,045 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 57.648358
2012-05-06 09:11:04,546 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 58.624226
2012-05-06 09:11:05,048 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 59.595251
2012-05-06 09:11:05,549 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 60.561433
2012-05-06 09:11:06,050 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 61.554251
2012-05-06 09:11:06,551 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 62.520433
2012-05-06 09:11:07,052 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 63.496301
2012-05-06 09:11:07,553 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 64.469748
2012-05-06 09:11:08,054 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 65.435930
2012-05-06 09:11:08,555 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 66.404533
2012-05-06 09:11:09,056 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 67.380401
2012-05-06 09:11:09,557 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 68.356269
2012-05-06 09:11:10,059 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 69.324873
2012-05-06 09:11:10,559 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 70.291055
2012-05-06 09:11:11,061 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 71.264501
2012-05-06 09:11:11,562 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 72.223419
2012-05-06 09:11:12,063 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 73.187179
2012-05-06 09:11:12,564 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 74.167890
2012-05-06 09:11:13,065 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 75.112279
2012-05-06 09:11:13,567 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 76.083304
2012-05-06 09:11:14,068 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 77.049485
2012-05-06 09:11:14,569 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 78.010824
2012-05-06 09:11:15,070 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 78.974585
2012-05-06 09:11:15,571 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 79.952874
2012-05-06 09:11:16,072 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 80.911792
2012-05-06 09:11:16,573 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 81.848916
2012-05-06 09:11:17,074 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 82.798147
2012-05-06 09:11:17,575 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 83.766751
2012-05-06 09:11:18,077 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 84.742619
2012-05-06 09:11:18,578 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 85.699115
2012-05-06 09:11:19,079 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 86.658032
2012-05-06 09:11:19,580 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 87.631478
2012-05-06 09:11:20,082 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 88.590396
2012-05-06 09:11:20,583 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 89.561421
2012-05-06 09:11:21,084 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 90.517917
2012-05-06 09:11:21,585 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 91.486520
2012-05-06 09:11:22,086 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 92.443016
2012-05-06 09:11:22,588 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 93.423727
2012-05-06 09:11:23,089 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 94.385066
2012-05-06 09:11:23,590 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 95.358513
2012-05-06 09:11:24,091 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 96.334381
2012-05-06 09:11:24,592 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 97.312670
2012-05-06 09:11:25,093 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 98.276431
2012-05-06 09:11:25,182 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 98.435512
2012-05-06 09:11:25,183 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 98.440355
2012-05-06 09:11:25,684 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 99.416223
2012-05-06 09:11:25,982 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 100.000000
2012-05-06 09:11:26,997 DEBUG: install progress dpkg-exec 0.000000
2012-05-06 09:11:29,697 DEBUG: install progress libqt4-svg 0.884956
2012-05-06 09:11:30,116 DEBUG: install progress libqt4-svg 1.769910
2012-05-06 09:11:33,628 DEBUG: install progress libqtgui4 2.654870
2012-05-06 09:11:34,482 DEBUG: install progress libqtgui4 3.539820
2012-05-06 09:11:35,943 DEBUG: install progress libqt4-declarative 4.424780
2012-05-06 09:11:36,386 DEBUG: install progress libqt4-declarative 5.309730
2012-05-06 09:11:37,734 DEBUG: install progress libqt4-network 6.194690
2012-05-06 09:11:38,145 DEBUG: install progress libqt4-network 7.079650
2012-05-06 09:11:38,484 DEBUG: install progress dpkg-exec 7.079650
2012-05-06 09:11:38,540 DEBUG: install progress libqt4-network 7.079650
2012-05-06 09:11:39,028 DEBUG: install progress libc-bin 7.079650
2012-05-06 09:11:39,923 DEBUG: install progress dpkg-exec 7.079650
2012-05-06 09:11:41,420 DEBUG: install progress libqt4-sql 7.964600
2012-05-06 09:11:41,745 DEBUG: install progress libqt4-sql 8.849560
2012-05-06 09:11:42,002 DEBUG: install progress dpkg-exec 8.849560
2012-05-06 09:11:42,049 DEBUG: install progress libqt4-sql 8.849560
2012-05-06 09:11:42,538 DEBUG: install progress libc-bin 8.849560
2012-05-06 09:11:42,840 DEBUG: install progress dpkg-exec 8.849560
2012-05-06 09:11:44,339 DEBUG: install progress libqt4-xmlpatterns 9.734510
2012-05-06 09:11:44,793 DEBUG: install progress libqt4-xmlpatterns 10.619500
2012-05-06 09:11:45,062 DEBUG: install progress dpkg-exec 10.619500
2012-05-06 09:11:45,164 DEBUG: (Reading database ... 222545 files and directories currently installed.)
Preparing to replace libqt4-svg 4:4.8.1-0ubuntu4 (using .../libqt4-svg_4%3a4.8.1-0ubuntu4.1_amd64.deb) ...
De-configuring libqt4-svg:i386 ...
Unpacking replacement libqt4-svg ...
Preparing to replace libqt4-svg:i386 4:4.8.1-0ubuntu4 (using .../libqt4-svg_4%3a4.8.1-0ubuntu4.1_i386.deb) ...
Unpacking replacement libqt4-svg:i386 ...
Preparing to replace libqtgui4:i386 4:4.8.1-0ubuntu4 (using .../libqtgui4_4%3a4.8.1-0ubuntu4.1_i386.deb) ...
De-configuring libqtgui4 ...
Unpacking replacement libqtgui4:i386 ...
Preparing to replace libqtgui4 4:4.8.1-0ubuntu4 (using .../libqtgui4_4%3a4.8.1-0ubuntu4.1_amd64.deb) ...
Unpacking replacement libqtgui4 ...
Preparing to replace libqt4-declarative:i386 4:4.8.1-0ubuntu4 (using .../libqt4-declarative_4%3a4.8.1-0ubuntu4.1_i386.deb) ...
De-configuring libqt4-declarative ...
Unpacking replacement libqt4-declarative:i386 ...
Preparing to replace libqt4-declarative 4:4.8.1-0ubuntu4 (using .../libqt4-declarative_4%3a4.8.1-0ubuntu4.1_amd64.deb) ...
Unpacking replacement libqt4-declarative ...
Preparing to replace libqt4-network:i386 4:4.8.1-0ubuntu4 (using .../libqt4-network_4%3a4.8.1-0ubuntu4.1_i386.deb) ...
De-configuring libqt4-network ...
Unpacking replacement libqt4-network:i386 ...
Preparing to replace libqt4-network 4:4.8.1-0ubuntu4 (using .../libqt4-network_4%3a4.8.1-0ubuntu4.1_amd64.deb) ...
Unpacking replacement libqt4-network ...
Setting up libqt4-network (4:4.8.1-0ubuntu4.1) ...
Setting up libqt4-network:i386 (4:4.8.1-0ubuntu4.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 222545 files and directories currently installed.)
Preparing to replace libqt4-sql:i386 4:4.8.1-0ubuntu4 (using .../libqt4-sql_4%3a4.8.1-0ubuntu4.1_i386.deb) ...
De-configuring libqt4-sql ...
Unpacking replacement libqt4-sql:i386 ...
Preparing to replace libqt4-sql 4:4.8.1-0ubuntu4 (using .../libqt4-sql_4%3a4.8.1-0ubuntu4.1_amd64.deb) ...
Unpacking replacement libqt4-sql ...
Setting up libqt4-sql (4:4.8.1-0ubuntu4.1) ...
Setting up libqt4-sql:i386 (4:4.8.1-0ubuntu4.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 222545 files and directories currently installed.)
Preparing to replace libqt4-xmlpatterns:i386 4:4.8.1-0ubuntu4 (using .../libqt4-xmlpatterns_4%3a4.8.1-0ubuntu4.1_i386.deb) ...
De-configuring libqt4-xmlpatterns ...
Unpacking replacement libqt4-xmlpatterns:i386 ...
Preparing to replace libqt4-xmlpatterns 4:4.8.1-0ubuntu4 (using .../libqt4-xmlpatterns_4%3a4.8.1-0ubuntu4.1_amd64.deb) ...
Unpacking replacement libqt4-xmlpatterns ...
dpkg: error: dpkg status database is locked by another process
Error in function: 
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (2)

2012-05-06 09:11:45,164 ERROR: Package failed to install:
(Reading database ... 222545 files and directories currently installed.)
Preparing to replace libqt4-svg 4:4.8.1-0ubuntu4 (using .../libqt4-svg_4%3a4.8.1-0ubuntu4.1_amd64.deb) ...
De-configuring libqt4-svg:i386 ...
Unpacking replacement libqt4-svg ...
Preparing to replace libqt4-svg:i386 4:4.8.1-0ubuntu4 (using .../libqt4-svg_4%3a4.8.1-0ubuntu4.1_i386.deb) ...
Unpacking replacement libqt4-svg:i386 ...
Preparing to replace libqtgui4:i386 4:4.8.1-0ubuntu4 (using .../libqtgui4_4%3a4.8.1-0ubuntu4.1_i386.deb) ...
De-configuring libqtgui4 ...
Unpacking replacement libqtgui4:i386 ...
Preparing to replace libqtgui4 4:4.8.1-0ubuntu4 (using .../libqtgui4_4%3a4.8.1-0ubuntu4.1_amd64.deb) ...
Unpacking replacement libqtgui4 ...
Preparing to replace libqt4-declarative:i386 4:4.8.1-0ubuntu4 (using .../libqt4-declarative_4%3a4.8.1-0ubuntu4.1_i386.deb) ...
De-configuring libqt4-declarative ...
Unpacking replacement libqt4-declarative:i386 ...
Preparing to replace libqt4-declarative 4:4.8.1-0ubuntu4 (using .../libqt4-declarative_4%3a4.8.1-0ubuntu4.1_amd64.deb) ...
Unpacking replacement libqt4-declarative ...
Preparing to replace libqt4-network:i386 4:4.8.1-0ubuntu4 (using .../libqt4-network_4%3a4.8.1-0ubuntu4.1_i386.deb) ...
De-configuring libqt4-network ...
Unpacking replacement libqt4-network:i386 ...
Preparing to replace libqt4-network 4:4.8.1-0ubuntu4 (using .../libqt4-network_4%3a4.8.1-0ubuntu4.1_amd64.deb) ...
Unpacking replacement libqt4-network ...
Setting up libqt4-network (4:4.8.1-0ubuntu4.1) ...
Setting up libqt4-network:i386 (4:4.8.1-0ubuntu4.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 222545 files and directories currently installed.)
Preparing to replace libqt4-sql:i386 4:4.8.1-0ubuntu4 (using .../libqt4-sql_4%3a4.8.1-0ubuntu4.1_i386.deb) ...
De-configuring libqt4-sql ...
Unpacking replacement libqt4-sql:i386 ...
Preparing to replace libqt4-sql 4:4.8.1-0ubuntu4 (using .../libqt4-sql_4%3a4.8.1-0ubuntu4.1_amd64.deb) ...
Unpacking replacement libqt4-sql ...
Setting up libqt4-sql (4:4.8.1-0ubuntu4.1) ...
Setting up libqt4-sql:i386 (4:4.8.1-0ubuntu4.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 222545 files and directories currently installed.)
Preparing to replace libqt4-xmlpatterns:i386 4:4.8.1-0ubuntu4 (using .../libqt4-xmlpatterns_4%3a4.8.1-0ubuntu4.1_i386.deb) ...
De-configuring libqt4-xmlpatterns ...
Unpacking replacement libqt4-xmlpatterns:i386 ...
Preparing to replace libqt4-xmlpatterns 4:4.8.1-0ubuntu4 (using .../libqt4-xmlpatterns_4%3a4.8.1-0ubuntu4.1_amd64.deb) ...
Unpacking replacement libqt4-xmlpatterns ...
dpkg: error: dpkg status database is locked by another process
Error in function: 
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (2)

2012-05-06 09:11:45,375 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-05-06 09:11:45,376 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2012-05-06 09:11:45,387 ERROR: xorg:nvidia_current_updates: get_alternative_by_name(nvidia-current-updates) returned nothing
2012-05-06 09:11:45,802 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-05-06 09:11:45,803 DEBUG: nvidia_current_updates is not the alternative in use
2012-05-06 09:11:55,981 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-05-06 09:11:56,085 DEBUG: KMH enabled: True
2012-05-06 09:11:56,355 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-05-06 09:11:56,356 DEBUG: nvidia_current_updates is not the alternative in use
2012-05-06 09:11:56,462 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-05-06 09:11:56,462 DEBUG: nvidia_current_updates is not the alternative in use
2012-05-06 09:11:56,566 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-05-06 09:11:56,676 DEBUG: KMH enabled: True
```

---

### Post by Sunships on 2012-05-11
*Bump*

---

### Post by Sunships on 2012-05-13
No solution in jywarren's partner thread as yet either...

---

### Post by Sunships on 2012-08-07
Just wanted to bump this problem up - I have done a fresh install since I last posted here, and still have the same issue. 

Again, I can live with the problem just by changing the horizontal offset on my monitor, which means I can't see GRUB or other menus/output during boot, but since I don't really change these it doesn't matter.

However, I have started playing Civ5 using wine, and when I exit the game it seems to undo the effects of the offset, meaning when I exit half the desktop shifts to be off-screen. This is a little annoying, hence my renewed search for a solution. 

:)

---

### Post by licnep on 2012-08-12
I have the same (or a very similar) problem since upgrading to 12.04 .

My card is an ATI (Mobility Radeon HD 4500) and I enabled the proprietary drivers from the system settings (not the ones with "(post-release updates)" cause that fails to install).

Basically everything works normally, if i go on tty1 (ctrl-alt-f1) everything is still centered, but then if i go back on tty7 (ctrl-alt-f7), to see the window manager, everything is offset A LOT. It's unusable. The monitor is all black except a very small stripe on the left, that corresponds to the extreme right of my desktop .

I tested with several window/desktop managers and the problem still persists. Once you switch to a fullscreen text-only view, the regular view becomes unusable cause it's offset.
Hope we can find a solution. I'm available to try things, 
bye

---

### Post by Sunships on 2012-08-13
Thanks for stopping by licnep - good to know I'm not alone!

---

### Post by Sunships on 2012-08-16
Annnd, as if by magic, this seems to have fixed itself without me doing anything. There is now no relative difference in the offset between the display during boot and when running Ubuntu. Hooray?

When I open Civ5 in Wine there is still an offset...but this does not persist after the game is closed. I'm not worried about resolving this though, since I don't think I will play that often.

---

### Post by licnep on 2012-08-31
I solved it by following the instructions [here]("http://askubuntu.com/questions/142672/just-installed-ubuntu-12-04-when-booting-all-i-get-is-a-black-screen-with-curs").
What i did was:

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.confBACKUP
```

and reboot.


Keywords:
nvidia 12.04 upgrade update screen monitor offset black cursor

---

### Post by Sunships on 2012-08-31
Thanks for posting licnep - if this happens to me again I will try your instructions. :)

---

