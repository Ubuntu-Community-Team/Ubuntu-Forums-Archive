---
title: "Wubi won't start"
date: 2009-03-08
forum: General Help
---

### Post by lingenfr on 2009-03-08
I installed Wubi/Ubuntu 8.10. I had it working for some time. I had followed instructions to make Ubuntu my default boot. That worked fine. Today, I went in and deleted the old kernel 2.6.27-7 and during the purge it asked me if I wanted to replace menu.lst with the package maintainers version and I made the mistake of saying yes. Now it won't boot at all. If I try to boot to Ubuntu or Windows via grub, I get Error 15: File not found. When I get to the GRLDR menu, there is no option for Windows, only Ubuntu. I booted with a live CD and mounted the partitions as per the wubi guide. I was hoping to restore my menu.lst, but I can't find it. What next?

**[SOLUTION]**

I booted with the live CD then opened terminal 
sudo mkdir /win
sudo mount /dev/sda1 /win
cd /win/ubuntu/disks/boot/grub
mv menu.lst sav.menu.lst
copy menu.lst.backup menu.lst

That restored my menu.lst to a working one. Then I used nano to edit menu.lst and removed the entries for the 2.6.27-7 kernel. Then it was time to fix the problem of no Windows option in GRLDR. For that, I did the following:

cd /win
mv boot.ini sav.boot.ini
mv boot.ini~ boot.ini

Then I rebooted into Windows and followed the instructions on the Wubi Guide [here]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20make%20Ubuntu%20the%20default%20boot%20option?").

---

