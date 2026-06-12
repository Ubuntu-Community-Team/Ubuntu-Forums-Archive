---
title: "Uninstall Virtualbox"
date: 2009-04-18
forum: General Help
---

### Post by ssdt on 2009-04-18
I installed Virtualbox but I do not need it any more. So I tried to uninstall it from Sypnetec and Add/Remove but it i didn't find anything. Can anyone tell me how i can uninstall Sun xVM Virtualbox

Thanks

---

### Post by chriskin on 2009-04-18
how did you install it? if it was from a deb, it is supposed to be on synaptic

---

### Post by ssdt on 2009-04-18
I got it from their own site. I think i downloaded the verion with i386 not amd one because my comptuer's Dell 530N.

---

### Post by chriskin on 2009-04-18
what i asked was about how you installed it though, not where you got it from :)

was it a .deb file or a .tar.gz that you had to "make/make install" it in the terminal?

---

### Post by chriskin on 2009-04-18
taken from their own manual

> 2.4.3 Uninstallation
    Note: If you have installed VirtualBox inside one or more local zones,
    you must halt all zones that are referencing the VirtualBox device
    (/dev/vboxdrv) before uninstalling VirtualBox. This is required for prop-
    erly unloading the VirtualBox kernel driver without requiring a full system
    reboot. Use the zoneadm command to halt a zone.
  Uninstallation of VirtualBox on Solaris requires root permissions. To perform the
uninstallation, start a root terminal session and execute:
pkgrm SUNWvbox
  After confirmation, this will remove VirtualBox from your system.
  To uninstall the VirtualBox kernel interface module, execute:
pkgrm SUNWvboxkern


---

### Post by ssdt on 2009-04-18
Thank you for the information but I didn't understand it clearly. I had downloaded and installed a .deb package from their website. But it seemed not to uninstall from their own site.

---

### Post by chriskin on 2009-04-18
did you use the commands given on the quote i wrote? i didn't check if they work, they are at virtualbox's manual pdf

---

### Post by ssdt on 2009-04-18
I used *make install* to install the package. Hope this would help you help me remove this.

---

### Post by chriskin on 2009-04-19
> **chriskin said:**
> did you use the commands given on the quote i wrote? i didn't check if they work, they are at virtualbox's manual pdf


as i said, did you use the commands given in the quote?
i can't help you if you don't want to be helped :S

---

### Post by ssdt on 2009-04-19
Yes i did, and now I'm trying to uninstall it.

---

### Post by Rival11 on 2009-12-20
You can uninstall virtual box via the synaptic package manager if you are using Ubuntu 9.10 (System --> administration --> synaptic package manager).

The trick is to not do a quick search - hit the search icon (directly next to the quick search box) and simply search for "virtual" - virtualbox will then show up - simply mark for removal and apply your changes - even if you have a bad install, it will be removed completely.

One last important note: if you are trying to install the most current version of virtual box after uninstalling via the method above...if the virualbox icon does not appear under your system tools for launch, wait a couple of minutes, if it still does not appear....simply re-install the 3.1 package and it will be successful.

Hope this helps anyone.

---

### Post by Raoul Duke, esq. on 2011-01-12
Thank You! Huge help.

---

