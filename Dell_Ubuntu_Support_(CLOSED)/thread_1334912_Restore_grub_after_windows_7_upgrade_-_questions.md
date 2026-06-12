---
title: "Restore grub after windows 7 upgrade - questions"
date: 2009-11-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by EvansFive on 2009-11-22
I had Ubuntu 9.10 and Vista dual booted via GRUB (NOT GRUB2...too many bugs!)

I have just upgraded Vista to Windows 7 and as expected GRUB is no longer displaying.

From what I can find from various posts I need to do the following:
1) Boot Ubuntu 9.10 live CD
2) sudo grub
3) find /boot/grub/stage1 or find /grub/stage1
4) root (x,y) - using result from step 3
5) setup (x) - using result from step 3
6) quit

BUT...Ubuntu 9.10 live CD has GRUB2!

Will I not also need to do:

sudo apt-get install grub

BEFORE I do the steps above.

Will this result in any conflicts that could cause be great grief...I just want to get the dual boot thing working again!

Any advice/assistance would be gratefully received thanks!

LASTLY, do I need to change anything in my MENU.LST to boot Windows 7 instead of VISTA!

Thanks

---

### Post by oldfred on 2009-11-23
This link has instructions. I have not tried and grub2 works fine for me. I think the instructions assume you are already in your Ubuntu install but one of the comments had a link to using an old liveCD to install.

HowTo: Revert from grub2 to Legacy Grub. 
[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

---

### Post by EvansFive on 2009-11-23
Thanks for the suggestion, but don't have a running Ubuntu thanks to the Windows 7 install.

What if I used a 9.04 live cd to do the repair of GRUB for a 9.10 Ubuntu will that work?

Or is there a better way to fix my problem?

---

### Post by fancypiper on 2009-11-23
I believe so. Boot with it and try this:

# Re-install grub
sudo bash # DANGEROUS! ENTER COMMANDS EXACTLY!
mount /dev/sdb2 /mnt #<--Change to your root partition
mount /dev/sdb1 /mnt/boot #<--If you have a /boot partition
mount -o bind /proc /mnt/proc
mount -o bind /dev /mnt/dev
chroot /mnt bash
update-grub
grub-install /dev/sda #<--Change to your hard drive
exit
exit

---

### Post by EvansFive on 2009-11-23
I am wondering if it is better to do a fresh install of Ubuntu 9.10 and get GRUB2 installed.

That way I can get ext4 partitions as well!

Are there any compatibility issues re GRUB2 and WINDOWS 7?

Thanks

---

### Post by EvansFive on 2009-11-23
Well I decided to give it a go before doing a complete reinstall.

1) Booted from 9.10 live CD
2) sudo mount /dev/sdb4 /mnt
3) sudo mount /dev/sda6 /mnt/boot
4) sudo grub-install --root-directory=/mnt/ /dev/sda
5) reboot

This worked and I ended up with my contents of menu.lst.

I then did sudo apt-get install grub-pc and it built a new grub.cfg with recently installed kernel and Windows 7 even appeared.

Booting either Ubuntu or Windows 7 works ok!

So big sigh of relief!

Thanks for the assistance.:D

---

### Post by Rasheeke on 2009-11-29
I'm still having issues, I think it's because I have multiple hard drives.  After installing windows 7 it goes straight to windows without touching grub even after following these steps and getting a completion without error message.  

Is this an MBR problem?

---

### Post by oldfred on 2009-11-29
Rasheeke, you would do better to post in a new thread with your exact problem. Did you install grub to the wrong drive? Quick test is to try to  boot from the second drive.

---

