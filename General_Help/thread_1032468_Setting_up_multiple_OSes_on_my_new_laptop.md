---
title: "Setting up multiple OSes on my new laptop"
date: 2009-01-06
forum: General Help
---

### Post by PlayWithFire on 2009-01-06
I just purchased an MSI Wind laptop, and i love it. I would like to use it as my experimentation machine, so I'd like to get a few OSes on there, like XP, Vista, Windows 7, OS X and of course Ubuntu. 

The biggest barrier for me right now, is the fact that the laptop doesn't have a DVD drive, so i have to boot from a USB thumbdrive. I already used UNetbootin to create an Ubuntu drive that i can boot to. I am a little lost on what to do next, but here's what i have in mind. 

I should boot into Ubuntu, and fire up the Partition Editor. Next, i should partition out my HD for each OS. Let's say it's something like this:
XP - 15GB - NTFS
Vista - 15GB - NTFS
Win 7 - 15GB - NTFS
OS X - 15GB - hsf+
Linux - 15GB - ext3
Linux Swap - ?? - ?? (not sure what these need to be)
Data - the rest - NTFS

I plan to use NTFS for data, because Linux and OS X can access these just fine, and XP will be my main OS for when i am actually doing work, and not screwing around. Is there any order these partitions should be in? 

So, for the next step: how do i actually get something bootable on a thumbdrive? Is it sufficent to just use [HPUSBFW]("http://www.hardwarecanucks.com/forum/guides-how-tos/1457-how-making-usb-thumbdrive-bootable.html") to make the drive bootable, and the extract the OS ISO on that drive? 

What is the best order to install all these OSes in? I'd like to use GRUB as the bootloader, because it seems like the most flexible one, but i am open to other suggestions.

---

### Post by snowpine on 2009-01-06
My advice is to learn about virtual machines (using virtualbox, vmware, etc) and experiment with different OS's that way. There is an entire Virtualization sub-forum here if you want to learn more. :)

To answer your specific question, Unetbootin is an excellent tool for creating a "Live CD" type of thumb drive from which you can install an OS. Generally speaking, it is easier to install Windows first and then Ubuntu. Good luck!

---

### Post by PlayWithFire on 2009-01-06
I do use VirtualBox quote a lot on my home PC, mainly to avoid gunking up my XP installation.
But on the laptop, i'd rather run the OSes natively.

---

### Post by HermanAB on 2009-01-06
Yup, multi-boot is totally 20th century.  You will do better with VMware or Virtualbox.  It is much nicer to run them all at the same time, rather than reboot whenever you find yourself in the wrong system.

Cheers,

Herman

---

### Post by PlayWithFire on 2009-01-06
How about the performance though? It's not a very powerful laptop, and i have a feeling it will be sluggish when emulating Vista.

---

