---
title: "Run Windows(dual boot partition) as Virtual Machine in Linux"
date: 2007-10-23
forum: Desktop Environments
---

### Post by Benjamin888 on 2007-10-23
I have my laptop setup with 2 partitions for Dual boot operation of Windows XP, and Ubuntu 7.10 Gutsy.

I am aware it is possible to run Virtual Machine software such as VMWare to work in an OS from another OS. 

But is there a away i can make Ubuntu load the Windows XP install that i have already installed on the other partition as a virtual machine within Ubuntu?

---

### Post by staticsage on 2007-10-23
I have done this before so I know it is possible.

I'm pretty sure this is the tutorial I used:
[http://www.venturecake.com/a-simple-guide-to-using-your-existing-windows-install-apps-in-ubuntu/](http://www.venturecake.com/a-simple-guide-to-using-your-existing-windows-install-apps-in-ubuntu/)

If you search around for "ubuntu vmware existing xp install" or something like that, you'll get lots of results. I think the writeup I linked to is the most userfriendly I've seen.

Let me know if you hit any roadblocks, and please post back with your results. :)

Edit:

Pay close attention to this:

> **But before we go further, a note: don&#8217;t start Linux inside the VM. If you do accidentally start Linux, turn the VM off immediately - otherwise your files may be eaten as Linux checks a running disk. Consider yourself warned.**

In other words, when your boot loader prompts you to choose your OS, don't choose Linux. If you have Linux as your default in grub (or whatever boot manager you use), make sure you choose boot the XP install.

---

