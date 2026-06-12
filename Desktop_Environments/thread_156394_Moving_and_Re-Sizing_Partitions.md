---
title: "Moving and Re-Sizing Partitions"
date: 2006-04-06
forum: Desktop Environments
---

### Post by InExtremis on 2006-04-06
I have a question about moving and re-sizing ntfs partitions.

I used to have a wingle boot Windows system. I installed Kubuntu as a second OS, used GRUB in the MBR to manage the booting. Never really visited the Kubuntu install too often, but recently, my Windows install became corrupt and I decided to go full bore Linux ( Kubuntu obviously ).

Here's my layout:

[IMG]http://www.cfra.com/computes_show/images/qtparted.gif[/IMG]

My question is, is it possible to delete the ntfs partitions, and either absorb them into the existing linux one, or possibly mount them as different devices. Can I also move the current / partition to the front? Is that even possible without having to re-install everything?

Thanks!.

---

### Post by amohanty on 2006-04-07
Use QtParted (for Kubuntu) or GParted (Ubuntu) to blow away and reformat the windows partition

HTH
AM

---

