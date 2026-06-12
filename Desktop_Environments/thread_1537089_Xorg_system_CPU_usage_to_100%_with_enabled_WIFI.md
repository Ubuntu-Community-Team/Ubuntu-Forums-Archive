---
title: "Xorg system CPU usage to 100% with enabled WIFI"
date: 2010-07-23
forum: Desktop Environments
---

### Post by tobyS23 on 2010-07-23
Hi,

I'm facing a very strange problem on my Thinkpad T61p since some days. In most of the cases, when I switch on my WIFI chip hardware-wise, Xorg system CPU usage raises to 70-100% and fully stales the machine after a while. Switching off the WIFI chip resolves the problem again.

I tried killing different processes that might be involved like NetworkManager and friends and also removed the WIFI driver without any success. When I switch on the WIFI chip through the hardware switch, Xorg shows the presented behavior.

The issue is not always reproducable, but occurs in about 90% of the boots. Without being logged into X, the issue does not occur, although GDM is started.

System log, Xorg log and dmesg did not yield any helpful information, e.g. error messages.

I attached some apport debug information I generated while the issue is evident.

Has anyone an idea how I could attempt to further debug this problem or maybe even how to solve it?

TIA,
Toby

---

### Post by clrg on 2010-07-23
Download and install the latest drivers for your machine's wlan chip.

---

### Post by tobyS23 on 2010-07-23
I'm using IWL wifi, so I doubt there is a need to update the driver manually? Correct me please, if I'm mistaken.

Thx for your support,
cheers,
Toby

---

### Post by clrg on 2010-07-23
I'll ask again, do you have the latest versions of iwl3945 or iwl4965?

---

### Post by tobyS23 on 2010-07-23
I'm not sure if I can assess anything else here than that I'm using the latest Ubuntu kernel

```

Linux tango 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 07:54:58 UTC 2010 i686 GNU/Linux

```

since iwlagn ships with the kernel, I should state: Yes, I'm using the latest available driver for Ubuntu.

```

[   32.794995] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[   32.794997] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   32.795086] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   32.795122] iwlagn 0000:03:00.0: setting latency timer to 64
[   32.795180] iwlagn 0000:03:00.0: Detected Intel Wireless WiFi Link 4965AGN REV=0x4
[   32.851632] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 19 802.11a channels
[   32.851739] iwlagn 0000:03:00.0: irq 31 for MSI/MSI-X
[   32.876586] phy0: Selected rate control algorithm 'iwl-agn-rs'

```

Or am I missing something?

Regards,
Toby

---

### Post by clrg on 2010-07-23
Yes you can:
```
phirt@detox:~$ modinfo iwlagn
filename:       /lib/modules/2.6.32-23-generic/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko
alias:          iwl4965
license:        GPL
author:         Copyright(c) 2003-2009 Intel Corporation <ilw@linux.intel.com>
**version:        1.3.27k**
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
firmware:       iwlwifi-4965-2.ucode
<more blah blah>

```

Check your version. Then, search the internet for the latest version.

Edit: Fyi, if you want, read about kernel modules. Also, the kernel Ubuntu ships with is not the latest kernel, nor are the modules shipped with it. Ubuntu aims for stability, not actuality. That is perfectly fine in most cases, but sometimes there are bugs in the older versions that need to be fixed (and usually already are by the time of discovery through the user, so you just need the newest version). Someone needs to build a .deb (from the latest sources) and upload it into the repositories before you can get it as a regular update. Until then, you need to download, compile and install it yourself.

---

### Post by tobyS23 on 2010-07-23
> Edit: Fyi, if you want, read about kernel modules. Also, the kernel Ubuntu ships with is not the latest kernel, nor are the modules shipped with it. Ubuntu aims for stability, not actuality. That is perfectly fine in most cases, but sometimes there are bugs in the older versions that need to be fixed (and usually already are by the time of discovery through the user, so you just need the newest version). Someone needs to build a .deb (from the latest sources) and upload it into the repositories before you can get it as a regular update. Until then, you need to download, compile and install it yourself.

