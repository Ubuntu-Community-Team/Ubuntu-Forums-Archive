---
title: "Nomodeset was only the beginning!"
date: 2012-09-13
forum: Desktop Environments
---

### Post by BrianBlaze on 2012-09-13
Hey all I am having weird problems and so would like to see if anyone can help... I own a Gateway DX4850... A stupid purchase for sure but being one of the first towers I have ever bought I have learned a lot from it :) Sadly it has an Nvidia graphics card and so I believe originally I had tons of problems loading it up but once I added the nomodeset option it booted properly and everything is great, UNTIL I am ready to make my Ubuntu partition and instead of seeing 488 GB windows (NTFS) partition (my windoes 7) and my 443GB of unallocated space it just sees the whole TB drive... I don't want to get rid of windows but I am at a loss at how Ubuntu can't see anything... Is that because of nomodeset or what? I am so confused I have never had a problem installing all distros on any of my PC's but this one. If anyone has a clue let me know thanks! Also I am using the latest version of Ubuntu Desktop :)

---

### Post by Bashing-om on 2012-09-14
BrianBlaze ; Hi ! Welcome to the forum.

  Lets back up a bit and get a better foundation from which to work(confused me)

So to recap in my terms, You have a desktop that presently has windows installed, and you desire to dual boot with ubuntu ?

  If the above is correct (not installed ubuntu) ..you must first set aside space on the disk for ubuntu. This should only be done from the windows disk utility (prevents corrupting window's files, using window's tools).

  In your partitioning scheme bear in mind can only have a max of 4 partitions per disk.

To see what the present partitioning is from terminal within the ubuntu live cd run:
```
sudo fdisk -lu
```We will deal with making the "nomodeset" parameter permanent when you are installed. 

I hope this helps, as you require additional assistance, please ask.

---

### Post by 2F4U on 2012-09-14
> In your partitioning scheme bear in mind can only have a max of 4 partitions per disk.

This is certainly not true. While you can have only 4 primary partitions with the traditional MBR partitioning table, you can have additional extended partitions. Not to talk about GPT partitioning, where you can have 128 partitions.

---

### Post by BrianBlaze on 2012-09-14
Well I guess i didn't word it well so here it goes. I have windows installed on a ~440GB Partition and I have about the same ~440GB of unallocated space! If I do fdisk -l from ubuntu I only see /dev/sda with a full TB... I see no partitions or anything. When I tried to install Ubuntu it obviously says the same thing, It can't see the NTFS partition and just wants me to use the full TB drive for the install. I am using a custom install (meaning I am not doing some automatic one). I decided to try Fedora after having this problem and it worked... Fedora could detect my partitions including the unallocated space (which I saved for linux). I have never seen this problem before but I appreciate you guys giving input.I really feel like it is the fault of my tower... Gateway DX4850. Anywho thanks guys!

---

### Post by Bobhuber on 2012-09-14
> **BrianBlaze said:**
> Hey all I am having weird problems and so would like to see if anyone can help... I own a Gateway DX4850... A stupid purchase for sure but being one of the first towers I have ever bought I have learned a lot from it :) Sadly it has an Nvidia graphics card and so I believe originally I had tons of problems loading it up but once I added the nomodeset option it booted properly and everything is great, UNTIL I am ready to make my Ubuntu partition and instead of seeing 488 GB windows (NTFS) partition (my windoes 7) and my 443GB of unallocated space it just sees the whole TB drive... I don't want to get rid of windows but I am at a loss at how Ubuntu can't see anything... Is that because of nomodeset or what? I am so confused I have never had a problem installing all distros on any of my PC's but this one. If anyone has a clue let me know thanks! Also I am using the latest version of Ubuntu Desktop :)
Nomodset has nothing to do with your partitions. As posted you need to do everything from within windows should you decide to resize your windows partition to make room for Ubuntu before using the Ubuntu installer. A screenshot would help and be sure to backup anything important before doing anything.

---

