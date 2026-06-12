---
title: "multi booting?"
date: 2008-12-30
forum: General Help
---

### Post by mtandrews on 2008-12-30
Hello everyone.  I just downloaded and burned ubuntu 8.1 and I'm going to give it a world.  I have used linux before (mandrake) some years ago at a place of employment but I downloaded this for my personal computer.  I've already burned it to a CD. The question I have is my machine has 2 hard drives which is set up dual boot with Windows XP Home on C:drive and XP Pro on D:drive. My plan is to partition C: and give the bulk of it to Ubuntu. Is this even possible and if so will my computer still allow me to boot to which OS I want to use.  Thanks in advance...

M.T. Andrews
San Antonio, Texas

---

### Post by dcstar on 2008-12-30
> **mtandrews said:**
> Hello everyone.  I just downloaded and burned ubuntu 8.1 and I'm going to give it a world.  I have used linux before (mandrake) some years ago at a place of employment but I downloaded this for my personal computer.  I've already burned it to a CD. The question I have is my machine has 2 hard drives which is set up dual boot with Windows XP Home on C:drive and XP Pro on D:drive. My plan is to partition C: and give the bulk of it to Ubuntu. Is this even possible and if so will my computer still allow me to boot to which OS I want to use.  Thanks in advance...

M.T. Andrews
San Antonio, Texas

It should all happen automagically as part of the Ubuntu installation process and give you exactly what you have outlined.

---

### Post by ajmorris on 2008-12-30
hi there,
yes, this is indeed possible, and the favoured way of dual booting windows and linux for most people. You can use a partitioner like 'gparted' to resize your windows partition and make room for ubuntu. You can either download the gparted live cd (or use it from another linux cd) and resize it, or do it during the process of the ubuntu installer - just make sure you choose manual/guided partitions if you do it via the ubuntu installer.


AJ

---

### Post by ajmorris on 2008-12-30
> **dcstar said:**
> It should all happen automagically as part of the Ubuntu installation process and give you exactly what you have outlined.

oh, the ubuntu installer does that now? nice.

---

### Post by thomas228 on 2008-12-30
> **mtandrews said:**
> Hello everyone.  I just downloaded and burned ubuntu 8.1 and I'm going to give it a world.  I have used linux before (mandrake) some years ago at a place of employment but I downloaded this for my personal computer.  I've already burned it to a CD. The question I have is my machine has 2 hard drives which is set up dual boot with Windows XP Home on C:drive and XP Pro on D:drive. My plan is to partition C: and give the bulk of it to Ubuntu. Is this even possible and if so will my computer still allow me to boot to which OS I want to use.  Thanks in advance...

M.T. Andrews
San Antonio, Texas

Hi

What you propose doing with your C drive will allow to to install ubuntu on C and will probably create a grub on the C drive's mbr. edit: recommend you use windows xp to partition C to make room for ubuntu installation.  Check XP is working after partitioning and before installing ubuntu.  It will make troubleshooting (if required) easier later. end of edit

A question or two before you proceed 

1 How is your present system dual booted? Do you use your bios option to select C or D boot?

2 When you multi boot (After ubuntu install) do you expect to do it in the grub?  most logical way but might involve editing ubuntu menu.lst 

3 Consider using ubuntu 8.04 as it is long term vs 8.10's 6 month.

There are many great members out there on this forum that will bend over backwards to help you solve any of your OS problems

