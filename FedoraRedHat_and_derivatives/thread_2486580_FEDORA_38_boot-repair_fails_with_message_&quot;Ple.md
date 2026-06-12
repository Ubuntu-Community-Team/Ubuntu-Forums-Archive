---
title: "FEDORA 38 boot-repair fails with message &quot;Please enable a repository...&quot;"
date: 2023-05-04
forum: Fedora/RedHat and derivatives
---

### Post by djspatule on 2023-05-04
Hi everyone, 

I broke my windows when I installed fedora 38 without understanding what i was doing and formatting the "*boot/efi*" partion. I repaired since with bcdboot on a windows install media but this broke my fedora install which I can't boot no more. There is no Grub at start-up...My computer is a quite recent DELL laptop with UEFI.

I tried using boot-repair but got the following message : "*Please enable a repository containing the [grub-efi] packages in the software sources of Fedora Linux 38 (Workstation Edition) (sda6). Then try again."*

My pastebin is : paste.ubuntu.com/p/2H3MPgnJ2Y

Any help is welcome.... thx in advance. Best, djspatule

 #yannubuntu #grub2 #fedora #boot-repair

---

### Post by TheFu on 2023-05-04
Exactly which release of Ubuntu are you running?

---

### Post by djspatule on 2023-05-04
I was running the boot-repair utility from a dedicated live boot repair USB drive. Not Ubuntu.

---

### Post by yancek on 2023-05-04
Lines 7-14 of your boot repair output show the EFI partition which only contain windows EFI files.  If you look at lines 82-94, you see the EFI entries in your BIOS which do not contain any Fedora entry.  Fedora is installed on sda6 but you do not have the boot loader installed properly, probably whatever you did to repair windows.  If this is a new install, it might be simpler to reinstall Fedora and make sure you boot and install in EFI mode and accept the defaults for bootloader installation.  That should create a directory on the EFI partition (sda1) for Fedora which will not affect the windows EFI files.  Do NOT create another EFI partition and do NOT format that partition.

Fedora has their own forums at the link below which are excellent for Fedora and would probably be a better source of information specific to Fedora.

[https://forums.fedoraforum.org/](https://forums.fedoraforum.org/)

Fedora has a site which explains how to reinstall Grub EFI files referred to in your post at the link below.

[https://docs.fedoraproject.org/en-US/quick-docs/bootloading-with-grub2/](https://docs.fedoraproject.org/en-US/quick-docs/bootloading-with-grub2/)

---

### Post by coffeecat on 2023-05-04
*Thread moved to **Fedora/RedHat and derivatives** sub-forum.*

As yancek says, the fedoraforum would be a better place for you to post your question. This sub-forum is here as a convenience for forum members who are predominately Ubuntu (and official Ubuntu flavours) users.  This is not the best place if your main OS is Fedora.

---

### Post by djspatule on 2023-05-05
Hi, thanks for the help. 

I tried to post on "fedoraprojects.org" without success...login is hell (or I'm the worst) so I posted here: [https://www.reddit.com/r/Fedora/comments/138efxt/fedora_38_bootrepair_fails_with_message_please/](https://www.reddit.com/r/Fedora/comments/138efxt/fedora_38_bootrepair_fails_with_message_please/)

I tried to reinstall Fedora but I have been using Ubuntu for a while and got lost in translation when moving towards Fedora regarding the particularity of the partitionning tool at install.... And when I try to reinstall, the tool tells me that I don't have enough space on disk...And I feel Blivet intimidating and don't want to risk breaking my windows boot again....

Anyway, thanks again

---

### Post by yancek on 2023-05-05
Read through the article at the fedoraproject link.  There is no reason to log in.  If you want to post, use the first link in my post above to the fedoraforums.  To use the commands at the fedoraprojects link, you will need a Fedora install USB as the commands won't work from Ubuntu.  If you get a message that you don't have enough disk, it is likely you are installing to another partition rather than over the partition on which you currently have Fedora.  I don't use Fedora myself but, my understanding is that the default is to use a separate /boot partition with LVM as well as an EFI partition.  If you are not familiar with LVM, you might select a different option.   

If you look at your original boot repair lines 129-138, you will see that your partitions take up about 476GB of a 477GB drive so you need to write over the Fedora partitions, sda6 and sda7.  You could either install over sda6 and sda7 or start over by deleting sda6 and sda7 which would leave 70GB of unallocated space on which to install Fedora.  You have to boot the Fedora from the BIOS using the UEFI boot option and install UEFI.  

The link below has pretty detailed instructions on installing Fedora.  You can skip the steps for creating unallocated space and creating the USB.

[https://itsfoss.com/dual-boot-fedora-windows/](https://itsfoss.com/dual-boot-fedora-windows/)

---

### Post by BBQdave on 2023-05-06
> **yancek said:**
> Fedora has their own forums at the link below which are excellent for Fedora and would probably be a better source of information specific to Fedora.

[https://forums.fedoraforum.org/](https://forums.fedoraforum.org/)

And to further clarify, FedoraForum is users. There are no devs or official Fedora Project leaders on FedoraForum. It was set up long ago by a group of users who continue to help (as they can) with Fedora Linux questions, but is not the official forum of Fedora Linux.

The official forum is [https://discussion.fedoraproject.org/](https://discussion.fedoraproject.org/) [B]Fedora Discussion
[/B]
@djspatule  I understand what you are saying about Fedora Discussion (fedoraproject.org) I too find it confusing and difficult to navigate and have a discussion. I like and use FedoraForum for all my Fedora Linux needs :)

---

