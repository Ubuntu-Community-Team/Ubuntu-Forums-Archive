---
title: "vmware with previous xp installation?"
date: 2006-12-25
forum: Desktop Environments
---

### Post by platinummonkey on 2006-12-25
Howdy! 

I am dual booting my laptop, a toshiba blah blah blah... :p  anywho there are a few apps that i really use on windows and until ive fully migrated away from windows, i still need to be able to use these programs, such as autocad, etc (I'm learning similar linux programs to replace the windows ones, but it will take some time to become efficient in them).

Now here is my problem, now from what ive found on the forums so far has all been installations of vmware that require me to install windows after vmware, but i already have xp installed on a separate 15 gb ntfs partition...:-k  I know there has to be a way to do this, but i dont want to try something and really mess something up :P
I only have one hardrive on this laptop; there are also 3 separate partitions, one 9gb ext3 for the linux installation some swap and my /home  which is also ext3 and I use fs-driver for windows to use the /home as a shared between windows and linux.

Thanks for any and all help! :-D

---

### Post by PilotJLR on 2006-12-25
I think there is some confusion here over the ESX and Server products. ESX is the enterprise-grade bare metal hypervisor, which sits directly on hardware... so ESX requires guest OS's to be installed after ESX.

What you'll want (and what is also free!) is VMware Server, which is an application that relies on a host OS.
Server will run as an app on your existing linux or windows installation.

If your question is instead regarding using your existing physical Windows system as a virtual machine... yes, that is possible, but not free. the P2V Assistant will convert a physical OS to a guest.

---

