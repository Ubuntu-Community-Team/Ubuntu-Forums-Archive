---
title: "Totally confusing..."
date: 2006-03-03
forum: Desktop Environments
---

### Post by maxmiles on 2006-03-03
Hi, 

I'm trying to install Ubuntu onto a new PC and am going nowhere fast. Having just bought the PC from a friend, I'd like to keep XP on a partition, with all of the programs, etc. on it. What I've tried: 

Used live disk to run GParted. There's a tutorial online that supposedly helps you set up various partitions on the HD. I've tried to set up a ext3 formatted partition and it's not working as demonstrated. My question: Does all this have to be so complicated? Does anyone know of a tutorial out there that doesn't make one want to throw the Ubuntu disks away? 

I'll settle for being able to install ubuntu onto the second HD, that currently has nothing on it but is formatted for windoze. What I'd love to be able to do is reformat the main HD and install ubuntu onto that. Is this really possible? 

Any help would be greatly appreciated!

max

---

### Post by sony102600 on 2006-03-03
I have a two hard drive , windows on one HD, Ubuntu on the other set up....If you really have a 2nd harddrive this shouldn't be too hard...

Just put the ubuntu install cd into the drive, and boot from it.... when you get to the partition part, select the hard drive you want to install ubuntu from and delete the partition, and then select it again as the place you want to install it to...

If your problem is more complicated and this is obvious to you then I'm sorry, just checkin though.

---

### Post by maxmiles on 2006-03-03
Thanks for your help Sony, it's clear for now I'll only be able to install on the second drive. I have an 80GB 10,000 rpm drive with XP already on it that I wanted to add Linux to, but the details are still wayyyy to confusing at the moment. In almost every tutorial or discussion I've read there's a detail that could seriously trip someone up if they aren't totally clear on what's going on. Obviously I'm not clear on what's going on... ;-)

---

### Post by sony102600 on 2006-03-03
I'm new to ubuntu as well, and have been on here for the last 3 days trying to get on getting my internet to work with it (it seems the onboard ethernet with my motherboard is not supported i'm guessing) but its going on day 4 and still no closer to getting online with ubuntu...

also, about your situation... if you have a place to back up your files you use on windows, you could just go ahead and delete windows on that hard drive and install linux to it with the linux disk, and then go ahead and reinstall windows with a windows install disk on the other one... however, you would need a place to back your info while this is going on.

---

### Post by Mustard on 2006-03-03
[QUOTE=sony102600]I'm new to ubuntu as well, and have been on here for the last 3 days trying to get on getting my internet to work with it (it seems the onboard ethernet with my motherboard is not supported i'm guessing) but its going on day 4 and still no closer to getting online with ubuntu...

also, about your situation... if you have a place to back up your files you use on windows, you could just go ahead and delete windows on that hard drive and install linux to it with the linux disk, and then go ahead and reinstall windows with a windows install disk on the other one... however, you would need a place to back your info while this is going on.[/QUOTE]

Installing Windows second is always a troublesome issue, I think its worth mentioning.  Firstly Windows will always try to install on the primary drive.  It doesnt like being on the secondary drive.  Secondly it will overwrite grub on the drive its installed on, so you would have to reinstall grub.  Seeing as the the user above is having trouble with partitioning, I would think that reinstalling grub manually would be an even greater nightmare scenario. :)

You can install Windows on a secondary drive, but its a  bit of mucking around to do it.  I actually disconnected the drive I had ubuntu on (unplugged the power from the back of the drive), then switched the jumper on the back of the secondary drive, to make it the master.  Then installed windows, then I switched the ubuntu drive back to master drive, made windows the slave drive and also had to use a special grub trick, so that windows thinks its still running from the master.

I guess what I am trying to emphasise is that 'just installing windows second' is probably a bit more complex than some might expect.

---

### Post by maxmiles on 2006-03-03
ok, I've installed Ubuntu on the second drive and am typing from it now. (the iBook is NOT happy. ;-) It's running well, but now I have the problem of figuring out why one of my monitors isn't working. I have a 128 MB graphics card and two CRT's, I'm figuring with the right driver or something it would work? One things certain, Linux ISN'T for the faint of heart. Sony, I wish you luck figuring out what's messing with the network connection. Thanks for the extra info Mustard. 

max

---

