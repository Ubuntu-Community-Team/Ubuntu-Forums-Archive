---
title: "Help with 32 bit libraries for 64 bit video drivers"
date: 2010-09-11
forum: Gaming &amp; Leisure
---

### Post by Halymaly on 2010-09-11
I am getting the following error when I try to run DDO with wine (and pyLotro).

```
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  137 (GLX)
  Minor opcode of failed request:  5
 (X_GLXMakeCurrent)
  Serial number of failed request:  634
  Current serial number in output stream:  634

*** Finished ***
```

After some searching I think the reason is that I am missing (or have incorrectly configured) 32-bit libraries. 

I downloaded the latest ATI drivers (for my Radeon HD 4870) from here: [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English). It has the same download file whether or not I select 64-bit driver download. On that page it also says, "32-Bit packages must be installed for 64-Bit Linux drivers to install or work." but I don't know how to get those.

I have tried uninstalling and reinstalling the drivers a few times and even reinstalled my OS but still the same error. I am using the newest (non-test) version of Wine and Ubuntu 10.04

Does anyone know how I can check to see if I actually have the 32-bit libraries, or how to get them and configure them properly?

Thank you.

---

### Post by Naiki Muliaina on 2010-09-11
sudo apt-get install ia32-libs

:)

---

### Post by Halymaly on 2010-09-11
Thank you for the reply. This is the result:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ia32-libs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Still the same error.

---

