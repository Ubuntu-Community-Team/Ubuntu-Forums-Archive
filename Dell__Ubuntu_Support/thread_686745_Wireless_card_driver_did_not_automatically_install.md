---
title: "Wireless card driver did not automatically install"
date: 2008-02-03
forum: Dell  Ubuntu Support
---

### Post by CloudFX on 2008-02-03
Hi, I recently put Ubuntu Gusty Gibbon 7.10 on my computer. I'm running a Dell Inspiron 1521 dual booting Windows Vista and Ubuntu. When I installed Ubuntu, all the drivers automatically installed, and I'm wondering if all Inspiron 1521's don't automatically install their wireless driver. If this is the case, how can I manually install it, and if I'm alone, what should I do?

Thanks,
CloudFX

---

### Post by faulkes on 2008-02-03
> **CloudFX said:**
> Hi, I recently put Ubuntu Gusty Gibbon 7.10 on my computer. I'm running a Dell Inspiron 1521 dual booting Windows Vista and Ubuntu. When I installed Ubuntu, all the drivers automatically installed, and I'm wondering if all Inspiron 1521's don't automatically install their wireless driver. If this is the case, how can I manually install it, and if I'm alone, what should I do?

Thanks,
CloudFX

Depends on which wireless card shipped with your laptop, the intel or broadcom

IIRC both have drivers in the restricted driver manager, however only the intel card has an OSS driver.  My experience has been that the broadcom card is better supported by ndiswrapper/windows driver based installation than the driver in the RDM.

You can find the restricted driver manager under 

```

System->Administration->Restricted Drivers Manager

```

Faulkes

---

### Post by CloudFX on 2008-02-03
The two things that appear in my restricted drivers are my ATI accelerated graphics driver, and something called Firmware for Broadcom 43xx chipset family. How can I find out if I have a broadcom or intel wireless card?

Btw, I enabled to graphics driver, but the other one requires me to open the firmware.

---

### Post by faulkes on 2008-02-03
> **CloudFX said:**
> The two things that appear in my restricted drivers are my ATI accelerated graphics driver, and something called Firmware for Broadcom 43xx chipset family. How can I find out if I have a broadcom or intel wireless card?

Btw, I enabled to graphics driver, but the other one requires me to open the firmware.

```

lspci | grep -i net

```

That should scan the pci bus for any connected network controllers, all bets are that you have the broadcom card.  My suggestion with those stands, to use ndiswrapper and the windows driver (you'll have to read up on that but it isn't complicated).

Faulkes

---

### Post by CloudFX on 2008-02-03
I read up on ndiswrapper, but I don't quite understand it. Would you be able to set me up with some links please? 

Thanks for everything!
CloudFX

---

### Post by faulkes on 2008-02-03
> **CloudFX said:**
> I read up on ndiswrapper, but I don't quite understand it. Would you be able to set me up with some links please? 

Thanks for everything!
CloudFX

Open the synaptic package manager and search for ndiswrapper.

Install the two ndiswrapper applications (there is a gui as well, but I have never used it).  You need the kernel module and the user space utilities.

You will also need a copy of the dell supplied windows drivers (extracted), these are usually located in the C:\DRIVERS\NETWORK\ADDON folder supplied by the default dell install.  Typically the file is called BCMWL5.INF but this may vary depending on the card.

Then see the ndiswrapper wiki at the [NDISwrapper]("http://ndiswrapper.sourceforge.net") site about installing the drivers.  You do NOT need to do everything that is there but you will need to install the windows drivers, see the section entitled "Install Windows Driver" under the Installation link,  this is typically done via

```

sudo ndiswrapper -i /path/to/BCMWL5.INF

```

You can check if it succeeded and found a card by using:

```

ndiswrapper -l

```

If all went well and the card was found, you should be able to connect to wireless networks.

You can check this via commands such as:

```

sudo iwlist eth1 scan
- eth1 is normally the default wireless ethernet device on dell laptops

and 

iwconfig

```

Faulkes

---

### Post by CloudFX on 2008-02-03
Thanks a lot! I'm on Windows right now, but I'll try that out later.

CloudFX

---

### Post by CloudFX on 2008-02-03
I found out it was a broadcom. The .inf file for me is bcmwl6.inf, and when I typed those thing into Terminal, it said driver bcmwl6 is already installed. When I typed ndiswrapper -l, I got an invalid driver! message.

---

### Post by faulkes on 2008-02-03
> **CloudFX said:**
> I found out it was a broadcom. The .inf file for me is bcmwl6.inf, and when I typed those thing into Terminal, it said driver bcmwl6 is already installed. When I typed ndiswrapper -l, I got an invalid driver! message.

Can you post the output of

```

ndiswrapper -l

AND 

lspci | grep -i net

AND

lsmod | grep ndis

```

As well, check /var/log/messages or secure for any messages relating to the ndiswrapper or the card itself, as well as dmesg.  If tehre is anything there, paste the output back here.

Faulkes

---

