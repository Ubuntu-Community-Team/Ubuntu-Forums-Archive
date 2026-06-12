---
title: "Centos Boot Issue - Kernel panic - not syncing - Attempted to kill init!"
date: 2023-01-20
forum: Fedora/RedHat and derivatives
---

### Post by burtm05 on 2023-01-20
Hi Folks,
   I have a legacy Asterisk PBX system and the motherboard died on it today. I moved the drive to another host just to get it back up and running temporarily. During boot I am receiving "Kernel panic - not syncing - Attempted to kill init!".

  I created a boot-repair USB. The scans perform and then when it begins attempting to fix I get "Please enable a repository containing the [grub2] packages in the software sources..." and once I click OK it just quits.

 I am pretty desperate for some professional insight here, and yes, I know the version of CentOS I'm running is ancient. Here is a link to my PasteBin: [https://paste.ubuntu.com/p/H24nnWqy3g/](https://paste.ubuntu.com/p/H24nnWqy3g/)

---

### Post by oldfred on 2023-01-20
Moved to Other OS as CentOS release 5.2 using ext3 and kernel 2.6. 
Do not know CentOS, but very old kernel and grub.

It has been about over 10 years since grub became grub legacy & grub2 has been the standard BIOS boot loader.
And most systems now use grub2's UEFI boot version on gpt partitioned drives.

I know Ubuntu phases out old versions and the repositories are then not readily available. 
Found this:
[https://centosfaq.org/centos/centos-5-end-of-life/](https://centosfaq.org/centos/centos-5-end-of-life/)
March 1, 2017

---