### Post by BrianBlaze on 2012-09-14
> **Bobhuber said:**
> Nomodset has nothing to do with your partitions. As posted you need to do everything from within windows should you decide to resize your windows partition to make room for Ubuntu before using the Ubuntu installer. A screenshot would help and be sure to backup anything important before doing anything.

My goodness I will say it again... I have 440 GB partition and 440GB unallocated... I did that from windows... I get that it is not a nomodeset problem but I was just curious if anyone knows what the problem could be... Why would I need to resize my windows partition if I have 440GB of unalocated space?? And like I mentioned Fedora saw all the partitions properly and let me install it on the unallocated space lol The screenshot I would show you would just be Ubuntu's install wizard at the custom part where I choose my partitions and all it sees is /dev/sda with 1TB of free space... Please don't write that I need to fix my partitions from windows again... I clearly have my partitions mapped but ubuntu couldn't see them...

---

### Post by JKyleOKC on 2012-09-14
With your 1-TB drive, it's probable that your system uses UEFI rather than the older MBR-based boot process. If that's the case, fdisk -l does not work properly, nor do most of the common utilities dealing with boot time.

You can install Boot-Repair and run it to obtain a detailed report, without making any changes to your system. Here's a link to it: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

I had to do this to get a proper installation in a situation similar to yours. I don't know whether it applies in your case or not but it's worth taking a look. I think the package will run properly under Fedora, and in any case its author Yann is quite active on the forums here and eager to help...

EDIT: I had to install Boot-Repair initially in the Live CD since I was unable to get the HDD copy of Xubuntu working, and that worked perfectly. Thus there's no need to try to run it under Fedora at all. Just boot to the Live CD, then download and install Boot-Repair there and run it to create the bootinfo report automatically. The program will use pastebin to put your report onto the cloud so that you can share it here, and will give you the address so that you can view it. Save that address to a flash drive so that you can refer to it later, or post it in this thread...

---

### Post by Bucky Ball on 2012-09-14
@BrianBlaze: Please use punctuation (e.g. paragraphs) for clarity. Big blobs of text can be virtually unreadable and some won't bother trying. ;)

PS: You may have scripting turned off. That seemed to be another user's problem.

---

### Post by BrianBlaze on 2012-09-14
> **Bucky Ball said:**
> @BrianBlaze: Please use punctuation (e.g. paragraphs) for clarity. Big blobs of text can be virtually unreadable and some won't bother trying. ;)

PS: You may have scripting turned off. That seemed to be another user's problem.

I thought I was writing in paragraphs since each post is only a paragraph long 

lol

---

### Post by Bucky Ball on 2012-09-14
Yep, they're one paragraph, but this:

> **BrianBlaze said:**
> Hey all I am having weird problems and so would like to see if anyone can help... I own a Gateway DX4850... A stupid purchase for sure but being one of the first towers I have ever bought I have learned a lot from it :) Sadly it has an Nvidia graphics card and so I believe originally I had tons of problems loading it up but once I added the nomodeset option it booted properly and everything is great, UNTIL I am ready to make my Ubuntu partition and instead of seeing 488 GB windows (NTFS) partition (my windoes 7) and my 443GB of unallocated space it just sees the whole TB drive... I don't want to get rid of windows but I am at a loss at how Ubuntu can't see anything... Is that because of nomodeset or what? I am so confused I have never had a problem installing all distros on any of my PC's but this one. If anyone has a clue let me know thanks! Also I am using the latest version of Ubuntu Desktop :)

... is not easy to read and many won't bother. You will increase clarity and your chances of getting help by breaking it up a bit. ;)

Incidentally, don't think your problem has anything to do with nomodset. That is about graphics.

---

### Post by BrianBlaze on 2012-09-14
> **Bucky Ball said:**
> Yep, they're one paragraph, but this:



... is not easy to read and many won't bother. You will increase clarity and your chances of getting help by breaking it up a bit. ;)

Incidentally, don't think your problem has anything to do with nomodset. That is about graphics.

