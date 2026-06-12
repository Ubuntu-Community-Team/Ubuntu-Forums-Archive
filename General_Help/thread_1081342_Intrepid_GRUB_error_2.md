---
title: "Intrepid GRUB error 2"
date: 2009-02-26
forum: General Help
---

### Post by wsonar on 2009-02-26
I'm getting an error 2 on boot from grub

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    40965749    20482843+   7  HPFS/NTFS
/dev/sda2        40966144    71686143    15360000    7  HPFS/NTFS
/dev/sda4        71698095   136761344    32531625    5  Extended
/dev/sda5        71698158    78172289     3237066   82  Linux swap / Solaris
/dev/sda6        78172353   136761344    29294496   83  Linux


Things work fine till I try to install GFXBOOT.

Curently I can only boot up using the super grub CD

I try going in and fixing grub

grub> root (hd0,5)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  15 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+15 p (hd0,5)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

grub> 


Everything looks good but when I reboot I still have the error 2


Anybody got a fix for this?

Thanks

---

### Post by wsonar on 2009-02-26
I've tried update-grub and completely removing grub and reinstalling grub



 worked fine before I tried gfxboot

---

### Post by makisupa123 on 2009-02-26
What version of gfxboot did you attempt to install?

I'm wondering if this has to do with the inode size.  When you attempted to reconfigure grub did you remove gfxboot?  Where did you re-do the grub setup from (live CD, local version of grub after booting to livecd, etc)?

--Mak

---

### Post by wsonar on 2009-02-26
I used a super grub cd I found and made

It lets me go through some steps then it actually brings me to my grub and 

I can choose any of the os's and go into them

I'm in my actuall install of ubuntu intredpid  kernal version  2.6.27-11 

when I run the grub setup




I had tried using grub-gfxboot_0.97-5_i386.deb

since then have uninstalled and reinstalled grub through synaptic package manager

as well as the terminal

I crashed my grub 3 times tring to get the gfxboot to work before I was able to reinstall grub the do the setup and it brought me back

now it dosen't work for some reason 

I've seen where people say error 2 on before the grub menu is related to some HD setting in the bios sometimes but it  was working before

GFXBOOT has not worked on intrepid

It did work on this same laptop on Gusty

---

### Post by wsonar on 2009-03-02
I got my gfxboot wroking

So I ended up just coping over the little data I had to the ntfs part this was a pretty fresh install of all os's it apears it was ext3 after all

I then booted to the ubuntu 8.04 cd deleted the linux and swap made the sawp 2 gig and the rest for the linux which was ext 3 and primary


after the install grub was back and booted into ubuntu 8.04

before getting any update

I followed the how to for the gfxboot here

[http://abhay-techzone.blogspot.com/2...on-ubuntu.html](http://abhay-techzone.blogspot.com/2...on-ubuntu.html)

rebooted and wolla I had my cool themed bootloader

I tested booting into each os

I then got all critical security updates

after testing was still good then got recomended updates

---

