---
title: "Virtualbox Error Message VERR_INVALID_PARAMETER"
date: 2010-01-29
forum: Desktop Environments
---

### Post by dell_boy on 2010-01-29
Hi guys,

I'm running Ubuntu 9.10 with Virtualbox 3.0.8-OSE on a Toshiba Satellite Pro laptop. I get the following VERR_INVALID_PARAMETER error message when trying to use the -partitions option in VBoxManage. I'm running Debian Lenny on another machine using Virtualbox 1.6.6-OSE and it works ok. Is it a problem with Ubuntu or the later version of VB.

```
steve@steve-laptop:~$ sudo VBoxManage internalcommands createrawvmdk -filename
 WinXP4.vmdk -rawdisk /dev/sda
VirtualBox Command Line Management Interface Version 3.0.8_OSE
(C) 2005-2009 Sun Microsystems, Inc.
All rights reserved.

RAW host disk access VMDK file WinXP4.vmdk created successfully.

steve@steve-laptop:~$ sudo VBoxManage internalcommands createrawvmdk -filename WinXP5.vmdk
 -rawdisk /dev/sda -partitions 1 -relative
VirtualBox Command Line Management Interface Version 3.0.8_OSE
(C) 2005-2009 Sun Microsystems, Inc.
All rights reserved.

Error while creating the raw disk VMDK: VERR_INVALID_PARAMETER
The raw disk vmdk file was not created

steve@steve-laptop:~$ sudo VBoxManage internalcommands createrawvmdk -filename WinXP5.vmdk
 -rawdisk /dev/sda -partitions 1
VirtualBox Command Line Management Interface Version 3.0.8_OSE
(C) 2005-2009 Sun Microsystems, Inc.
All rights reserved.

Error while creating the raw disk VMDK: VERR_INVALID_PARAMETER
The raw disk vmdk file was not created

steve@steve-laptop:~$ 
```

---

