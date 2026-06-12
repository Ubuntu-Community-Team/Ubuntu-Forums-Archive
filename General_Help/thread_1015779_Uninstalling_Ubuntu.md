---
title: "Uninstalling Ubuntu"
date: 2008-12-19
forum: General Help
---

### Post by perrti-y02 on 2008-12-19
First of all I would like to point out that I am not looking to uninstall my version of Ubuntu. I love it.

My sister is having problems with a Vista machine not connection to wireless, not recognising a dvd drive or a card reader. I want to try to convert her to Ubuntu because it is so much better.

If I install Ubuntu onto this machine on it's own partition with Grub on the Linux partition, will Windows still boot if the entire Linux partition is gone or will it revert back to it's normal habit?

Many Thnaks

Tim

---

### Post by hal8000 on 2008-12-19
If you dual boot Vista with Ubuntu, then it depends the bootloader that determines which OS will load, not the partition.

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

The link above is one of many found on google, if you install grub into the mbr then even if you delete the linux partition Vista will still load (as grub is installed to the mbr, not partition).

It may also be possible to let Vista control bootloading via bcdedit.exe although I wouldnt use any MS software for anything mission critical.
Hope that helps.

---

### Post by jay li on 2008-12-19
The answer is yes.

But I've got 2 questions for you perrti-y02:

1. What make you think all the issues you have in Vista has to do with Ubuntu?
It's 2 different systems which located on 2 different partitions.

2. If you want your sister using ubuntu, why do you care about windows?
I mean, that depends which partition you going to override.

---

### Post by caljohnsmith on 2008-12-19
> **hal8000 said:**
> 
The link above is one of many found on google, if you install grub into the mbr then even if you delete the linux partition Vista will still load (as grub is installed to the mbr, not partition).
It's true that Grub is installed in the MBR, but Grub consists of more than one stage; Grub is too big to fit in the MBR, because the MBR only allows a maximum of 446 bytes for the boot code; Grub has to load its "stage2" file in order for Grub to fully work. And because the stage2 file is in the linux partition, if you delete the linux partition at any point, Grub will not work, and consequently you won't be able to boot anything. :)

Perrti-y02, you could use the Vista boot loader to boot both Vista and Ubuntu; that way if anything happens to Ubuntu (including uninstalling it), Vista will continue to boot normally. If you want to do it that way, I would recommend using "[EasyBCD]("http://neosmart.net/dl.php?id=1")" to add Ubuntu to Vista's boot loader. You can find more info about how to do it here:

[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

Let us know how it goes. :)

---

### Post by Liviu-Theodor on 2008-12-19
Windows will keep its normal habbit no matter what you do. Today I was on a Vista machine and suddenly it restarted without asking anything, and I was in the middle of editing a document, because it installed some updates, even if the machine was configured not to look after updates! That kind of things shows us who is the control of Windows PCs (not the user, mind you).

So Windows will boot when dual-booting with linux, if this was its habbit, and no otherwise. And of course you should define the "normal habbit" of Vista, from your experience. From mine is: epic failure.

---

### Post by tsali on 2008-12-19
Use the WUBI executable installer on the install disk. Double click in Vista and follow the prompts.

This will allow you to "uninstall" Ubuntu just like any other Windows program if it doesn't suit her.

> Windows will keep its normal habbit no matter what you do. Today I was on a Vista machine and suddenly it restarted without asking anything, and I was in the middle of editing a document, because it installed some updates, even if the machine was configured not to look after updates! That kind of things shows us who is the control of Windows PCs (not the user, mind you).

So Windows will boot when dual-booting with linux, if this was its habbit, and no otherwise. And of course you should define the "normal habbit" of Vista, from your experience. From mine is: epic failure.

Liv, this is not correct. If you are struggling with getting Windows to behave properly (like you might with any OS), there are many here who can help you with those issues if you'd ask them to.

---

### Post by Liviu-Theodor on 2008-12-19
> **tsali said:**
> Liv, this is not correct. If you are struggling with getting Windows to behave properly (like you might with any OS), there are many here who can help you with those issues if you'd ask them to.

This is my poor experience with Vista (Basic, Premium and Ultimate, but I have not seen yet the Starter, Bussiness and Enterprise variants) (and in a smaller extent, but not big difference, with Windows ME). But I think I know something about Windows nonetheless, as I worked just fine with the following Windows versions: 3.1, 3.11 for Workgroups, 95, 95 OSR 2, 98, NT 4 Workstation, NT 4 Server, 2000, 2000 Advanced Server, XP (both Home and Pro). Vista Ultimate is just not compatible with what we have (both hardware and software). I mean, any other new OS works just fine with what we have (except Open Solaris, which did not recognized the sound and network cards).

And I am the network administrator here, and with the Fedora servers I had only a single problem. Vista I managed to make it work, but is still awful, and still does what it wants.

---

