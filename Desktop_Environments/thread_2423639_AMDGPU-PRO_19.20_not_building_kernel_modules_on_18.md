---
title: "AMDGPU-PRO 19.20 not building kernel modules on 18.04"
date: 2019-07-26
forum: Desktop Environments
---

### Post by RecceDG on 2019-07-26
I bit the bullet last night and upgraded my Ubuntu 16.04 LTS machine  to Ubuntu 18.04. The upgrade went well and the machine booted up fine.  However, I lost access to OpenCL, so I attempted to install the latest  AMDGPU-PRO drivers.

  The install script appeared to run fine, although I did notice  something about kernel modules - wasn't able to catch what it said  though as it scrolled up too quickly and it doesn't appear to be logged  anywhere.

  Upon completion, I rebooted. That got me to the Ubuntu login screen.  Attempting to log in just dropped me back into the login, which I know  is typical of an X Server crash.

  Hours of troubleshooting followed. dmesg confirmed that an amdgpu  library was segfaulting - but it also had no mention of amdgpu anywhere  in the output. As in "dmesg | grep amdgpu" would only return the message  about the segfaulting library (which corresponded to every gnome  session login attempt)

  After much mucking about with xorg.conf settings (to no avail) and  lacking a good hard error message somewhere in dmesg, syslog, or  Xorg.log that I recognized as a smoking gun, I ran the uninstall script.  That worked fine, but it also took out the X server, so I had to  reinstall the x packages from the distro. I am now back to a vanilla  Ubuntu installation with a functioning gnome session, but no OpenCL.

  I noticed during the uninstall process that the uninstaller was  complaining about not being able to find modules in  /lib/modules/4.15.0-55-generic/updates. This, coupled to the fact that  dmesg did not mention amdgpu anywhere leads me to believe that the  install script was not generating the kernel modules.

  So then... how do we troubleshoot this? I need OpenCL back and functioning.

  One other thing: when I do

```
 uname -a Linux karzai 4.18.0-25-generic #26~18.04.1-Ubuntu SMP Thu Jun 27 07:28:31 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux
```


  I *swear* that post amdgpu-pro-install --opencl=legacy that uname was returning 4.15.0-55-generic

  I have seen reports to the effect that amdgpu-pro did not play nice  with kernel 4.18.xx, so I checked that. I'm now very surprised to see  the machine running on 4.18.

  Card is an R9 Fury.

  Here is dmesg output for the current, working, vanilla install (so NOT amdgpu-pro)
  ```
dmesg | grep amdgpu
[ 12.089078] [drm] amdgpu kernel modesetting enabled.
[ 12.101265] fb: switching to amdgpudrmfb from VESA VGA
[ 12.101728] amdgpu 0000:04:00.0: Invalid PCI ROM header signature: expecting 0xaa55, got 0xffff
[ 12.101786] amdgpu 0000:04:00.0: VRAM: 4096M 0x000000F400000000 - 0x000000F4FFFFFFFF (4096M used)
[ 12.101787] amdgpu 0000:04:00.0: GTT: 1024M 0x0000000000000000 - 0x000000003FFFFFFF  
[ 12.101854] [drm] amdgpu: 4096M of VRAM memory ready
[ 12.101855] [drm] amdgpu: 4096M of GTT memory ready.
[ 12.401021] fbcon: amdgpudrmfb (fb0) is primary device
[ 12.493091] amdgpu 0000:04:00.0: fb0: amdgpudrmfb frame buffer device
[ 12.508288] [drm] Initialized amdgpu 3.26.0 20150101 for 0000:04:00.0 on minor 0`

```

---

### Post by Autodave on 2019-07-26
Upgrading from one release to another often causes problems like this. If it were my machine, I would d-l 18.04 and get it onto a bootable USB or DVD and boot from that and see if the graphics are working.

I learned a loooong time ago to only do clean installs after backing up everything to an external source.

---

### Post by QIII on 2019-07-26
It is always best when upgrading (it's even better to do a fresh install, in my opinion, but you are where you are) to remove any proprietary drivers.

In the case of AMDGPU-PRO, the open-source AMDGPU driver is available as part of the original Ubuntu installation, but the proprietary AMDGPU-PRO overlay is not.  Upgrading with AMDGPU-PRO still installed is almost sure to cause issues.

I recommend that you uninstall AMDGPU-PRO to see if you can get back to a usable system.  You can do that from the command line by issuing this command:

```
amdgpu-pro-uninstall
```

Reboot and see if you are now using just the open-source AMDGPU driver.  If you are up and running, then re-install AMDGPU-PRO.

---

