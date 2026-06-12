---
title: "Brother DCP-7020 Scan Button Support"
date: 2006-08-29
forum: Desktop Environments
---

### Post by frio on 2006-08-29
Does anyone know how to, or know of linux drivers capable of allowing the scan button to work on the Brother DCP-7020 (or a similar device)? I have CUPS printing working and scanning is working via sane and xsane. I would really like to get the scan button working so I do not have to log on the server to scan something.

Any ideas?

---

### Post by Tommy on 2007-11-05
> **frio said:**
> Does anyone know how to, or know of linux drivers capable of allowing the scan button to work on the Brother DCP-7020 (or a similar device)? 

Have you found the answer? There is a package called scanbuttonsd but it doesn't know the button codes for Brother. That would be the best place to start.

I haven't had a chance to tinker with the buttons yet -- I saw your post because I am trying to fix my DCP-7020 as a PRINTER after upgrading to Ubuntu Gutsy 7.10. The scanner still seems to work fine -- I just had to restore the changes I had made to a sane configuration file and a UDEV file (with the USB code).

EDIT: Upon reading several other forums here I realized there is NEWER software at the Brother web site, including something about the buttons. I will try it, but after I get printing working. For more details, look up your printer at [http://solutions.brother.com/linux/sol/printer/linux/sane_drivers.html](http://solutions.brother.com/linux/sol/printer/linux/sane_drivers.html)

---

### Post by ludovicc on 2007-11-10
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/161855](https://bugs.launchpad.net/ubuntu/+bug/161855) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hello,

I've got a Brother DCP 7025 and Gusty 64 bits. 

To install the printer, I had no problems, I simply used the Administration > Printers configuration, selected my printer model and it just worked. It's not using the official Brother printer drivers, apparently it's using the BR-Script3 compatibility mode of the printer (the printer native language is Windows GDI, so I wonder if there might be any loss of quality or functionality here).

To install the scanner, I had to add the following line to /etc/udev/rules.d/45-libsane.rules:

# Brother DCP 7025
SYSFS{idVendor}=="04f9", SYSFS{idProduct}=="0184", MODE="666", GROUP="scanner"

Now my scanner is also working.

I have tried to install scanbuttond, but it doesn't work at all. I will try to contact the developer and if I find a solution I'll keep you informed.

Cheers, Ludovic

---

### Post by garydale on 2007-12-21
I'm running 7.10 on an AMD64 system and am having no luck with the Brother DCP-7020 scanner or printer. I've tried the simple install - Ubuntu sees the printer but won't print. I've tried the drivers on Brother's site but they only provide an i386 binary and I'm not sure how to install the source cups wrapper - I untarred it and tried running the appropriate script but it gave errors.

I did install the drivers for the scanner portion and updated the udev information but still get the error others have reported when xsane starts.

Has anyone gotten the DCP-7020 (not 7025) to work?

---

### Post by grandmk on 2007-12-27
See my step-by-step instructions I just posted at 

[http://ubuntuforums.org/showthread.php?p=4026344#post4026344](http://ubuntuforums.org/showthread.php?p=4026344#post4026344)

Cheers :)

---

