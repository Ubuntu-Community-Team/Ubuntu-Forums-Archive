---
title: "No video during Grub boot menu using KVM"
date: 2011-06-18
forum: Desktop Environments
---

### Post by Sherlok1948 on 2011-06-18
I am using a Belkin Switch2 KVM (F1DF102Uea) to connect two PCs: 

1. Dell Dimension 9150 (Intel P4), dual-boot using (A) Windows XP Pro/ 750GB disk and (B) Ubuntu 10.01 32bit on a seperate 160GB disk. This machine is connected to the KVM using the  longest KVM cable (Green). This is my main machine which I use with Windows and works perfectly through the KVM.

2. HP-Compaq DX2250  (AMD64*2), dual-boot using (A) Ubuntu Linux 64bit/ 1TB disk and (B) Windows XP on a seperate 160GB disk. This machine is connected to the KVM using the shorter cable (Yellow). This is a new machine (new to me - ex company machine via ebay) which came with windows XP on the 160GB disk. I bought a 1TB disk and installed Ubuntu 11.04 64 bit.

There is no video displayed during the Grub  boot menu phase from the DX2250 and the monitor displays ' Analogue  input, Cannot display this video mode'. Video is OK (later) from the  Ubuntu OS. The Grub boot menu displays OK if the monitor is connected  directly to the PC.

I have sent a question to Belkin support on this but wondered if anyone on this forum has come across this problem and can offer a simple fix. Thanks.

---

### Post by amauk on 2011-06-18
These switches are absolutely horrid
don't use them if you can help it

To properly detect a connected monitor and set the right resolution & refresh rate, there's a 2-way communication between machine and monitor
The machine asks the monitor what settings it supports, and the monitor responds

These switches that allow a monitor to be shared between multiple machines don't allow for this 2-way communication to happen, so the machine has no idea what settings the monitor supports

---

