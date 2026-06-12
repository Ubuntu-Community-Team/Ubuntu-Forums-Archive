---
title: "PCMCIA Express Card"
date: 2010-02-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by gibbylinks on 2010-02-10
Has anyone managed to get the PCMCIA Express card slot working ?

I bought an adaptor for Compact Flash cards but it's totally ignored ;0(

---

### Post by tannalv on 2010-05-06
> **gibbylinks said:**
> Has anyone managed to get the PCMCIA Express card slot working ?

I bought an adaptor for Compact Flash cards but it's totally ignored ;0(

[https://help.ubuntu.com/community/ExpressCard]("https://help.ubuntu.com/community/ExpressCard")

[I]To do the equivalent of this last command in Ubuntu 9.10 pass the "pciehp.pciehp_force=1" to the kernel by editing /etc/default/grub file( See Grub2 ). Add it to the line 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
so it appears as 

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pciehp.pciehp_force=1"

Save and exit your text editor. Then run: 

sudo update-grub

And reboot.[/I]

---