OK, now I understand what you mean. So basically, I will basically need to grab the latest kernel source and compile it in a way that it works properly together with Ubuntu. Is there a quick and easy way to do that or do I need to mess around with all the kernel config, boot images and other kernel mess?

Didn't I hear someone say "don't mess around with kernels in Ubuntu"?

FYI, the version here is

```
ilename:       /lib/modules/2.6.32-23-generic/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko
alias:          iwl4965
license:        GPL
author:         Copyright(c) 2003-2009 Intel Corporation <ilw@linux.intel.com>
version:        1.3.27k
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
firmware:       iwlwifi-4965-2.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-2.ucode
firmware:       iwlwifi-6050-4.ucode
firmware:       iwlwifi-6000-4.ucode
```

So, in order to check if the latest "driver" version fixes my issue, I need kernel 2.6.34.1.

Thanks for your help,
regards,
Toby

---

### Post by clrg on 2010-07-23
Nah. *sigh* As I said three times, you need the -->DRIVER<--. No need to recompile the whole kernel. Check the web for the latest version of the -->DRIVER<--. If you find it, compile and install. Leave the kernel alone!

Nee, ehrlich. Lies was über Kernelmodule, ja? Und wofür die gedacht sind. Ich will nicht böse klingen, aber das Konzept zu verstehen wäre nicht schlecht.) Kernel != Modul

---

### Post by tobyS23 on 2010-07-26
OK, I tried installation of the most recent drivers through the Ubuntu package "linux-backports-modules-wireless-generic" and tried it manually via compat-wireless-2.6.35-rc4 ([http://wireless.kernel.org/en/users/Download](http://wireless.kernel.org/en/users/Download)). The problem seemed to have vanished during the weekend, but suddenly occurred again this morning.

Here is the output of modinfo

```
$ modinfo iwlagn
filename:       /lib/modules/2.6.32-23-generic/updates/drivers/net/wireless/iwlwifi/iwlagn.ko
alias:          iwl4965
license:        GPL
author:         Copyright(c) 2003-2010 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
firmware:       iwlwifi-4965-2.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-2.ucode
firmware:       iwlwifi-6000g2a-4.ucode
firmware:       iwlwifi-6050-4.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-1000-3.ucode
srcversion:     29A2948B3F1222F837A1806
alias:          pci:v00008086d00000084sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00004229sv*sd*bc*sc*i*
… lots of these …
depends:        iwlcore,cfg80211,mac80211,compat_firmware_class
vermagic:       2.6.32-23-generic SMP mod_unload modversions 586 
parm:           swcrypto50:using crypto in software (default 0 [hardware]) (deprecated) (bool)
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           queues_num50:number of hw queues in 50xx series (deprecated) (int)
parm:           queues_num:number of hw queues. (int)
parm:           11n_disable50:disable 50XX 11n functionality (deprecated) (int)
parm:           11n_disable:disable 11n functionality (int)
parm:           amsdu_size_8K50:enable 8K amsdu size in 50XX series (deprecated) (int)
parm:           amsdu_size_8K:enable 8K amsdu size (int)
parm:           fw_restart50:restart firmware in case of error (deprecated) (int)
parm:           fw_restart:restart firmware in case of error (int)
parm:           disable_hw_scan:disable hardware scanning (default 0) (int)
parm:           ucode_alternative:specify ucode alternative to use from ucode file (int)

```

Any further suggestions?

Thanks in advance,
Toby

---

### Post by tobyS23 on 2010-07-28
OK, I tried investigating further. Seems the WIFI card is not the  critical point, but the Bluetooth module. When the system CPU goes to  100% I can use the HW kill switch to get my system back to normal. When I  turn the HW kill switch again, the problem re-occurs. Am I fast enough  then to issue

```
$ echo "disable" > /proc/acpi/ibm/bluetooth
```

system load is reduced to normal again. Enabling bluetooth again results again in 100% CPU system usage (produced by Xorg).

Anyone a suggestion?

TIA,
Toby

---

