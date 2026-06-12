---
title: "Anyone using Feisty under VirtualPC 2007 with a XP Dimension 9200?"
date: 2007-08-20
forum: Dell  Ubuntu Support
---

### Post by regisphilbin on 2007-08-20
I posted the same message in the dell community forums:

For some reason, i can't get the OS to recognize the Intel chipset USB ports or the Ethernet port. Am i missing Drivers? do i need to add files and configure text files? I'm a rookie with Linux in general so if anyone can point me in the right direction, i'd surely appreciate it...

Just FYI, I'm able to install Ubuntu after modifying the "xorg.conf" file to displaydepth = 16 bit instead of 24 bit. ([https://help.ubuntu.com/community/HowToConfigureUbuntuForMicrosoftVirtualPC2004](https://help.ubuntu.com/community/HowToConfigureUbuntuForMicrosoftVirtualPC2004))

After the install, I notice that i get the message that "usbfs is not supported. Skip mounting"

I looked at this page and made the changes it specifies but to no avail... ([https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/120109](https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/120109)) I'm not sure how to proceed.... TIA!

***another piece if info, I'm using the Dell 2405 Monitor with the memory card slots....not sure if this confuses the ubuntu OS.***

---

### Post by regisphilbin on 2007-08-22
Update here:

For those interested in installing Ubuntu as a Virtual Machine,  I'd suggest using VMware instead of Virtual PC.  With VMware (with the Dimension 9200),  It was able to recognize the USB ports and ethernet port where as I could not get it configured properly in Virtual PC.  Its probably the fact that I'm new to linux but at least I know that with VMWare,  I don't have to deal with these set up issues....

---

