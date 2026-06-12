---
title: "kernel upgrade turn amd video graphics experience sluggish"
date: 2012-02-19
forum: Desktop Environments
---

### Post by jao_madn on 2012-02-19
Hi,

I would like to ask related to video graphics driver specifically the AMD (radeon HD 7000 series) or had someone with the same experience or problem that im currently experiencing and willing to share some info. I understand that the kernel is self contain it will not affect the installed driver on the system but as i observed on my AMD six core desktop my display will turn sluggish or had some delay when i used the current kernel not the kernel i used to installed the graphics driver. When i fresh installed the lucyd 64bit and update to the current kernel which is 2.6.32-37-generic this is the kernel i used to installed all my application and specially the AMD catalyst driver for linux. But as i observed and update the system which currently as of now has kernel version of 2.6.32-38-generic and 2.6.32-39-generic. When i used this current kernel or besides from the 2.6.32-37-generic my display will turn to sluggish or had some delays as i move or drag open windows explored or application.

My questions:
1. Does i miss something like modules/driver needs to update when i update the kernel. (i had experience with my wifi usb dongle, every time a new kernel release i need to compile the driver/modules in order to function in the newly installed kernel.
2. Or i need to reinstall the AMD catalyst driver every time a new kernel update.(that would be cumbersome)

Or any information that may somehow help me with my problem..as of now im using the old kernel.

Thanks in advance for any input that may help.

---

### Post by 3Miro on 2012-02-19
Technically the proprietary drivers need to be reinstalled for eevry new kernel version, however, Ubuntu is supposed to do that automatically, but on rare occasions it fails. 

You have probably been hit by a bug, you can reinstall the AMD driver manually (from Additional Driver, remove, reboot, activate, reboot). If this doesn't fix the issue, then the bug is with the kernel update. You can file a bug report and use the old kernel until a new update fixes the issue.

---

### Post by 2F4U on 2012-02-19
I guess that you nailed the sluggishness down to the graphics drivers? Or could there be other reasons, maybe programs running in the background?

---

### Post by jao_madn on 2012-02-19
> **2F4U said:**
> I guess that you nailed the sluggishness down to the graphics drivers? Or could there be other reasons, maybe programs running in the background?

I highly believe it is in the graphics side of things..since the program i used in the old kernel and the new currenly updated kernel is the same..thats why i dont use the new once..

I never tried to installed the proprietary driver in the newly installed kernel. I want first to get some info before i hit that road for every kernel update..

---

### Post by 3Miro on 2012-02-19
> **jao_madn said:**
> 
I never tried to installed the proprietary driver in the newly installed kernel. I want first to get some info before i hit that road for every kernel update..

You have to manually reinstall the driver only if you get it directly from AMD and this is not the recommended way. So long as you use the Additional Drivers tool, you should not have to reinstall the driver. If something went wrong on this update, then it will probably be fine for the next one.

---

### Post by jao_madn on 2012-02-21
> **3Miro said:**
> You have to manually reinstall the driver only if you get it directly from AMD and this is not the recommended way. So long as you use the Additional Drivers tool, you should not have to reinstall the driver. If something went wrong on this update, then it will probably be fine for the next one.

I now understand the problem its in the driver having problem in a newly/current kernel. I tried it on the costume kernel and the newly updated kernel. the sluggishness dis-appear in the kernel in which i installed the driver.

Im using the driver directly from the AMD site. I want to try the additional hardware, but the problem it doesn't detect the hardware anymore..

---