They helped me with my thumb installed ubuntu 8.04 and the triple boot I ended up with See [http://ubuntuforums.org/showthread.php?t=1021772](http://ubuntuforums.org/showthread.php?t=1021772)

Good luck

Tom

---

### Post by ajmorris on 2008-12-31
> **thomas228 said:**
> Hi

What you propose doing with your C drive will allow to to install ubuntu on C and will probably create a grub on the C drive's mbr. edit: recommend you use windows xp to partition C to make room for ubuntu installation.  Check XP is working after partitioning and before installing ubuntu.  It will make troubleshooting (if required) easier later. end of edit

A question or two before you proceed 

1 How is your present system dual booted? Do you use your bios option to select C or D boot?

2 When you multi boot (After ubuntu install) do you expect to do it in the grub?  most logical way but might involve editing ubuntu menu.lst 

3 Consider using ubuntu 8.04 as it is long term vs 8.10's 6 month.

There are many great members out there on this forum that will bend over backwards to help you solve any of your OS problems

They helped me with my thumb installed ubuntu 8.04 and the triple boot I ended up with See [http://ubuntuforums.org/showthread.php?t=1021772](http://ubuntuforums.org/showthread.php?t=1021772)

Good luck

Tom

XP's partitioner cannot partition the windows partition if it is active. Also, it is recommended to defragment an NTFS partition before resising it.

> What you propose doing with your C drive will allow to to install ubuntu on C and will probably create a grub on the C drive's mbr.
ermm, no? The OP wants to resize his windows partition, to make another partition for ubuntu. You cannot run windows and linux on the same partition simultaneously, without the use of a tool like WUBI. And it will not "probably create a grub on the C drive's mbr" as ubuntu will not be installed on the same partition as windows. It will be installed to either the boot records on the ubuntu partition, or the MBR.


AJ

---

### Post by thomas228 on 2008-12-31
> **ajmorris said:**
> XP's partitioner cannot partition the windows partition if it is active. Also, it is recommended to defragment an NTFS partition before resising it.


ermm, no? The OP wants to resize his windows partition, to make another partition for ubuntu. You cannot run windows and linux on the same partition simultaneously, without the use of a tool like WUBI. And it will not "probably create a grub on the C drive's mbr" as ubuntu will not be installed on the same partition as windows. It will be installed to either the boot records on the ubuntu partition, or the MBR.


AJ


Hi 
Thank you for clearifying my terminoligy The OP has 2 hard disks so that means he can use XP pro from the second hard disk to partition the first hard disk. He can then check his first disk for an operating XP. You are right in recomendig that he defragment his first hard drive before he tries to partition it.

His drive letters will probably change but his physical disks will still be the same and his 2 XP's will still reside on their respective disks. It would probably be wiser for the grub to reside on ubuntu's partition although I'm not smart enough to accomplish that.
Further I don't know how the OP is booting into his choice of XP's at present and even though it may be easy to edit ubuntu's menu.lst to correct for any problems it is always a good idea to make sure existing OS's work before adding new ones. ie after he partitions his first drive make sure that drive's XP still works before he installs ubuntu on that drive's new partition

Good luck

Tom

Again thanks for your imput
Tom

---

### Post by ajmorris on 2008-12-31
> **thomas228 said:**
> Hi 
Thank you for clearifying my terminoligy The OP has 2 hard disks so that means he can use XP pro from the second hard disk to partition the first hard disk. He can then check his first disk for an operating XP. You are right in recomendig that he defragment his first hard drive before he tries to partition it.

His drive letters will probably change but his physical disks will still be the same and his 2 XP's will still reside on their respective disks. It would probably be wiser for the grub to reside on ubuntu's partition although I'm not smart enough to accomplish that.
Further I don't know how the OP is booting into his choice of XP's at present and even though it may be easy to edit ubuntu's menu.lst to correct for any problems it is always a good idea to make sure existing OS's work before adding new ones. ie after he partitions his first drive make sure that drive's XP still works before he installs ubuntu on that drive's new partition

Good luck

Tom

Again thanks for your imput
Tom

haha, missed the 2 HD part...
Yes, the drive letters within windows will stay the same, however the UUIDs will change, but windows doesnt use the UUIDs so it doesnt matter. It doesnt really matter if grub is installed to the first sectors of the ubuntu partition, or to the mbr, it is up to preference, but both can be chosen, and easily accomplished via the ubuntu installer.

AJ

---

### Post by swiftwood on 2008-12-31
I just did this on my HP Windows XP laptop.

So far so good, it goes back and forth w/o any issues.

Just make sure you shutdown windows properly, otherwise it will ask you to boot back up into it to close out hardware.

---

### Post by jnw222 on 2008-12-31
that is the purpose of the of "guided partitioning" on the installer

not to mention grub allows you to set the default os booted (such as automaticly booting windows after the timeout)





or you can use Wubi

---

### Post by thomas228 on 2008-12-31
> **ajmorris said:**
> haha, missed the 2 HD part...
Yes, the drive letters within windows will stay the same, however the UUIDs will change, but windows doesnt use the UUIDs so it doesnt matter. It doesnt really matter if grub is installed to the first sectors of the ubuntu partition, or to the mbr, it is up to preference, but both can be chosen, and easily accomplished via the ubuntu installer.

AJ

Hi again

The OP has 2 versions of windows XP each on their own disk. Will the ubuntu installer put both versions (as choices) in the grub with the ubuntu choice.? If so the OP will have a choice of ubuntu, XP, or XP pro.  

I still don't know how the OP boots into his choice of XP or XP pro with his present setup and that might affect a clean ubuntu grub for his new 3 OS choices.

edit: It probably doesn't matter much as editing the menu.lst allows you many choices on system setup and  as I stated earlier there are some great forum members more than capable of straightening out grub and menu.lst problems. end of edit
 
Food for thought

Tom

---

### Post by ajmorris on 2009-01-01
> **thomas228 said:**
> Hi again

The OP has 2 versions of windows XP each on their own disk. Will the ubuntu installer put both versions (as choices) in the grub with the ubuntu choice.? If so the OP will have a choice of ubuntu, XP, or XP pro.  
Yes, the installation of grub via the ubuntu install, should pick up both versions of XP, and add them to the grub menu.lst.

> **thomas228 said:**
> 
I still don't know how the OP boots into his choice of XP or XP pro with his present setup and that might affect a clean ubuntu grub for his new 3 OS choices.
I'm assuming he is using the default Windows XP method, and just using the Windows XP boot loader. He will have the choice of all versions of XP within it, if this *is* the case, the installation of grub into the mbr over the top of it, shouldnt do anything detremental, and the OP should not experience any issues.

> **thomas228 said:**
> edit: It probably doesn't matter much as editing the menu.lst allows you many choices on system setup and  as I stated earlier there are some great forum members more than capable of straightening out grub and menu.lst problems. end of edit
 
Yep, menu.lst is very easy to debug and sort out.


AJ

---

