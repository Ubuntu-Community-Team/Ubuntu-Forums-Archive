---
title: "VirtualBox question"
date: 2009-06-19
forum: General Help
---

### Post by merlinus on 2009-06-19
WIth my new machine, I finally have enough system resources to run the one windows app I need in VirtualBox!  It took some tweaking, but it is running fine.

My question is when I install a new version of ubuntu, will I have to go through reinstalling the OS and app again?  I have a separate /home partition where application settings and configurations live, and of course that does not get formatted upon upgrading and/or reinstalling.

---

### Post by geirha on 2009-06-19
With that setup, your virtual machine should be safe. The files for virtualbox's virtual machines are stored in a hidden folder ".VirtualBox" in your home-folder. If you do a reinstall of the OS rather than upgrading the OS, you'll of course need to install virtualbox again too, but it should automatically locate and use any existing ".VirtualBox" folder.

---

### Post by merlinus on 2009-06-19
Thanks!  That's what I was hoping to hear!!  Whew...

---

### Post by raymondh on 2009-06-19
> **merlinus said:**
> Thanks!  That's what I was hoping to hear!!  Whew...

Have fun with VB, merlin :)

---

### Post by merlinus on 2009-06-19
Thanks, Raymond.  I frankly am amazed that I got the app to run, after failing miserably since 7.04.  Next challenge is setting up a network printer.

The big difference is that I gave the VM a dynamic 7G, with 1.5G RAM and 128MB VRAM.  My old machine did not have those capabilities (total was 1.5G RAM and 128 VRAM, so I could not allocate enough of either).

I only wish there were an open source alternative, but at least it's not a product from the big pigs.

---

### Post by raymondh on 2009-06-19
> **merlinus said:**
> Thanks, Raymond.  I frankly am amazed that I got the app to run, after failing miserably since 7.04.  Next challenge is setting up a network printer.

The big difference is that I gave the VM a dynamic 7G, with 1.5G RAM and 128MB VRAM. 
I only wish there were an open source alternative,

What, my freind, do you plan to run on VB?  Those are good sized allocations....

I believe the day will come when first choice will be open source ....

---

### Post by merlinus on 2009-06-20
The new machine is a dual core 3GHz, 4G RAM, nvidia geforce 9400 gt with 512M VRAM, and 500G hdd, so giving those resources to VB was easy.

The app is graphic-intensive, and runs better than it ever did on a straight windows install.

---

### Post by merlinus on 2009-06-20
Finally figured out how to access a win2000 box with network printer attached!

In VB Settings, I had to change Network/Attached To from NAT to Bridged Adapter.  The win box showed up instantly in Network Places, along with the shared printer.

Score one for RTFM!!!

---

