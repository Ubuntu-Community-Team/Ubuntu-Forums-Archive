---
title: "ReactOS in KVM"
date: 2010-03-24
forum: Desktop Environments
---

### Post by jdpipe on 2010-03-24
Hi all

Can anyone give me an update on whether it's possible to quickly launch the ReactOS KVM images (from reactos.org) such that ReactOS runs on Ubuntu with network support?

I have been able to run ReactOS and have a network card detected but I don't know how to bridge the network connection or whatever, such that this virtual machine has access to the network.

kvm -hda ReactOS-0.3.11-QEMU/files/ReactOS.vmdk -net nic,model=ne2k_pci 

Cheers
JP

---

