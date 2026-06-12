---
title: "How to patch and update Ubuntu and install dependancies with no Internet Connection"
date: 2011-06-24
forum: Desktop Environments
---

### Post by Ted_Smith on 2011-06-24
I won't explain the reasons, but just the situation : 

I have a 64-bit computer at work that cannot be connected to the Internet with Ubuntu 11.04 64-bit installed on it. 

My home computer, that is connected to the Internet, is 32-bit running Ubuntu 10.04. Though I can obviously installed Virtual Machines on it of Ubuntu 11.04, they can only be 32-bit (and I have checked that my 32-bit processor will not allow any kind of 64-bit mode). 

I realise APT-ON-CD allows for packages installed on one archietecture to be carried over to another matching archietecture and OS version, but the deb packages on my 32-bit 10.04 Ubuntu Internet connected PC won't work properly on my 64-bit 11.04 Ubuntu system. 

Obviously in the world of Windows you can download an "Offline" version of service packs that include everything, even if your system doesn't need part of it, that updates your system to the latest SP. AFAIK, there is no such bundles for Ubuntu that I could download at home and bring into work on a disk to install on my work computer. 

So can anyone suggest any other way of me doing two things : 

a) Updating my non-Internet connected Ubuntu 64-bit system with the latest patches and
b) Download a number of other debian packages and their dependancies so that I don't have to go backwards and forwards between one computer and another everytime I try to install a deb package that then says "I need depdenacy X"

Thanks

Ted

---

### Post by Frogs Hair on 2011-06-24
These links may help.
[https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository)
[https://help.ubuntu.com/community/AptGet/Offline](https://help.ubuntu.com/community/AptGet/Offline)

---

