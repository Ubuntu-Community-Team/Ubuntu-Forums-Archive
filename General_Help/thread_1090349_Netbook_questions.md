---
title: "Netbook questions"
date: 2009-03-08
forum: General Help
---

### Post by danbuter on 2009-03-08
I have an HP Mini with XP on it. I would like to install a linux distro, but I have a few questions:

1. I've heard I will have to remove swap and somehow limit writes, as the computer has a SSD. Will this really mean much or only add a month to the life of the computer?

2. If it really is important, is there  a step-by-step way to do this? And I mean every little detail, not just "remove the swap partition". If I knew how to do that safely, I'd already have done it.

3. If the swap and writes aren't that important, I'll just put in a regular distro. If they are, do any of the tweaked distros have this done automatically during install?

4. I've heard ext4 may be more netbook-friendly. Should I just wait until it starts popping up in distros before installing Linux?

Thanks!

---

### Post by Chibone on 2009-03-08
Hopefully, this answers some of your questions as this took me a while to write.

If your SSD does write leveling decently (which most do), then I would say there is no need.  The SSD failure mode will make your SSD read-only as well (write cycles are limited, not read cycles), so you are quite unlikely to lose data.  Also, the time to failure we are talking about is years.  More likely the screen will burn out or you will have moved on to a new laptop before you run out of writes.

If you are worried about the limited lifetime, there are two things I would do in your case.

1)Having enough RAM so you don't ever touch swap.  On Windows this is impossible as I had 2 GB of RAM, but I only ever used 1 GB and I still had a considerable sized swap file. On Linux, I had 2 GB of RAM and a 2.88 GB swap file and I never touched the swap in normal usage.  Ever. I upgraded to 4 GB RAM to run Windows in a virtual machine with 1.5 GB memory and not hit swap.

2)If you want to erase or change 1 byte of data, you will have to have the whole block the data is contained in erased.  So you might be doing a lot more writing than is strictly necessary. It might be that ext4 is better because your small writes are packed so they are done all at once with the minimum number of writes possible. But if you aren't making a lot of small writes I wouldn't worry.  With normal use, you will be fine.

During install, you can manually partition.  It's been a while since I've done it, but ...

- When you get to the partitioning step in the installer, you would use the manual option (I think it's step 4 in the Ubuntu installer) The following steps are for Ubuntu installer but you can adapt them for the Linux distro you pick.

- After selecting "manual", click on your XP partition and click resize. 

- If you are completely removing XP, click on it and select Delete.

- After making room for Linux (doing one of the two steps above), make a root partition with the free space (mount point /) and do not make a swap partition. 

I haven't tried a tweaked distro so I wouldn't know if they do this, but I imagine they would.  You'd have to ask on their forums.

---

### Post by linesma on 2009-03-08
I cannot answer your questions about SSD's, but I can tell you about the custom distros.  I have an Asus EeePC running EEEbuntu 2.0 Standard, and it works great.

If you are relatively new to Linux, I suggest going with a custom distro like EEEbuntu or EasyPeasy.  They both have been tweaked to work better with the Intel Atom Processor and have optimizations done for SSD's.  Both are based on Ubuntu.  EEEbuntu is available in three flavors, Standard, Netbook Remix, and Basic.  Easypeasy uses the Netbook Remix interface.

EEEbuntu worked great out of the box.  No configuring was required to get the wireless, camera, and touchpad working.  It uses a Kernel that has been specially compiled for netbooks.  Do not let the name fool you, it will work with other manufacturers Netbooks, because the underlying hardware of netbooks are generally similar.  I chose EEEbuntu because it could be installed with out the Netbook remix interface.  Both EEEbuntu and Easypeasy can be installed to and then run off of a SD card.

Here is a link to Easypeasy: [http://www.geteasypeasy.com/]("http://www.geteasypeasy.com/")

Here is a link to Eeebuntu:  [http://www.eeebuntu.org/]("http://www.eeebuntu.org/") 

I hope this helps you,

linesma

---

