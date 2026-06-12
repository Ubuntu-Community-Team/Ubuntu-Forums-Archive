---
title: "Install on Easynote Laptop freezes on boot at 70%"
date: 2009-03-28
forum: General Help
---

### Post by siabost on 2009-03-28
Hi,
Packard Bell EasyNote Laptop F5280HR
Celleron 2.8Ghz
768Mb Memory Installed (64Mb of this used for graphics)

Managed to install Ubuntustudio eventually by adding vga=771 to boot command.

On booting from hard disk loading freezes at about 70%.

I think I have a screen resolution problem.

How do I set the screen resolution from the command line & what should I set it to? 800x600?

Any help appreciated.

Thanks

---

### Post by 3Miro on 2009-03-28
Unfortunately Laptop hardware is so specific that sometimes you run into big driver problems.

The screen resolution is managed either by the monitor settings or by manually configuring /etc/xorg.conf. Look up tutorials on how to edit xorg.conf

---

### Post by siabost on 2009-03-28
Extra info:

The Video adapter is a SiSM661FX. And the SiS website says SiS661FX is supported in the Linux kernel (although the "M" may signify some tinkering by Packard Bell).

:)

---

### Post by siabost on 2009-03-29
More extra info.

It freezes at this point (last 5 lines shown):
> cat: /var/lib/acpi-support/system-manufacturer:No such file or directory
cat: /var/lib/acpi-support/system-product-name:No such file or directory
cat: /var/lib/acpi-support/system-product-version:No such file or directory
cat: /var/lib/acpi-support/bios-version:No such file or directory
* Saving VESA state... 

The last line means it can't find/save the video settings?

Ta

---

### Post by siabost on 2009-03-29
Even more info!

After booting into "recovery" and dropping into shell...

The output of > sudo lshw -C video is:
> *-display UNCLAIMED
  description: VGA compatible controller
  product: 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
  vendor: Silicon Integrated Systems [SiS]
  physical id: 0
  bus info: pci@0000:01:00.0
  version: 00
  width 32 bits
  clock: 66MHz
  capabilities: pm agp agp-3.0 vga_controller cap_list
  configuration: latency=0

Really need help on this. I don't need a great resolution just to be able to see the desktop!

Would ndiswrapper help if a windows driver is required?

Ta :(

---

### Post by siabost on 2009-03-30
Anybody...?

---

