---
title: "Upgrade ubuntu 9.04 kernel to 2.6.30"
date: 2009-05-17
forum: General Help
---

### Post by m0tyrider on 2009-05-17
Gday guys im not sure if im posting in the right section as i am fairly new here...

I have to dual boot my system, windows/linux. I much rarther linux but i cannot get sound in it because my sound card is a Asus Essence STX, and the kernel i got 9.04 with does not support it. But apparantly 2.6.30 does...

Can somebody help me upgrade the kernel install on my Ubuntu 9.04? I have no idea how to go about it, ive done a bit of google searching and found nothing thats helped :(

Or even if there is a newer kernal id much rarther use that as it can only be better! though id rarther stability over features...

Please help me out fellow linux users!

---

### Post by TheExplorer on 2009-05-17
You may install it from [here]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/"), it's done by the Ubuntu Team, **BUT**...
It's not supported by Ubuntu as it should with the default kernel. You are doing it at your own risk. Note also that the 2.6.30 kernel is still in RC stage (for e.g. if you've got a wifi card it's more likely that it won't work 'cause there are a lot of complaints about that on the Net), but still you are free to try this new kernel.
Btw, I'm using 2.6.29.3 kernel as it fixes Intel graphics regression found in the default Jaunty Jackalope 2.6.28 kernel. It's working fine for me.
I've also tried installing some RC from 2.6.30 branch. Well, it seemed to be more snappy and faster than 2.6.28, but I couldn't see the boot splash screen at all and also some minor issues.

**P.S.** Upgrading the kernel triggers also the reinstalling of your video driver and it will depend on the way you installed it in the first place (the native Ubuntu way or by your own hands). So that's all there is to it actually. Good luck learning Linux :)

---

### Post by m0tyrider on 2009-05-17
Thanks ill try it out and let you know how i go :)

---

### Post by m0tyrider on 2009-05-17
Kernel seemed to install fine, my audio works fine. But i cannot install a graphic driver for my Nvidia GTX260, i tried installing it via command line without xserver running and i get errors about my kernel and the compiler version.

Anyone know ways around this?

---

### Post by m0tyrider on 2009-05-17
Bump...

---

### Post by Arup on 2009-05-18
> **m0tyrider said:**
> Kernel seemed to install fine, my audio works fine. But i cannot install a graphic driver for my Nvidia GTX260, i tried installing it via command line without xserver running and i get errors about my kernel and the compiler version.

Anyone know ways around this?

Make sure older driver was removed with previous kernel, if not boot into previous kernel and remove it, then boot into your new kernel and do a sudo apt-get install build-essential

---

### Post by zika on 2009-05-19
is there a way I could make 2.6.30.rc6 boot with my ext3 on Jaunty in data=ordered or data=guarded mode? I do not want to use writeback ... too risky ... :)
as I understood data=guarded is not available in 2.6.28?
I've tried things that worked in 2.6.28... data=ordered in /etc/fstab e.t.c. ... nothing worked. if I put data =ordered in /etc/fstab I get read-only boot ... :(
update: For anybody concerned: rootflags=data=ordered is the magic string. In the meantime I moved to ext4 and that to Karmic ... and then to writeback ... .)

---

### Post by JohnnyRogers on 2009-06-18
I figured this might be a good spot to ask something, before starting a new thread on it.

I updated my kernel to 2.6.30-020630-generic, but now the update manager wants to install 2.6.28.13.17. Do I ignore this? 

Also, I can't use remastersys to make a backup of my system anymore - the live CD just boots to a really strange shell that I can't do anything more than reboot with. Is this fixable? I can't even follow a manual live CD creation tutorial with the new kernel.

Any advice on either of these questions would be appreciated. Thanks!

---

### Post by stlouisubntu on 2009-08-01
> **JohnnyRogers said:**
> I figured this might be a good spot to ask something, before starting a new thread on it.

I updated my kernel to 2.6.30-020630-generic, but now the update manager wants to install 2.6.28.13.17. Do I ignore this? 

Also, I can't use remastersys to make a backup of my system anymore - the live CD just boots to a really strange shell that I can't do anything more than reboot with. Is this fixable? I can't even follow a manual live CD creation tutorial with the new kernel.

Any advice on either of these questions would be appreciated. Thanks!

I installed this kernel on a 64-bit Jaunty install and had the same update manager.  What I am doing and what I would advise is to do updates manually from now on (i.e. use Update Manager but look at each and every available update) and uncheck each and every possible update with linux in the title at all.  Otherwise you risks improper kernel mixing or reverting to the old kernel and undoing your 2.6.30 install.

I have not every used remastersys but would recommend changing to a different backup method and only backing up your /home folder and not your entire system (would seem much more efficient anyway) and exclude .iso and large files which are easily re-downloadable.

In regard to security and stability kernel updates, it seems that we are out of luck in that regard and that is a sacrifice we have to make for using this more current, but in-between ubuntu releases kernel.

Hope this helps. :)

---

### Post by stlouisubntu on 2009-08-01
> **stlouisubntu said:**
> In regard to security and stability kernel updates, it seems that we are out of luck in that regard and that is a sacrifice we have to make for using this more current, but in-between ubuntu releases kernel.

Hope this helps. :)

I would like to revise and extend my remarks on that last paragraph.  By what I have read, I see no way to add the kernel ppa as a repository for updates, but it does look like those who have installed the 2.6.30 kernel can still have security and stability updates.  I downloaded my kernel from here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/)
However, if you back off one to the parent folder, you will see that v2.6.30.1, v2.6.30.2, v2.6.30.3, and v2.6.30.4 are also available.  So if one keeps watch on this directory, kernel stability / security updates are available.  The only catch is that they must be downloaded and installed more or less manually (i.e. via dpkg -i, not via apt-get aptitude, or synaptic.)  Here is a link to the installation instructions I used (must be adjusted to the update being installed) :

[http://www.ramoonus.nl/2009/06/10/linux-kernel-2-6-30-installation-guide-for-ubuntu-and-debian-linux/](http://www.ramoonus.nl/2009/06/10/linux-kernel-2-6-30-installation-guide-for-ubuntu-and-debian-linux/)

Hope this is helpful.

---

### Post by cbraxton on 2009-08-06
I tried out the 2.6.30 kernel on my Jaunty system, most things worked well, the only problem is that suddenly my parallel-port starting spewing garbage out to the printer. Booting up the same system on 2.6.28-n the port works OK. Looks there is some kind of problem with the lpt port code.

I see there is also a 2.6.31 kernel release candidate, that's probably in even rougher shape.

My main interest in the newer kernel is any improvements in the ext4 filesystem, since I'm using that on a 1.5TB drive.

---

