---
title: "stuck in lost Vista MBR hell/ Ubuntu kernel panic loop"
date: 2007-03-10
forum: Desktop Environments
---

### Post by Beruka on 2007-03-10
I install 6.10 amd 64bit from live CD. Previous installation was Vista only

I used noapic after F6 to get live cd to run. It went down hill fast after that. I installed Ubuntu on separate stat drive partitions to 50% as I can use remainder for other files.

After installation I continuously get Kernel panic - run without apic and have never booted installed Ubuntu. I have tried every conceivable way to boot from the kernel but can not do it. Please do not tell me to tell kernel to disable apic, as I will need actual instructions on how to do this. 

To make this real fun Ubuntu lost the master boot record of Vista. I can not boot from grub. I can not edit the grub file since I can not boot installed copy, and more fun yet I can not boot Vista and ignore the fouled Ubuntu drive. Reinstalling Vista now hangs as well.

I have read the files telling me to run with apic diabled, but I can not get past this annoyance without clear instruction. Vista is a boot choice instead of Ubuntu but as I mentioned that does not work either. 

I think it is clear Ubuntu lost the MBR of Vista or overwrote it. I didn't do this installation to waste a full saturday but to use Ruby on Rails with Ubuntu as described in 'Beginning Ruby on Rails Ecommerce' instead of using readily available Ruby downloads for windows 

so the solution is 

A- get Ubuntu to actually run of installation and repair MBR from grub file
B- wipe drives clean and only install Vista using Ruby 

I have found posts in bulletin boards describing the exact same problem and frustration with MS for some reason.... but no resolved solution.

I can not keep rebooting and guessing at boot sequences to make Ubuntu load. 20-30 is far to many already. I'll put Ubuntu CD in trash if this can not be resolved.

---

### Post by Ocxic on 2007-03-11
if your not worrind about your Vista parttitonthen i would suugest wiping your drive, then install Vista, and partitioning for ubuntu asweel while there then install ubuntu, It'll prolly work out better

---

### Post by timski on 2007-03-11
This thread - [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) - might also be helpful to you.

The best Vista tip I learnt was how to use gparted (it is on the live CD or the downloadable Linux System Rescue Disk) to temporarily set the "boot" flag for different partitions.

Aside from that, keeping the boot loader out of the master boot record seems to pay dividends. I've had no problems with:

* Partition up the space on the disk before installing any operating system. Then install Vista first.

* Manually set the Linux partition with the boot flag during Ubuntu installation.

* Manually installing GRUB on the Linux main partition during Ubuntu installation. The default is (hd0), which you can edit on the final setup screen. For example, if Ubuntu is in the second partition (hda2), you would change that to read (hd0,1). The first partition (hda1) would be (hd0,0).

This didn't require any further tweaking.

The main oddity to watch for is that some parts of vista don't take kindly to not being on the bootable disk. For example, the repair process (on the Vista install disk) seems to fail to find Vista if it isn't directly bootable. Switching the boot flag turns a complete (bad driver = Blue Screen Of Death) disaster into an easy recovery.

---

### Post by Beruka on 2007-03-11
thanks for the help but reinstalling Ubuntu  is just not an option until I can atleast get the original instal to boot.Thank you for the link. I am working off the firefox on Ubuntu lIve cd right now. 

To clarify the situation. I have two physical sata drives. Ubunutu on one and Vista on the other. I am not incline to give Ubuntu another chance without clearer instructions. The whole point of having two drives is to have a bootable system if one drive fails. This will be a failure with the suggestions given. 

If I had another chance I would have simply unplugged the vista drive, installed ubuntu and then selected boot drive from bios sequence. This is the only way I would permit with this OS again on my machine.

I really need to get Ubuntu to atleast boot from the drive today other wise the live cd will be tossed out and I will be using windows utilities instead. I will unplug the Vista drive and reformat Ubuntu drive to another Vista installation. 


I get the error message on booting Ubuntu of something like 'kernel panic -try running without apic...............' . Then searching the web states disable apic. I have know idea how to make this work.  I tried about 20-30 ways and still get the same error. Just reloading it would be a waste of time.

---

### Post by Beruka on 2007-03-11
Just say no to Ubuntu boot loader and installations with kernel configurations. Not designed for humans.... If I had been more careful I would have unplugged Vista drive first so it would have been left intact. 

My first impressions is that Ubuntu is not well supported by documentation and your on your own to guess at configurations. Advice like turn off apic flag at kernel is mostly useless banter as installations may require bios updates ect.  I don't have much background in Unix line command and don't really want to. I have no issue performing tasks from aline command but why would I want to if alternates are available. It may be more user friendly for older hardware as I easily installed it on a pentium 166 with 256 mb pc-133 ram. It is just too buggy for a 64 bit installation on new mobo.

Any way I had to reload vista on Ubuntu drive, load iso burn utility and then create iso recovery disc for xp and vista. I can then repair damage from Ubuntu boot loader in a sane manner with guessing at unix syntax w/o a manual.

I'll try Ubuntu in the near future if it can load without kernel modifications and my other drive is backed up AND unplugged. I just don't get the fascination at the moment with this OS. My only interest was to work through 'Begining Ruby on Rails Ecommerce' book but it does have windows based alternatives.  My interest was waved off by useless support and lots of bulletins about similiar, almost useful, but in the end different issues to resolve installations.

---

