---
title: "Highpoint RocketRaid 2640X4"
date: 2008-09-08
forum: Desktop Environments
---

### Post by mrholepunch on 2008-09-08
Hello!

I am having an issue installing Ubuntu 8.04 x86 on a desktop that utilizes 4 Fujitsu 15000rpm SAS drives on a HighPoint RocketRaid 2640X4. It seems that the default kernel does not have the RocketRaid driver installed, and thus making it very difficult to install Ubuntu with no hard drives showing. I have been able to insmod the pre-compiled driver during the install and modprobe it, allowing me to perform a full install. After rebooting, grub loads and the system halts at the Ubuntu logo. This is presumably happening from the lack of a scsi driver in the initrd. Does anyone know how to either add the driver to the initrd, or simplify the entire process by adding the driver to the installation media? Any suggestions or info would be greatly appreciated!

---

### Post by AllGamer on 2011-07-13
check this walkthrough out

[https://help.ubuntu.com/community/RocketRaid](https://help.ubuntu.com/community/RocketRaid)

it has all the information you need

---

