---
title: "Invalid 64-bit installer on a real 64-bit CPU"
date: 2009-05-10
forum: General Help
---

### Post by LesterPalooza on 2009-05-10
To those who have used other distros besides Ubuntu:

I am new to the Linux  world and I am exploring the different distributions (Fedora, Mint, openSUSE). I have downloaded their x86_64 installers, hash-checked, and burnt on CDs on the lowest speed possible to avoid errors and hash-checked again on .iso from the newly burnt CD. I tried installing them but I didn't get far after the option "Boot" from the boot options of the Live CD. *For the sake of getting a screenshot*, I used Virtual Box OSE 2.14. This is the actual message I get when I boot with Live CDs of openSUSE, Mint, Fedora and Ubuntu 8.10 64-bit from turning on the PC. (Check screenshots attached at the bottom.)

I am running on AMD AthlonX2 64-bit, 3Gb RAM, 1.9Ghz, 250Gb HD, NVidia 8200M G, on a HP Compaq Presario CQ50.

Do you think this is an issue of outdated BIOS, or the linux kernel? Clearly I am running a 64-bit system but it tells me I cannot run 64-bit installers... Please advise. Thank you!

---

### Post by dcstar on 2009-05-11
> **LesterPalooza said:**
> 
..........
I am running on AMD AthlonX2 64-bit, 3Gb RAM, 1.9Ghz, 250Gb HD, NVidia 8200M G, on a HP Compaq Presario CQ50.

Do you think this is an issue of outdated BIOS, or the linux kernel? Clearly I am running a 64-bit system but it tells me I cannot run 64-bit installers... Please advise. Thank you!

Are you **100% sure** you have a 64-bit system, there are CQ50s that aren't:

[http://www.kokeytechnology.com/gadgets/laptops-notebooks/compaq-cq-50-139wm-notebooklaptop-price-features-and-specifications/](http://www.kokeytechnology.com/gadgets/laptops-notebooks/compaq-cq-50-139wm-notebooklaptop-price-features-and-specifications/)

---

### Post by LesterPalooza on 2009-05-11
Yes 100% sure. AMDAthlon X2 is 64-bit right? Sticker's on my laptop. And I am currently running 64-bit Ubuntu 9.04.

---

### Post by jespdj on 2009-05-11
Is your host operating system 32-bit or 64-bit? I'm not sure, but it might be required that your host OS is 64-bit if you want to run a 64-bit guest OS.

When you create a new virtual machine in VirtualBox, you have to choose if the guest OS is 64-bit or not (for example, you choose between "Linux" or "Linux (64-bit)"). Did you make the 64-bit choice there?

*edit* Looked in the VirtualBox help. Section 1.6 says that for 64-bit guests (1) you need a processor with hardware virtualization support (for AMD, that means your processor must support "AMD-V"), (2) hardware virtualization support must be enabled in the BIOS of your computer and in the virtual machine you are creating, (3) on a 32-bit host, running a 64-bit guest means extra overhead, but it is possible.

---

### Post by LesterPalooza on 2009-05-11
> **jespdj said:**
> Is your host operating system 32-bit or 64-bit? I'm not sure, but it might be required that your host OS is 64-bit if you want to run a 64-bit guest OS.

When you create a new virtual machine in VirtualBox, you have to choose if the guest OS is 64-bit or not (for example, you choose between "Linux" or "Linux (64-bit)"). Did you make the 64-bit choice there?

*edit* Looked in the VirtualBox help. Section 1.6 says that for 64-bit guests (1) you need a processor with hardware virtualization support (for AMD, that means your processor must support "AMD-V"), (2) hardware virtualization support must be enabled in the BIOS of your computer and in the virtual machine you are creating, (3) on a 32-bit host, running a 64-bit guest means extra overhead, but it is possible.

Great! I have AMD-V support. I just enabled Virtualization Support in BIOS and VBox works fine now. :) Thanks!

---

