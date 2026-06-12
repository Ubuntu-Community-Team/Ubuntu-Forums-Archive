---
title: "Problem Blacklisting Hash now preventing login"
date: 2023-04-06
forum: Desktop Environments
---

### Post by shag00 on 2023-04-06
This issue started with 21.10 and was nothing more than a nuisance but this week after the update containing a lot of Nvidia related updates my system freezes during login, that is I can no longer login normally. I am able to login by selecting to login through the recovery option.

I infrequently also get a few lines about Bluetooth problems:
bluetooth: hcio10: FW download error recovery failed (-19)
bluetooth: hcio10: FW sending frame failed (-19)
bluetooth: hcio10: FW Failed to read MSFT supported features (-19)
bluetooth: hcio10: FW Malformed MSFT vendor event: 0x02

It appears that the 0x02 line refers to the device sending a flag 2 when it is actually a flag 1. The bluetooth device itself is the built in one on the MSI X570 Unify motherboard, not a dongle. I have tried disabling bluetooth in [COLOR=#232629][FONT=ui-monospace]/etc/bluetooth/main.conf>[/FONT][/COLOR][COLOR=var(--black-800)][FONT=var(--ff-mono)]AutoEnable=false with no effect. Any suggestions?[/FONT][/COLOR]

---

### Post by ActionParsnip on 2023-04-07
Ubuntu 21.10 reached end of life on July 14, 2022. I suggest you upgrade to a newer release. You can upgrade directly to 22.04 which is LTS and supported for 5 years. Alternatively you can wipe the install off and do a clean install of Ubuntu 22.04 from USB/DVD/CD. You can restore your user data from your backups

---

### Post by shag00 on 2023-04-07
To clarify, I am using 22.10:

Operating System: Kubuntu 22.10
KDE Plasma Version: 5.25.5
KDE Frameworks Version: 5.98.0
Qt Version: 5.15.6
Kernel Version: 5.19.0-38-generic (64-bit)
Graphics Platform: X11
Processors: 16 × AMD Ryzen 7 5800X 8-Core Processor
Memory: 15.5 GiB of RAM
Graphics Processor: llvmpipe
Manufacturer: Micro-Star International Co., Ltd.
Product Name: MS-7C35
System Version: 2.0

---

