---
title: "Squeeze install on ancient machine"
date: 2014-12-19
forum: Debian
---

### Post by jwbrase on 2014-12-19
I have an ancient (1995 vintage) Pentium I machine with DOS and Windows 95 (for retrogaming) multibooted alongside Linux. The Linux distribution in use had been D*mn Small Linux, but that has only a v2.4 kernel, and because I switch between OS's on the machine fairly often and the BIOS is absolutely glacial about posting, I'd like to be able to use kexec to cut the BIOS out of the loop. Kexec, however, is only available on 2.6 or later kernels. The problem has been finding a distribution that both has a 2.6 kernel and will fit in RAM on the machine in question (40 MiB). 

I had been experimenting around with SliTaz, and had run across some roadblock (this was a while ago, so I don't recall exact details), when someone on the SliTaz IRC suggested that Debian itself will run in 40 MiB, but that its installer won't. So I yanked the hard drive, installed Debian Sqeeze on another machine, then moved it back to the target machine. The default kernel for Squeeze, however, gives up waiting for the root filesystem and drops me to an initramfs prompt. Some Googling revealed that the issue is likely related to missing drivers for old PATA controllers in the squeeze kernel, then I got a new job and didn't have any time to mess with the machine for quite a while.

I came back to the issue recently and put the drive back in the machine I had installed Debian from, compiled a custom kernel with all the non-manufacturer-specific IDE/PATA drivers I could find compiled in, installed the new kernel, and tried moving the drive back to the target machine. I now get some new errors with the new kernel (for instance "hda: drive not ready for command"), but still end up timing out on the root filesystem and getting dumped to an initramfs prompt.

So, I have a few questions:

[LIST]
[*]Can anybody suggest kernel configuration settings or kernel command line options that might  help? I've attached the .config for my current kernel configuration.
[*]Would I have better luck with legacy hardware support with a previous version of Debian, or the same version with a downgraded kernel?
[*]Alternatively, can anyone mention a better distribution for this machine? Requirements are 2.6 kernel, ability to fit in 40 MiB of RAM (I do have a swap partition, so this isn't a hard limit, but the working set needs to be small enough that the machine doesn't spend all its time thrashing swap), and a lightweight X environment. Preferably the installer should also run in 40 MiB, but that's at least somewhat negotiable.
[/LIST]


[ATTACH]258677[/ATTACH]

---

### Post by sudodus on 2014-12-19
40 MiB of RAM is by far too small for the current linux distros. And the hardware is very old. I think DSL, that you have already, might be the best alternative. You can try ***Tiny Core***, which might work. And you can try ***Kolibri***, which is really small (nice to play with, but cannot do much). Please post back and tell us how it works.

---

### Post by jwbrase on 2014-12-19
> **sudodus said:**
> 40 MiB of RAM is by far too small for the current linux distros.

RAM is not my issue in this case, and I'm fairly confident the Debian install I've set up is slim enough to run in 40 MB.

> And the hardware is very old. I think DSL, that you have already, might be the best alternative.

DSL doesn't have the kernel I'm looking for.

> You can try ***Tiny Core***, which might work.

I had previously looked at Tiny Core and thought it wasn't quite what I was looking for. I forget why I discounted it, so I may take another look.

> And you can try ***Kolibri***, which is really small (nice to play with, but cannot do much). 

:-\

Kolibri is a homebrew OS. It is not a Linux distribution. Recall that one of the things I'm looking for is Linux 2.6+. Tiny Core qualifies (at least on kernel version and possibly on RAM), but Kolibri does not at all.

One thing that is preferable in whatever distribution I end up using is that it be more focused on being installed as a hard disk OS than on being used as a live CD. There are a few Live-CD distributions that would probably fit my memory budget if they could be installed to hard disk without firing up the full live CD environment, but load the entire CD contents into a ramdisk at boot, thus requiring much more RAM than the software on them actually requires.

---

### Post by sudodus on 2014-12-20
The following link shows what is possible with a very small system based on Debian.

[https://help.ubuntu.com/community/9w/RAM_%26_disk_usage](https://help.ubuntu.com/community/9w/RAM_%26_disk_usage)

If you create a basic Debian installation that boots into a text screen, it will be small enough. Then you can add a small window manager, for example fluxbox or jwm or openbox, and add the eye-candy you like (and you can squeeze into the available RAM. Maybe the concept of 9w would work for you, or the concept behind it, that you make your own re-spin based on Debian. I think you can make it smaller based on Debian than based on Ubuntu.

---

### Post by jwbrase on 2014-12-21
Can anyone offer any insight on the IDE driver issue?

---

### Post by sudodus on 2014-12-21
I can use modern operating systems with my old IBM Thinkpad T42 and some old desktop computers, that have IDE (PATA) HDDs. I have not had any problems because of IDE instead of SATA drives. But those computers are made during this milennium ;-)

---

### Post by jwbrase on 2014-12-21
Yeah, that's just the thing: The drive works just fine on the machine I used to run the installer with the stock squeeze kernel. The same drive fails with the same stock squeeze kernel on the target machine.

---

### Post by jwbrase on 2014-12-28
I tried moving back from Squeeze to Etch, and it seems to be working. The installer is crawling along, since it's using about 60 MiB RAM on a 40 MiB machine, but that's to be expected. It does have a 2.6 kernel, so I think I'll be good as far as kexec is concerned.

---

