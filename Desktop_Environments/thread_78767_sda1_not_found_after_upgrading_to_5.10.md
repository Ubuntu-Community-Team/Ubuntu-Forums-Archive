---
title: "sda1 not found after upgrading to 5.10"
date: 2005-10-18
forum: Desktop Environments
---

### Post by TWBalls on 2005-10-18
Hello,
  First, I'm hoping this wasn't already covered as I did do some searching before posting. 
Second, here's my PC specs:
Dual Xeon 3.06
Supermicro [X5DAE]("http://www.supermicro.com/products/motherboard/Xeon/E7505/X5DAE.cfm") (Intel E7505 + ICH4)
2GB REG. ECC Kingston Value RAM
Intel [SRCS14L]("http://www.intel.com/design/servers/raid/srcs14l/index.htm") RAID Controller (In the first PCI-X Slot)
2x 80GB Seagate 7200.7's in RAID-1 (sda1 - ReiserFS)
2x 160GB Seagate 7200.7's in RAID-1 (sdb1 - ReiserFS)
120GB Seagate Barracuda (hdc - NTFS - Temporary, just copying files from it)
Lite-On SOHW-1693S 16x DVD Burner (hdb)
Nvidia GeforceFX 5600XT 
Turtle-Beach Santa Cruz

I originally had this connected to a Startech SV411K KVM switch running WinXP. Had no problems, but want to use XP on a different PC so I decided to install Ubuntu, which never gave me problems on other PC's.
Installed Hoary, then installed the 686 SMP kernel. After booting into the SMP kernel (2.6.10-5-686-smp), mouse function was flakey (Works fine using non-SMP kernel :confused: ). Tried connecting mouse directly to PS/2 (bypassing KVM) and it works. Then, I was unable to set DMA on my optical drive using hdparm. Then, I had problems with gam_server eating up CPU cycles when watching any video. :mad: 

So, I decided to upgrade to breezy and hope it would fix my problems. I upgraded following [these instructions]("https://wiki.ubuntu.com/BreezyUpgradeNotes") (I used Synaptic).
Everything *seems* to have installed properly. I didn't see any mention of missing/broken packages/dependencies. However, when I attempt to boot into the new 2.6.12-9-686-SMP kernel (or even the Non-SMP kernel) I get an error stating that /dev/sda1 is not found, then I get dumped into busybox. 
Thankfully, I still have the 2.6.10-5 kernel installed, so I can choose that and work, but I'm wondering why the new kernel can't seem to locate my array? Any suggestions?

Thanks.

---

### Post by TWBalls on 2005-10-19
Bump

Some more info/thoughts:
Previously, I also tried Debian 3.1. Using the 2.4 based kernels (Uniproc & SMP) I had no problems with my mouse. When I installed the 2.6 Kernels, mouse would work using Non-SMP kernel but would not work using 2.6 based SMP kernel. 

Since 2.4 based Kernels seem to play nicely, I'm wondering if I should try downgrading to warty? Or would that screw things up?

Thanks.

---

### Post by RAOF on 2005-10-19
Ok, my guess would be that for some reason support for that raid card is not being built into the breezy kernel.  That's strange, and annoying, but you can probably get around it by building a new kernel and checking that support for your card is built in.

Your SMP mouse issue is also a bit wierd, but SMP is actually pretty difficult to do correctly.  All sorts of wierd stuff can happen - deadlocks and races and data corruption, oh my! :)  It's possible that the latest vanilla kernel from kernel.org will have fixed your mouse problem, I don't know.  Given that it worked when you plugged the mouse in directly, there's probably some edge condition with slightly slower/more noisy mouse input somewhere in the mouse drivers.  It might be nice to file a [bug]("bugzilla.ubuntu.com"), if there isn't one already :)

I've recently built a kernel, and it was actually very painless.  I might write up a breezy-kernel-howto sometime soon, but for the moment try [this thread]("http://www.ubuntuforums.org/showthread.php?t=43065&highlight=breezy+kernel+howto+compile%5C").  There's a lot of it, but I just followed the first page instructions, and it worked fine.  For breezy, I believe you should add the --initrd option when you do
```
sudo make-kpkg --initrd --append-to-version=-custom kernel_image modules_image
```
I'd also recommend running "make oldconfig" before "make menuconfig" or "make xconfig" or whatever - this will initialise all the options to what your running kernel has, and the ubuntu kernels have nice, sane defaults :)

---

