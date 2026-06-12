---
title: "custom kernel for snapdragon X elite"
date: 2024-07-27
forum: Development CD/DVD Image Testing
---

### Post by jos-dehaes on 2024-07-27
Hi

I want to create an ISO that can boot on the Lenovo Yoga Slim 7x (snapdragon X elite). I have a custom kernel and modules, and want to repack that so it can boot. How can I replace the kernel/modules ? I tried doing this manually using xorriso, it boots, but then it doesn't start the installer. I can't figure out how casper starts the installer, as the initrd only contains firmware and modules.

---

### Post by slovenskekasina on 2024-08-06
Install necessary tools like mkisofs, grub, and genisoimage, and compile the Custom Kernel

---

