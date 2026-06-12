---
title: "pleas help me"
date: 2009-01-26
forum: General Help
---

### Post by hittooo on 2009-01-26
How to run in Linux wi fi?

---

### Post by mb_webguy on 2009-01-26
It depends on your system.  And without more information about your system, such as the make and model of your wireless card, it's very hard to advise you.

Most wireless cards just work in Ubuntu with no additional work.  Some cards, however, are not well supported in Linux, and you have to use the Windows driver.

If you need to use the Windows driver, you should first locate the driver.  If you have a Dell or HP, you can locate and download the driver from their website.  Otherwise, you'll have to search the web.  Once you have the driver (which is an .inf file), you should install the package ndis-gtk using Synaptic or with the command "sudo apt-get install ndis-gtk" in the terminal.  Once that is installed, go to System->Administration->Windows Wireless Drivers, click Add Driver, and locate the driver you downloaded.  Once that is done (and perhaps after a reboot), you should be able to connect to wireless networks.

Although like I said, this is only if your wireless card isn't supported by Linux.  Without more information about your situation, it's really hard to help.

---

### Post by hittooo on 2009-01-26
thank you

---

