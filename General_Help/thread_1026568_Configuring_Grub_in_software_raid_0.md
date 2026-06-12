---
title: "Configuring Grub in software raid 0"
date: 2008-12-31
forum: General Help
---

### Post by OmnyDevi on 2008-12-31
Greetings,

Just a quick question. I have Windows XP x64 and Ubuntu x64installed on a software raid 0 on my machine at home. I cannot get grub configured for anything. My raid using dmraid is /dev/mapper/nvidia_fgajafce which Ubuntu installed just fine on. WindowsXP x64 is nvidia_fgajafce1 and Ubuntu x64 is nvidia_fgajafce2. Problem is when I go to grub and do device (hd0) /dev/mapper/nvidia_fgajafce the command completed. Then I do find /boot/grub/stage1 or find /grub/stage1 and I get either a error 15 not found, error 17 cannot mount the partition, or it actually says something like seeing if /boot/grub stage 1 exists...no, checking if /grub/stage1 exists....no. 

After doing some research, it looks like you can install grub on a raid1, or raid5, but doesn't look like you can on a raid0. Is that accurate?

If so, could I toss in another hard drive and not make it part of the raid array and just as a bootloader drive and use that to detect the array and maybe get it to work better? 

Any/all help, feedback, comments, suggestions greatly appreciated!

UPDATE! Woot! Just found out Call of Duty 4 was able to run via wine. Although I will miss my old servers on XP I used to play on, that game was the only reason I was holding on to XP. Now I have no reason to use it, thus I only need Ubuntu as my only OS. Will report if the install goes well with only the partitions Ubuntu will make and if doing away with my XP partition will make this any easier. *squeal* I am so happy!! Woohoo!!

---

### Post by fjgaude on 2008-12-31
I've never heard of Ubuntu or Linux being put onto a fakeRAID raid0 array uisng **dmraid** or any other way.

I've never heard of **grub** being put on raid5 or raid0, period.

You can put in a boot drive and have it come up with Ubuntu and then it will detect all else that is mountable on the computer.

Here's a link that has been useful to many:

[http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/](http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/)

Gook luck!

---

### Post by OmnyDevi on 2008-12-31
Thank you for the reply! 

There are several tutorials out there for installing Ubuntu on fakeraid. I have tried a few (several times) and got it to install with no issues at all. Not until configuring grub came into play. But it doesn't matter too much anymore. I just wanted XP for my games, but after doing some more research, I can play them in Ubuntu just fine, so XP is going out the window. I destroyed my array and installed Ubuntu on my lunch break. Guess I should have tried installing that other HDD I had outside of the raid0 just to see what would happen...oh well, gives me something to do later when I get bored :D

---

### Post by fjgaude on 2008-12-31
Okay, and have a great day, moment-by-moment!

---

