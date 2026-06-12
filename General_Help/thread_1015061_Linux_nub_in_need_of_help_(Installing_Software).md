---
title: "Linux nub in need of help (Installing Software)"
date: 2008-12-18
forum: General Help
---

### Post by Ltrra on 2008-12-18
I'm working on updating a machine that has NovellSUSE on it.  My goal is to get Kubuntu 8.10 on the machine.  In another forum I found out what i need to do in order to get the LiveCD to work for me, but now I've hit a new problem.

[https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)
Tells me to use gparted to partian my hard drive. Great! So I download Gparted from [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php) and burn the ISO to a dvd and pop it in the Linux.  Obviously I didn't know that this old version of SUSE doesn't have any form of auto run like newer OS's.  SO here is my question:

How do I install (or compile, which ever it may be) Gparted?  As the title states I am a nub of Linux, this is my third day working on Linux and its been a very fast paced learning experience, any help is more than welcomed!!!

---

### Post by oldos2er on 2008-12-18
You need to boot from the gparted cd (or dvd).

---

### Post by fiddler616 on 2008-12-18
> **Ltrra said:**
> I'm working on updating a machine that has NovellSUSE on it.  My goal is to get Kubuntu 8.10 on the machine.  In another forum I found out what i need to do in order to get the LiveCD to work for me, but now I've hit a new problem.

[https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)
Tells me to use gparted to partian my hard drive. Great! So I download Gparted from [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php) and burn the ISO to a dvd and pop it in the Linux.  Obviously I didn't know that this old version of SUSE doesn't have any form of auto run like newer OS's.  SO here is my question:

How do I install (or compile, which ever it may be) Gparted?  As the title states I am a nub of Linux, this is my third day working on Linux and its been a very fast paced learning experience, any help is more than welcomed!!!
If you want to get Kubuntu Intrepid on the machine, I would burn the *Kubuntu* Live CD, boot off that, and use the installer's built-in version of gparted to sort everything out. Doing gparted as a separate step seems like a mighty waste of time to me (since you *must* use it in a Kubuntu install).

---

### Post by Titan8990 on 2008-12-18
The Ubuntu live CD has Gparted on it. I have checked the Suse repositories recently and I noticed there wasn't a gparted there.

Keep in mind gparted is just a graphical front-end for parted, which you could always use.

Also, during the Ubuntu installation (either Live CD or alternate) you will have an opportunity to partition your HDD.

---

### Post by gsgleason on 2008-12-18
Do you want to replace your existing install of suse with ubuntu or do you want to dual-boot?

---

### Post by cariboo on 2008-12-18
There is a partitioner in the LiveCD so you don't need to partition the hard drive before installing. If you don't intend on keeping SUSE you can install right over the top of it, using the same partitions.

Jim

---

### Post by Ltrra on 2008-12-18
Oh sorry I left that part out. I am moving the files on the CD to its own partian because the BIOS doesn't have the option to load from CD/DVD.

---

### Post by tuxxy on 2008-12-18
Fiddlers correct just run it from the installation CD will be much quicker, select manual partitioning option at the partition stage of the installation.

---

### Post by Titan8990 on 2008-12-18
Ah! Just remembered the name of the Suse partitioner.

If you go to Menu -> Yast -> Advanced Partitioner


It is very similar to gparted.

---

### Post by fiddler616 on 2008-12-18
> **cariboo907 said:**
> There is a partitioner in the LiveCD
Yes, if for whatever reason you feel that you *must* run gparted by itself, boot off the very same Kubuntu disk(or partition, in this case) and select "Try Kubuntu" instead of "Install Kubuntu".
Then you can just run gparted off of that. Unmount everything first--including swap
```
sudo swapoff -a
```

If "Partition Editor" or "gparted" doesn't appear in your administration menu, just type
```
gparted
```
into a terminal.

Is this thread solved? It seems so to me.
If it isn't, then please provide a bit more information--your first post confused me a little bit.

---

### Post by Ltrra on 2008-12-18
> **Titan8990 said:**
> Ah! Just remembered the name of the Suse partitioner.

If you go to Menu -> Yast -> Advanced Partitioner


It is very similar to gparted.

You freaking rock

---

### Post by fiddler616 on 2008-12-18
> **Ltrra said:**
> Oh sorry I left that part out. I am moving the files on the CD to its own partian because the BIOS doesn't have the option to load from CD/DVD.
Having never done this myself....I'm not sure.
But it seems to me like just blindly copying and pasting wouldn't work...have you successfully done this yet? If so, let me know, I'll be *very* interested (saving the trouble of VirtualBox or buying CDs would be quite nice)(and my BIOS doesn't support USB bootups, although I gather there's a way to make it)

---

### Post by Ltrra on 2008-12-18
> **fiddler616 said:**
> Having never done this myself....I'm not sure.
But it seems to me like just blindly copying and pasting wouldn't work...have you successfully done this yet? If so, let me know, I'll be *very* interested (saving the trouble of VirtualBox or buying CDs would be quite nice)(and my BIOS doesn't support USB bootups, although I gather there's a way to make it)


Here is the guide

[https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)

I'm just starting it myself.

---

### Post by Ltrra on 2008-12-18
Well I can't get this to work.  Any suggestions as to how i can do this?  I need to put Kubuntu on a machine with no floppy and a BIOS that can't start from CD/DVD.  What do I do?

---

### Post by fiddler616 on 2008-12-18
> **Ltrra said:**
> Well I can't get this to work.  Any suggestions as to how i can do this?  I need to put Kubuntu on a machine with no floppy and a BIOS that can't start from CD/DVD.  What do I do?I've heard of booting off the hard drive, here:
[http://geekblog.oneandoneis2.org/index.php/2008/10/25/everything-is-and-should-be-a-file](http://geekblog.oneandoneis2.org/index.php/2008/10/25/everything-is-and-should-be-a-file)

If some kind soul could decipher:
>   So I mounted the ISO image via the loopback, copied the kernel and initrd files to the hard drive, created a grub entry capable of booting off the ISO *(root=iso:/dev/XXX:/path/to/lfslivecd.iso)* as per the LFS instructions, and **booted into the LFS LiveCD from the ISO image.**


---

