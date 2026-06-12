---
title: "libhal_drive_from_device_file() returns NULL on 64 bit Linux"
date: 2011-10-05
forum: Development CD/DVD Image Testing
---

### Post by laxmi_p on 2011-10-05
Hi All,

We use libhal to write to CD/DVD. It works fine on 32 bit Ubuntu 10.04 system. But on 64 bit Ubuntu 11.10 system it fails.
When we insert CD/DVD, we see /dev/sr0 block device. But call to libhal_drive_from_device_file() returns NULL and errno is set to 11. 
On 64 bit system libhal version is 0.5.14.6
On 32 bit system it is 0.5.14.Oubuntu6.
 I downloaded the souce and there is no difference between the two versions. 

Any idea, why it fails? I appreciate your immediate help.

Thanks,
Latha

---

### Post by laxmi_p on 2011-10-12
I use Ubuntu 11.10 Beta 1 version. Not sure whether libhal problem will be fixed in 11.10 release version.  Is there anyway I can check on this with Ubuntu development team?

---

