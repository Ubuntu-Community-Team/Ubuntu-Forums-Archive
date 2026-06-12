---
title: "Fails to boot"
date: 2010-06-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by p4nts on 2010-06-19
I have a Dell Studio 1747.

It has been stalling on boot with GRUB2.
I tried the test boot [fix]("http://ubuntuforums.org/showthread.php?t=1406666") (removing the quiet splash options) unfortunately this has not worked for me and it can take 4 or five attempts to boot successfully. 

The boot stops at pages shared and pages non-shared.


Does anyone have any tips on how to further debug this. 

Thanks

---

### Post by wilee-nilee on 2010-06-19
Post the script in my sig in code tags so we can see whats on the computer and where it's at

---

### Post by p4nts on 2010-06-19
.

---

### Post by p4nts on 2010-06-19
> **wilee-nilee said:**
> Post the script in my sig in code tags so we can see whats on the computer and where it's at


Thanks wilee for the quick reply.

After I posted I just spotted that an update for the Radeon driver was [COLOR=DarkRed][released]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.2&product=2.4.2.3.32&lang=English")[/COLOR] on the 16th, though its not in Synaptic yet? 

Uninstalled and installed this a couple of times in various embarassing forms ( directly and using [this]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates") However this left me with strange artifacts in Flash on Chrome. 

I used ppa-purge to rollback the X.org ppa changes but it seems to have left the new Radeon driver installed. Things appear to be okay having  rebooted successfully a couple of times, will see how it goes over the next few days. 


Not sure what problems I have set up for myself with Synaptic though?


I noticed this > [Ubuntu 10.04] X segmentation faults on startup on multi-ASIC systems in the driver [release notes]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_106_linux.pdf").

---

