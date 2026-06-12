---
title: "Vista will only boot with the LiveCD"
date: 2009-06-02
forum: General Help
---

### Post by xeltul11001 on 2009-06-02
Here's the deal:

I was testing out a customers hard drive(that was bad) on my computer and when I plugged my hard drives back in my computer would freeze after the "Boot from CD:" prompt durring bootup.  So I used the ubuntu live cd and I was able to boot from the hard drive.  So after doing some searching I found that could try reinstalling grub.  So after following the instructions I reinstalled grub.  It would then load grub and I could boot to Ubuntu just fine but when I tried to boot to Vista it would give me this: "Error 12: Invalid Device Requested"  If I use the Ubuntu liveCD I can boot to Vista just fine.  I read that Grub and Vista don't get along the best.  I heard that the best thing to do is install EasyBCD and use it instead of Grub to dual boot.  So using the Ubuntu LiveCD I booted to Vista and installed EasyBCD.  But when I rebooted it still loaded grub.  If I use the LiveCD and use it to load Vista it loads the menu EasyBCD put on there.  So the Bios is loading my second hard drive first.  I can manually(in the bios boot menu) boot from my first hard drive and vista boots just fine.  But if I reboot the computer it will boot from the second hard drive and load grub.  I cannot find an option to force the computer to boot from the first hard drive first automatically in the bios.

So I need to either fix grub so that it will load Vista.  Or get my computer to boot to the first hard drive and dual boot with EasyBCD(which by the way I cant get to load Ubuntu).

I have 2 hard drives

The first is 160GB and has Vista installed on it with only one Partition.

The Second is 640GB with several partitions including one with Ubuntu installed on it.

In other posts they have asked to attach the attached results.txt

---

### Post by xeltul11001 on 2009-06-05
bump

---

### Post by DeMus on 2009-06-05
> **xeltul11001 said:**
> bump

Are you sure you re-connected your drives the right way? You did not by any chance exchange the two?

---

### Post by xeltul11001 on 2009-06-05
Yeah, I am sure I connected them back up the same as they were before.  And I can see that in the Bios too.

---

