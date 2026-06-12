---
title: "single os grub problems"
date: 2008-07-10
forum: Desktop Environments
---

### Post by will3265 on 2008-07-10
Hi guys. i have read a little about grub and am a total newbie here. i have installed ubuntu on a couple of old pcs before and fiddled around. i liked what i saw so i decided to migrate my main machine from xp to ubuntu 8.04 x64. live worked fine so i installed ubuntu and rebooted. grub loads and gives me an error. error 22. then i got error 17 and error 15. these all came as i tried all the different things the other posts said to do. everything from swapping the sata plugs between drives, ticking the install boot loader box during install, unticking the bootloader box(which still gave me the grub error) and reinstalling several times. now i am going to try opensuse to see if it helps, its installing now. now my questions i have is:

why do i need a boot loader?

if a boot loader is for a dual boot machine why is it giving me errors when i only have one os installed?

is a boot loader drive specific, partition specific or systemwide?

is opensuse any good?

thanks in advance for any answer on sign point me in the right direction and i must say that after reading a fair bit of this forum i have realised that the linux forum community isn't the bunch of trolls they are made out to be. thanks again

---

### Post by ramaswamyps on 2008-07-10
give your partition table here.
if you have only one partition install grub to partition and make the partition active.

---

### Post by will3265 on 2008-07-10
i only had the single partition and a swap area. opensuse just formatted that same area (no partition alteration) and it is working fine using the same swap area and all. 
can i install ubuntu without grub?

---

### Post by VMC on 2008-07-10
> **will3265 said:**
> i only had the single partition and a swap area. opensuse just formatted that same area (no partition alteration) and it is working fine using the same swap area and all. 
can i install ubuntu without grub?

You have few options, Lilo maybe, but your MBR needs to know where to start. Grub is more than just a bootloader. You can also edit menu.lst and have Linu start immediately.

> ## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3


---

### Post by will3265 on 2008-07-10
ok i will try again. after the reinstall i will find menu.lst and see how i go. thanks again

---

