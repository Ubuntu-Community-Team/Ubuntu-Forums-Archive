---
title: "[SOLVED] Help!!!! Need To Update Bios??"
date: 2007-07-10
forum: Desktop Environments
---

### Post by arashiko28 on 2007-07-10
I have this OLD Desktop, is a clone, don't know the motherboard name (the pc is a handmedown). Any way, I've decided to undust granny after my laptop tragically fell into near death due to a voltage problem. Now, the granny has an Intel Celeron processor 701 MHz, 256 MB of RAM, right now, (don't know how) is running Windows XP. But, when i try to install ubuntu, it frozes into what a friend of mine describes as a HD problem, but it has no weird sounds, nor gives any problems with XP. Someone recommended me to use Xubuntu, the same thing happens. Now, the BIOS, have never been update since it was first bought (know the owner I used to fix it when it had any problems). It has a 1993-2000 signature. I downloaded a newer version but don't know how to do it, it has floppy and CD drive. On my laptop, I updated the BIOS once, but only had to double click the file...:confused::confused::confused: HELP PLEASE!!!! DESPERATE!!!

---

### Post by Theimon on 2007-07-12
How can you download a BIOS when you don't even know what kind of motherboard you actually have? 
I don't think this is a HD problem...would it not also occur in Windows XP? Because I can't imagine you're swapping HD's everytime you switch between XP and Ubuntu.
I think you should try the alternate install cd first before you start thinking about updating your BIOS.

---

### Post by arashiko28 on 2007-07-14
I already know all that, but don't know hot to upgrade the BIOS on a desktop, it is not the same that on a laptop. Now, I won't be swapping between OS's, the plan is to install linux alone. But I keep receiving the error every time I try to do it. It says that the port failed to respond.... or something like that

---

### Post by reset3x on 2007-07-14
> **arashiko28 said:**
> I already know all that, but don't know hot to upgrade the BIOS on a desktop, it is not the same that on a laptop. Now, I won't be swapping between OS's, the plan is to install linux alone. But I keep receiving the error every time I try to do it. It says that the port failed to respond.... or something like that

Can you post the error so we can tell whats going on? Flashing your BIOS can leave you with a doorstop if you're not familiar with how to do it... If you're getting the error during POST you may be able to halt the screen  by hitting the pause key.  If you're getting the error while you're booting from the Live CD do you're best to write down what it says and post it here... If XP is working Ubuntu should work too.. I'd don't think it's a BIOS issue....

---

### Post by arashiko28 on 2007-07-14
Maybe this is way too unbelievable, I changed to a 40GB HDD, and the problem kept going on, changed the IDE cables, got worse, so put everything back as it was, thinking that the HDD was damaged, how ever, could install XP with no bigger problems. Changed the HDD to another desktop and managed to install Xubuntu from there. Now my problem is that it seems to stay looking for the ATI Radeon 7000, 64MB, instead of recognizing whatever the older motherboard has built in. I was told that if had any problem, press escape when the GRUB countdown ended... but it does not shows, so I can't do it, How ever, I can access terminal in some odd DOS-like screen (only missess that hideous green letters). 

I need the command to deactivate that search, in other words, to force a reconfigure...:confused:
PD: No dual boot!!! Just Xubuntu.

Update!!! Found the GRUB countdown, everything goes great until it stops opening root and waiting for a command.... what do i write???

---

### Post by reset3x on 2007-07-14
> **arashiko28 said:**
> Maybe this is way too unbelievable, I changed to a 40GB HDD, and the problem kept going on, changed the IDE cables, got worse, so put everything back as it was, thinking that the HDD was damaged, how ever, could install XP with no bigger problems. Changed the HDD to another desktop and managed to install Xubuntu from there. Now my problem is that it seems to stay looking for the ATI Radeon 7000, 64MB, instead of recognizing whatever the older motherboard has built in. I was told that if had any problem, press escape when the GRUB countdown ended... but it does not shows, so I can't do it, How ever, I can access terminal in some odd DOS-like screen (only missess that hideous green letters). 

I need the command to deactivate that search, in other words, to force a reconfigure...:confused:
PD: No dual boot!!! Just Xubuntu.

Update!!! Found the GRUB countdown, everything goes great until it stops opening root and waiting for a command.... what do i write???

So you installed Ubuntu and pulled the drive and put it in another PC? That's going to give you nothing but headaches... To begin with X is configured for the video in the other PC. Then there's the rest of the hardware that's most likely different... I would suggest that you figure out what machine you want to install the OS in and go that route....

---

### Post by arashiko28 on 2007-07-15
Is in the old one, but for some reason that only that computer knows, does not allows me to install any Linux. How ever, goes like train on track while installing windows, but I have no interest in using windows anymore.

The question lies on why, I can install a memory, HDD space and power eater like Windows XP, and can't do it with Xubuntu, wich consume less than half of everything i just mentioned?:confused:

UPDATE!!!

I managed to fix the problem, now what's left is the resolution, the screen resolution is way to big! I want it 1024x768, and is 640x480. Ackwardly uncomfortable. Can't change it on display settings. I've tried on dpkg-recoconfigure xserver-xorg, and no matter what i do can't eliminate what is selected, nor select new ones.

---

### Post by reset3x on 2007-07-15
Boot to recovery mode and enter:

```
sudo dpkg-reconfigure -phigh xserver-xorg
``` 

You use the space bar to select the options you want...

---

### Post by arashiko28 on 2007-07-19
Thanks, problem solved with a similar command.:guitar:

Ok, sorry i lefot it so uncomplete. What I did was this:
After restarting went to restore mode, as root: dpkg-reconfigure xserver-xorg
On the device part, changed the driver "ati" for "vesa", later on, found out the name of the video driver of the motherboard and changed it. problem solved. No more head aches, everything works like a charm!!!

---

