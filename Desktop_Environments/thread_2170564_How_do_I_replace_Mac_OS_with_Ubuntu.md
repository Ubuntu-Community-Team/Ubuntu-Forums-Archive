---
title: "How do I replace Mac OS with Ubuntu"
date: 2013-08-26
forum: Desktop Environments
---

### Post by Music_Guy on 2013-08-26
I have Ubuntu 13.xx on a PC, and I'm seriously considering putting it onto my iMac. Will Ubuntu install on a Mac the same way it does on a PC? Or will I have to do something differently.

---

### Post by lah7 on 2013-08-29
**Welcome to the community forums!** I don't have an Apple Mac myself but I do know you will need some software called **BootCamp **for dual-booting. This allows you to boot your Mac between OS X and another OS like Ubuntu. This procedure can vary depending on your model.

I have come across this resource which I think will help you:
[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

In particular the **"Single Boot: Ubuntu Only"** part of the guide.

It's also pointed out that it's recommended to keep a copy of Mac OS X in case of a problem, firmware update or if you decide to switch back.

---

### Post by buzzingrobot on 2013-08-30
While you can install and run Ubuntu via Bootcamp, it isn't necessary and probably just adds more things that could go wrong.  The drivers supplied in Bootcamp are for Windows and won't help at all in Ubuntu.

OS X boots in EFI mode. The machine has no BIOS.  Ubuntu offers a Mac install image that uses EFI mode, plus an image that uses a BIOS compatibility mode, as does Bootcamp.

The latter is often easier to install, but if the machine has two video chips, like MacBooks, an EFI install may be needed before the kernel recognizes both.

Fan control, as in the fans run maxed out all the time, is often an issue. 

Before you try it, check for tutorials, especially those for your specific iMac model. That's listed in About This Mac.

Finally, shrinking the OS X partition and installing Ubuntu may be preferrable to removing OS X. If nothing else, you can't do firmware updates in Ubuntu.

---

