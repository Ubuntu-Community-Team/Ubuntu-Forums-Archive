---
title: "I have a GRUB issue."
date: 2009-03-11
forum: General Help
---

### Post by BightningLug on 2009-03-11
I have a bit of an issue and I'm not sure how to proceed. I have 2 harddrives in my system. One is the original WinXP C: drive. The other was a 60GB drive I had left over from a Win2k computer. I formatted the 60GB drive and installed Ubuntu on it. I used GRUB set up a dual-boot system. I haven't had to use the Windows XP option at boot-up for 18 months. However, the 60GB drive, being much older than the computer, becomes damaged. I can clearly hear something hitting one of the discs in the harddrive. Then the system hangs. 

My problem is that I am going to replace the 60GB drive with a 250GB drive and need to know if GRUB is going to have a problem when I remove the drive that Ubuntu is installed on?

I plan to make a new Ubuntu live cd and install it on the new 250GB drive. Will GRUB have a problem with that?

Can GRUB be removed?

and Where is GRUB installed?

---

### Post by Jubward on 2009-03-11
I think grub is placed on the one before it right? If so then replacing the 60gb shouldn't give you any problems.

But lets wait for someone else to reply before you try anything. :mrgreen:

---

### Post by MaxIBoy on 2009-03-11
Grub can install to a number of places, but the default option is to install it to the MBR of whatever the default booting hard drive is. If it got installed to the MBR of the 60-gig hard drive that you plan to remove, then that could be a problem, but if you remove the hard drive and it breaks, all you have to do is boot from an Ubuntu CD and follow the instructions to setup GRUB that I helped this other guy with:
[http://ubuntuforums.org/showthread.php?t=1092975](http://ubuntuforums.org/showthread.php?t=1092975)


By the way, fixing that hard drive issue could be as easy as tightening some mounting screws. Try before you buy!;)

---

### Post by jelle_ on 2009-03-11
i dont think grub will cause probems. you will install ubuntu and grub on a new hard drive. you just have to be sure that the new hard drive is the first one you boot.

---

### Post by BightningLug on 2009-03-11
If I understand correctly, I should be able to replace the drive and boot up with a new Ubuntu CD and install Ubuntu on the new drive, and doing so will overwrite previous GRUB settings with new ones.

Or will something else happen?

---

### Post by 3l3vans on 2009-03-11
i am by no means an expert but 

1. ubuntu is pretty good about installing grub correctly right off the bat in almost any situation

2.your grub file is completely modifiable after its installed the file you want to locate is /boot/grub/menu.lst. find that file and open it with a text editor. if you take a good look at it you can see how it works, it basically just lists the operating systems on your computer and where they are located. if you screw it up and your computer won't boot just use a live CD distro (i use Dyne:Bolic 2 because the live cd logs you in as root automatically) and go in and fix the file from the live cd.

---

### Post by ntatealan on 2009-03-22
I want to change the default option for the Grub loader to 'Vista', so I followed your advice and modified the menu.1st file to 'savedefault   0' for the vista option. When i tried to save the file the message was 'You cannot save. . . You do not have the necessary permissions to save the file.' When i installed I gave only one name and one password, so who *has* the necessary permision??

---

