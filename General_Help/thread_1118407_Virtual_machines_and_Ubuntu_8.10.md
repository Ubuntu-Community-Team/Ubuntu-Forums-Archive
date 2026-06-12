---
title: "Virtual machines and Ubuntu 8.10?"
date: 2009-04-06
forum: General Help
---

### Post by Zedday on 2009-04-06
I'm running Windows XP.
I would like to try out ubuntu, but i don't want to do a dual boot quite yet, so i was wondering about virtual machines.

1) are you able to save files, turn off your computer, come back the next day and open up the same files? or does it get wiped clean every time?
2) is it a lot of strain on a computer? like running two operating systems at once? will a computer be able to handle that?
3) what are your overall opinions on virtual machines?

---

### Post by DGortze380 on 2009-04-06
> **Zedday said:**
> I'm running Windows XP.
I would like to try out ubuntu, but i don't want to do a dual boot quite yet, so i was wondering about virtual machines.

1) are you able to save files, turn off your computer, come back the next day and open up the same files? or does it get wiped clean every time?
2) is it a lot of strain on a computer? like running two operating systems at once? will a computer be able to handle that?
3) what are your overall opinions on virtual machines?

1) The software creates a virtual hard drive (just think of it as a really big file). The OS is installed on the virtual hard drive (file). Anything you do on the virtual machines is also saved on the virtual hard drive (file). Yes, it is permanently saved.

2) What the specs of your computer?

3) Great idea. The future of computing. (Not looking for a discussion, he asked for an opinion, I gave it, period).

---

### Post by ryanhaigh on 2009-04-06
Virtualbox will be able to do everything you want. The machine I use is an old P4 and it runs fine. A newer CPU might have extensions so that you get better performance but I found that the virtual xp machine was just as fast as the real thing (probably because I didn't have antivirus on it). I was using the VM for office 2007 and some engineering packages. 

One of the best things about running a VM was that I could use my card reader that was otherwise inaccessible on Ubuntu. I also use a virtual ubuntu machine on my work laptop for those times when bash lets me get things done much faster than I can with bare windows.

---

### Post by Zedday on 2009-04-06
> **DGortze380 said:**
> 1) The software creates a virtual hard drive (just think of it as a really big file). The OS is installed on the virtual hard drive (file). Anything you do on the virtual machines is also saved on the virtual hard drive (file). Yes, it is permanently saved.

2) What the specs of your computer?

3) Great idea. The future of computing. (Not looking for a discussion, he asked for an opinion, I gave it, period).

Thanks for your opinion, and I'm glad stuff saves on it :)
Ad if you come back to this thread, I have 512mb ram, single core processr at 2.2Ghz, 160gig HDD+500gig external

---

### Post by mb_webguy on 2009-04-06
Your two best options would be a Wubi installation, which installs Ubuntu in Windows like a Windows application, or using a LiveCD or LiveUSB.

Both should be considered purely as options for evaluation, and not permanent solutions.

The former, as I said, installs Ubuntu like an application within Windows, and suffers from the same basic issues as running a virtual machine, in that it uses more resources than running the OS itself.  A Wubi installation should use fewer system resources than running Ubuntu inside a VM, however.  A Wubi installation is persistent, allowing you to make changes and install software, which persist from one session to another.

A LiveCD is runs off of a CD, and is therefore going to be a bit slow (depending on the read speed of your CD/DVD drive), and because it's being run from a read-only medium, isn't persistent.  You can install software and make changes, but these reside only in memory, and will be lost when you shut down.  A LiveUSB is a bit more flexible than a LiveCD in that it can be persistent to a degree, but it requires you to boot from a LiveCD to create it in the first place.

---

### Post by DGortze380 on 2009-04-07
> **Zedday said:**
> Thanks for your opinion, and I'm glad stuff saves on it :)
Ad if you come back to this thread, I have 512mb ram, single core processr at 2.2Ghz, 160gig HDD+500gig external

I would suggest upgrading your RAM before running a virtual machine. While XP can run on 256MB, and Ubuntu can run on 256MB, they will be painfully slow and prone to crashes. 

1GB should be sufficient as it will allow 512MB for each OS. Rule of thumb with RAM is to buy as much as you can afford (that is supported).

Other than that, you should be good to go.

---

### Post by ryanhaigh on 2009-04-07
> they will be painfully slow and prone to crashes
Slow yes but I see no reason why they would be prone to crashes. Each OS will use its disk to store data that would otherwise be in memory (swap partition/paging file) and while this can make performance unbearably slow it shouldn't cause crashes.

---

### Post by DGortze380 on 2009-04-07
> **ryanhaigh said:**
> Slow yes but I see no reason why they would be prone to crashes. Each OS will use its disk to store data that would otherwise be in memory (swap partition/paging file) and while this can make performance unbearably slow it shouldn't cause crashes.

tell that to the VMs I ran on a core duo with 512MB...

I understand your thought process, but I've seen it first hand. Lack of memory will cause crashes eventually regardless of swap/paging/virtual memory.

---

