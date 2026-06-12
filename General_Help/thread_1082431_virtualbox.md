---
title: "virtualbox"
date: 2009-02-27
forum: General Help
---

### Post by Ofloo on 2009-02-27
Hi, I'm trying to run window xp for my flatbed scanner on virtualbox but for some reason it's not seeing usb devices, I've found several howto's regarding this issue, however none of them seem to work, .. when I type id to check if I'm added to the appropriate group I see vboxusers is listed though without result, ..

I'm currently running hardy heron 8.10 and I've installed virtualbox from apt-get, ose which isn't supporting usb however I went through the steps described on [https://help.ubuntu.com/community/VirtualBox#USB](https://help.ubuntu.com/community/VirtualBox#USB)

Anyone any suggestions ?

---

### Post by silent contender on 2009-02-27
Is the scanner recognized by Ubuntu?  I think if Ubuntu reads the scanner, then virtualbox can't read it, and vice versa.  Disable (or unmount, don't know the right term for it) the scanner in Ubuntu.  I don't know if you've already does this.

Please someone correct me if I'm wrong.  I'm not 100% sure.

---

### Post by howefield on 2009-02-27
> **Ofloo said:**
> I'm currently running hardy heron 8.10 and I've installed virtualbox from apt-get, ose which isn't supporting usb however I went through the steps described on [https://help.ubuntu.com/community/VirtualBox#USB](https://help.ubuntu.com/community/VirtualBox#USB)

To clarify, are you running the OSE version or the PUEL version from the virtualbox website ? Only the PUEL version supports usb.

---

### Post by Ofloo on 2009-03-05
Indeed it was due the puel version, once I installed that version all worked fine, however I was under the impression from the howto that you where supposed to use the ose version.

Thank you guys for your reply.

---

