---
title: "checking facts before switching to ubuntu (kind of)"
date: 2006-08-05
forum: Desktop Environments
---

### Post by maniacmusician on 2006-08-05
All right, after testing xubuntu for a couple of months, I've decided to install it on my main machine so I could get real perfomance out of it; I'm pretty sick of windows and only need it for some little things. What I'm going for is a Xubuntu install with a Windows XP virtual machine (I'll build it using easyvmx and use VMWare Player to run it) so that I can do the occasional Windows thing.

My main concern is sharing hard drive space...I don't really feel like using fat32 because, well...it sucks. Someone told me that windows can read and write to ext3...does this work well and is it stable? If so, that's probably what I will use. I have two 80 GB hard drives on this computer...i'm using one of them for my files right now and i have XP installed on the other one (this is the one that I will install Xubuntu on). I'm thinking i'll copy my files over to another computer (its a good 70 GBs so it will take a while :() and format the drive to ext3 using gparted or something like that and then copy the files back. sound good?

Another thing I was concerned about...How good is Ubuntu at handling newer hardware? I think have a new low-cost ATI chipset with onboard video and audio. Nothing too fancy, but I'm just double checking and making sure here.

Thanks

---

### Post by synd7 on 2006-08-05
Welcome to ubuntu :D 

Yes windows can read/write to ext2 and ext3 using drivers from [www.fs-drivers.org](www.fs-drivers.org), I've only been using it for a week and havent tried to write to my ext3 partition yet but ive heard that it works fine for most.

As for using vmware, i would just dual boot. Ive got windows and ubuntu on the one harddisk and i only boot into windows for a few things (photoshop etc). Try using wine (lets windows programs run on,linux) for windows apps and for those that dont work, just boot back into windows.

I hope this helps.

---

### Post by iamhugeinjapan on 2006-08-05
A virtual OS uses a virtual filesystem so you don't need to make a physical partition for the VMware Windows to run on. It is all contained in a single file on your linux partition.

---

### Post by maniacmusician on 2006-08-05
i've considered dual booting and its really just a hassle to be honest. I've never used a VM but it seems perfect for occasional use. I have tried wine and it works fine for some programs but not so well for others. And i'm all for trying new things, it promises to be an interesting experience.

Now all i have to do is set up one of my old computers so i can temporarily transfer those 70 GBs, and then get installing. and hope ubuntu handles new computers just as well as it did my old junkies.

---

