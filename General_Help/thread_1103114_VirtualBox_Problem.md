---
title: "VirtualBox Problem"
date: 2009-03-22
forum: General Help
---

### Post by kentcb on 2009-03-22
Hi all,

I'm trying to run XP as a guest inside an Intrepid host. I want bridged (host interface) networking rather than NAT. However, when I select it in the options and try to boot the XP image, I get this:

```
Failed to initialize Host Interface Networking.
VBox status code: -3100 (VERR_HOSTIF_INIT_FAILED).


Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
Console
Interface: 
IConsole {e3c6d4a1-a935-47ca-b16d-f9e9c496e53e}
```

Any ideas?

Thanks

---

### Post by ju2wheels on 2009-03-22
Which version of Vbox are you using OSE or closed source?

You may just be missing the VBox drivers on your Intrepid Host.

---

### Post by kentcb on 2009-03-22
> **ju2wheels said:**
> Which version of Vbox are you using OSE or closed source?

OSE. Installed via the Add/Remove menu. Would that install necessary drivers too?

---

### Post by ju2wheels on 2009-03-22
Applications->Accessories-> Terminal:

```

sudo apt-get install virtualbox-ose-source

```

---

