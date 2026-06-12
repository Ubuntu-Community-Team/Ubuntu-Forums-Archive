---
title: "Ubuntu 14.04 Desktop 64 bit Kernal panics every day Frezzing"
date: 2014-04-28
forum: Desktop Environments
---

### Post by hitekwaiter-j on 2014-04-28
Since I have written the below, I'm getting Kernal Panics every single day. I then go to recovery mode, enable networking
and fix broken packages.
Log into root shell and run
apt-get install-f
apt-get update
shutdown -r now.

it then reboots to GDM, but I have to use classic GNome

description: VGA compatible controller
product: Cedar [Radeon HD 5000/6000/7350/8350 Series]
vendor: Hynix Semiconductor (Hyundai Electronics) '

About 2 weeks before the 14.04 official release, I downloaded (and, yes donated a little) to get 13.10 desktop 64, which I installed on a 
fresh hard drive from scratch.
I had a lot of problems with  the display and screen frezzing up (no response, no errors, just frozen)
I found that my graphics card responds better with the open sourced drivers (not amd/catalyst) 
Since 14.04 (note, the proprietary drivers work better in my dual installation of 12.04) 
I have updated my 13.10 Ubuntu desktop 64 bit to 14.04.

I have also run an 
apt-get install gnome

***I NEED to know the command to switch display managers from the root promt in recovery mode***
I was promted and decided to change to GDM (gnome display manager) welcome screen, but I find Gnome is Worse for the screen frezze problem, so I select Unbuntu/unite

Note: I'm not running the proprietary ATI/AMDFGLRX GRAPHICS DRIVER for  my amd graphics card
that makes the problem worse.
****NOTE******
over 12 hours later. Had to go to work. Got back...left out some stuff****
********************************************************************
Hardware info.
the command
sudo lshw -C video
yields:
description: VGA compatible controller
       product: Cedar [Radeon HD 5000/6000/7350/8350 Series]
       vendor: Hynix Semiconductor (Hyundai Electronics)

NOTE: this is from the XORG i have running on the same PC, from a different Harddrive (yes, i have a lot of hard drives)

I know its a ATI Radeon 8350 series card
I'm only running the open source driver on my 14.01 side. 

Changing to Gnome (classic) desktop help, but I just got another crash/frezze

The card IS listed amongst the fullly supported video cards.

---

### Post by hitekwaiter-j on 2014-04-29
description: VGA compatible controller
       product: Cedar [Radeon HD 5000/6000/7350/8350 Series]
       vendor: Hynix Semiconductor (Hyundai Electronics)

---

