---
title: "Duel Booting Windows XP and Ubantu 6.06"
date: 2006-06-08
forum: Desktop Environments
---

### Post by Harley51 on 2006-06-08
Has anyone tried this with Ubuntu 6.06. I tried with all other Linux Distos. Before I try Ubantu I would like to know if there is going to be a problem. Here's my instructions that work for Red Hat,Fedora, Centos.

			
			Centos 4.3 Install

This by all means may not work for everybody.			

I run an Intel D865perl motherboard with 2.6 gig Intel processor with 1 gig of ram. Two 250 gig 			
hard drives. The first hard drive is for Windows XP. Second hard drive is for Fedora and data			
backups.			

Drive 2 the first 40 gig is Fedora and the second 210 gig is for files backups and Norton ghost 2003			
images. Which I never doing anything without a current image file it will save your butt. 			

Install Centos 4.3 on the second hard drive and use the automatic partitioning tool but don't			
put grub on your Master MBR put it on the first sector on your second drive. When you get to the			
Boot Loader Configuration screen make sure you check the Configure advanced boot loader			
options. The next screen will give the option where to put Grub Boot Loader. It should say like			
hda or hdb. Hda is usually your XP Drive. Put it on hdb.

Now duel booting using XP boot manager (My Preference. I don't like third party boot managers.)

Use your CD 1 to boot to Centos 4.3.
Hit enter at the boot prompt Hot F2 and type linux rescue.
Hit enter for English
Hit enter for us
Setup network select no
At the rescue screen select continue
At the next rescue screen hit enter
Now you have a prompt sh-3.00#
At the prompt type in chroot /mnt/sysimage
If hdb2 is Not your boot partition, change it as appropriate. Type: df then determine which hda#
Run the command dd if=/dev/hdb2 of=boot.lnx bs=512 count=1
You should see
1+0 records in
1+0 records out
Type ls and you should see a file named boot.lnx 
Put a blank floppy disk in your a: drive 
Type mcopy boot.lnx a:
It should have copied the file to your a: drive

Now reboot to Windows

Copy boot.lnx to your root directory
Right click on your boot.ini file select properties and uncheck read only click ok
Double click your boot.ini file and add one line at the end it should read
C:\boot.lnx="Centos 4.3 Project". Then save it. When you reboot your XP boot
manager will come up and you can chose Centos 4.3 it jumps to the Grub Boot manager on your 
second drive.

My file looks like this

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(0)(1)\windows
[operating systems]
multi(0)disk(0)rdisk(0)partition(0)(1)\windows="Microsoft Windows XP Pro SP2"
/fastdetect /NoExecute=OptIn
c:\boot.lnx="Centos 4.3 Project"

You call it anything you want

---

### Post by jgcamp99 on 2006-06-09
"Now duel booting using XP boot manager (My Preference. I don't like third party boot managers.)"

I have no issues with either LILO or GRUB, both are automatic, and sometimes, the splash screen makes the task of selecting your boot option a visually stimulating experience. I use the tool that's easiest, we're talking about a boot loader here, something I want to look at for about as long as a bios initialization screen that doesn't have a single hardware issue on it. But, just for arguments sake, why would you want the Windows boot loader to come up first, then tell it to go to GRUB or LILO or whatever to select the flavor of Linux you really want to boot instead of XP. Isn't that redundant, GRUB or LILO can handle that on the first attempt at choice ?

---

### Post by Harley51 on 2006-06-09
No offense intended but it's my preference. I use this method to try out new verisons of linux. My question is if this has been tried before with Ubantu. I'm using Centos now. I tried most other Distros. I here Ubantu is top of the line.

---

