---
title: "Problems with nVidia"
date: 2005-12-17
forum: Desktop Environments
---

### Post by oxEz on 2005-12-17
Since a week or so, I always have to reinstall nvidia drivers each time I boot Ubuntu. The modules 'does' load, (lsmod | grep nvidia tells me). 

I thought at first it was my custom kernel (2.6.14-nitro2), but it seems it does the same thing with the -k7 and -686 from ubuntu repos. I tryied the version 7667 from nvidia.com and ubuntu repos, and 8174 from nvidia.com. What happens is: when I boot, X tryies to start, and I just get that blue screen that X  was not able to start.. Then the screen hangs for a few secs and I have to reinstall drivers through tty to get to X.

I'll post my /var/log/Xorg.log, as an attachement.. My system specs are in my signature.

Thank you!

---

### Post by pmj on 2005-12-17
Bump.

I have the exact same problem.

---

### Post by maken on 2005-12-17
same problem too.
i had to install the default package of nvidia drivers, 8174 worked fine until reboot.

---

### Post by MartinG on 2005-12-18
[QUOTE=maken]same problem too.
i had to install the default package of nvidia drivers, 8174 worked fine until reboot.[/QUOTE]

See this thread:

[http://www.ubuntuforums.org/showthread.php?t=103030](http://www.ubuntuforums.org/showthread.php?t=103030)

---

### Post by oxEz on 2005-12-26
Sorry the late response, I was very busy with holidays ! ;) 

I ran an apt-get remove *nvidia*, uninstalled restricted-modules, and removed the nvidia script from /etc/init.d, and then reinstalled the nvidia 8174 package.

Now it works like a charm :o

---

### Post by rupert on 2006-01-03
when I try to uninstall the packet  linux-restricted-modules-2.6.12-10-686-smp apt tries to uninstall also the kernel which im currently running.
Is there a safe way to get across this?
I made a modinfo on the nvidia module that is loaded while booting but dont work, and a modinfo with the module right after compiling, which works:
```

filename:       /lib/modules/2.6.12-10-686-smp/volatile/nvidia.ko
license:        NVIDIA
alias:          char-major-195-*
vermagic:       2.6.12-10-686-smp SMP 686 gcc-3.4
depends:        agpgart
alias:          pci:v000010DEd*sv*sd*bc03sc00i00*
parm:           NVreg_RmLogonRC:int
parm:           NVreg_VideoEnhancement:int
parm:           NVreg_DevicesConnected:int
parm:           NVreg_FlatPanelMode:int
parm:           NVreg_ResmanDebugLevel:int
parm:           NVreg_DeviceFileMode:int
parm:           NVreg_DeviceFileGID:int
parm:           NVreg_DeviceFileUID:int
parm:           NVreg_ModifyDeviceFiles:int
parm:           NVreg_Mobile:int
parm:           NVreg_SoftEDIDs:int
parm:           NVreg_EnableAGPFW:int
parm:           NVreg_EnableAGPSBA:int
parm:           NVreg_NvAGP:int
parm:           NVreg_ReqAGPRate:int
parm:           NVreg_EnableALiAGP:int
parm:           NVreg_EnableVia4x:int
parm:           NVreg_VideoMemoryTypeOverride:int
parm:           nv_disable_pat:int
----after-install---
filename:       /lib/modules/2.6.12-10-686-smp/volatile/nvidia.ko
license:        NVIDIA
alias:          char-major-195-*
vermagic:       2.6.12-10-686-smp SMP 686 gcc-3.4
depends:        agpgart
alias:          pci:v000010DEd*sv*sd*bc03sc00i00*
parm:           NVreg_VbiosFromROM:int
parm:           NVreg_DetectPrimaryVga:int
parm:           NVreg_UseCPA:int
parm:           NVreg_RemapLimit:int
parm:           NVreg_RmLogonRC:int
parm:           NVreg_VideoEnhancement:int
parm:           NVreg_DevicesConnected:int
parm:           NVreg_FlatPanelMode:int
parm:           NVreg_ResmanDebugLevel:int
parm:           NVreg_DeviceFileMode:int
parm:           NVreg_DeviceFileGID:int
parm:           NVreg_DeviceFileUID:int
parm:           NVreg_ModifyDeviceFiles:int
parm:           NVreg_Mobile:int
parm:           NVreg_SoftEDIDs:int
parm:           NVreg_EnableAGPFW:int
parm:           NVreg_EnableAGPSBA:int
parm:           NVreg_NvAGP:int
parm:           NVreg_ReqAGPRate:int
parm:           NVreg_EnableALiAGP:int
parm:           NVreg_EnableVia4x:int
parm:           NVreg_VideoMemoryTypeOverride:int
parm:           nv_disable_pat:int

```

---