Sadly I am aware it is not the nomodeset... although I couldn't even boot without it. This is for sure a different strange problem but I will try [JKyleOKC]("http://ubuntuforums.org/member.php?u=374258") solution.

This is seriously the strangest problem...

Also I noticed that when I boot from a USB I have an EFI option and a regular option i.e when I start up and press F12 to choose which device I want to boot with it says:

EFI: Scandisk Ultra (USB)
Scandisk Ultra (USB)

If I choose the EFI one it won't work at all and if I choose the regular one I am forced to use nomodeset. I know this is probably not the partition problem but still these are things I have never had to deal with until I got this Gateway DX4850 :KS

---

### Post by JKyleOKC on 2012-09-14
Since you are getting that EFI option I'm almost certain that your problem has to do with the UEFI incompatibilities. While UEFI appears to be the coming thing, few if any Linux installation programs recognize it by default or treat it correctly. What makes this so bad is that so few folk who volunteer support via forums are even aware of the differences, and give you advice that can make the problems even worse.

The one person I've encountered who seems fully knowledgeable abour the situation is YannBuntu at [http://ubuntuforums.org/member.php?find=lastposter&t=2053371](http://ubuntuforums.org/member.php?find=lastposter&t=2053371) but OldFred at [http://ubuntuforums.org/member.php?find=lastposter&t=2051204](http://ubuntuforums.org/member.php?find=lastposter&t=2051204) runs him a close second...

---

### Post by oldfred on 2012-09-14
> OldFred at [http://ubuntuforums.org/member.php?f...ster&t=2051204]("http://ubuntuforums.org/member.php?find=lastposter&t=2051204") runs him a close second...

What!! oldfred is second. ;)

Yann's Boot-Repair actually fixes things or puts out a great report to use to analyze complex issues. oldfred just gives some advice, sometimes useful and has a list of links, sometimes useful. Often the best advice from oldfred is to use YannBuntu's Boot-Repair. :)

---

### Post by YannBuntu on 2012-09-14
Yann is just trying to gather the experience of everybody into "Boot-Repair", so that:
- Ubuntu users can fix their boot problems by themselves
- helpers don't need to repeat the same advice 100times/day ;)
- we detect and report GRUB/Ubiquity bugs

**@BrianBlaze:** don't install Ubuntu via the automatic installer as it would probably erase your Windows! 
please indicate your [Boot-Info]("https://help.ubuntu.com/community/Boot-Info") URL.

---

### Post by JKyleOKC on 2012-09-14
I sorta thought that my listing might bring both of you into the thread and get Brian some real expert help.

On a more general note, oldfred, I think we really need a prominent sticky in ABT, and possibly the Hardware forum as well, to point out the pitfalls of UEFI versus the traditional MBR setup. A month ago I had hardly heard of EFI, and had to become aware of it in a real hurry. Thanks to you and Yann for educating me; had I been a newcomer rather than a guy who used to disassemble DOS at its heart and wrote a couple of books about it, I would have been totally lost in this maze. But in the past couple of weeks this is the second such problem I've seen discussed here, and the number can only increase as more off-the-shelf systems come with EFI rather than MBR motherboards!

---

### Post by oldfred on 2012-09-14
Windows 8 pre-installs will only be UEFI and have the Security Bit set. So that will be even a larger issue. There is a sticky on that already.

[http://ubuntuforums.org/showthread.php?t=2056300](http://ubuntuforums.org/showthread.php?t=2056300)

While I do not have UEFI, I have been following it as I was going to build a new system this summer. Summer seems to have past, but it still is on my list. 

Yann has made some real improvements to Boot-Repair, in that it will repair a BIOS install of Ubuntu into a UEFI install. 

I have links to about 10 different threads/users who have successfully installed Ubuntu with UEFI in different configurations. We just about understand how to install UEFI ourselves, but the new security bit will greatly complicate even that. Many or even most users do not have any understanding of partitioning much less MBR(msdos) vs. gpt(GUID) partitioning schemes and then BIOS or UEFI where UEFI needs gpt.

---

