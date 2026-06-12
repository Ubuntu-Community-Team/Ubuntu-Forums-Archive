---
title: "undo dual-boot"
date: 2009-05-24
forum: General Help
---

### Post by brake16 on 2009-05-24
Good Morning

Well, I started my Ubuntu trip with the LiveCD and liked it enough to setup a dual-boot.  I used gparted to squeeze 15 GB out of my Vista machine, installed Ubuntu in the new section and started playing.  Fast forward 2 years, I now have 2 computers running Ubuntu, 1 computer running LinuxMCE (very cool, based on Kubuntu), and the original Vista/Ubuntu dual-boot.  I and the kids use the Ubuntu computers, my wife is staying with Vista (for now, we're still working on her!).  Since we really don't use the Ubuntu part of the dual-boot machine, I'd like to give her back that 15 GB (the harddrive is down to 70GB left).  So, now that you know I'm not a basher: how do I uninstall Ubuntu and give that part of the harddrive back to Vista?  It's probably also important to know that GRUB 1.5 is the bootloader.

Thanks
brake16

---

### Post by cariboo on 2009-05-24
Use the LiveCD to delete the ubuntu partitions. BOot from the LiveCD and once at the desktop go to System-->Administration-->Partition Editor and delete the ubuntu partitions. Use the Vista disk management tool to resize yoour Vista partition. If you have a Vista install cd you can boot from the cd and select repair from the menu, this should remove grub from the mbr. If you don't have a Vista install disk go [here]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") and download the correct version to repair the mbr.

---

### Post by raymondh on 2009-05-25
and ... here's a guide to fix the MBR of Vista for your reference

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

it'll be (at Vista's command prompt) 

bootrec.exe/FixMbr

Happy Ubuntu-ing.

---

