---
title: "designating/creating writethrough vmdk's for VirtualBox"
date: 2009-01-26
forum: General Help
---

### Post by parminides on 2009-01-26
Back in December I dabbled in setting up virtual machines. I don't remember exactly what I did at the time, but I definitely used some VMware product (Converter or something else) to create a vmdk disk image of the Vista partition on my laptop. I got it running reasonably well with VirtualBox on the Fedora partition of the same laptop.

Now I have an HP TouchSmart running Vista and Ubuntu. I would like to set up the Ubuntu partition to be able to run Vista. However, I haven't been able to get it to work. I've tried remaking the vmdk virtual disks using both Vista's (laptop and "desktop"), and I've tried copying the Vista vmdk files that work (i.e., the ones in Fedora) over to Ubuntu. Nothing works.

Here's the last thing I did and some observations:

I took the laptop Vista vmdk image files that Fedora uses and copied them over to Ubuntu. Didn't work. 

I noticed that in Fedora's VirtualBox, the main vmdk file is classified as a writethrough disk (which is supposed to be necessary for VirtualBox running vmdk's), but Ubuntu's VirtualBox classifies the same vmdk file as normal! Both Fedora and Ubuntu are running version 2.1.2 of VirtualBox.

I don't know how to get around this problem. Everything I've seen says that the vmdk image has to be writethrough for VirtualBox to use.

I've tried remaking virtual machines images for Vista from scratch (using VMware Converter) for both the TouchSmart and the laptop and neither works. Both attempts created disks get classified as normal in virtualbox.

Here's another strange thing: when Fedora runs VirtualBox (version 2.1.2) to create a disk/machine, it distinguishes between Vista and Vista (64 bit); Ubuntu running VirtualBox (version 2.1.2) only shows one option for Vista. In other words, there's no 64 bit choice.

---

