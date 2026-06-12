---
title: "How to optimize my machine for fast Ubuntu performance"
date: 2009-07-10
forum: Desktop Environments
---

### Post by terry@softreq.com on 2009-07-10
Hello,
I have an Acer desktop with a celeron 2.8 ghz processor.

Just for giggles, I'm trying to optimize this machine so that it's a "sleeper", ie. doesn't look like much but runs Ubuntu blazingly fast (sort of a hobby thing). 

First I increased the memory from 512mb to 2gb and that seemed to help. 

Next I plan to upgrade the video card to a more modern (albeit an AGP card) card with 256mb memory on board. 

Not sure what the best, most cost effective next thing would be to do (I've spent $80 on upgrades, I got this machine for free). 

Should I upgrade the disk to a 10,000 rpm disk?  Replace the current disk with a solid state disk?

What more could I do to really get this machine super fast and responsive?

Thanks, Terry

---

### Post by QIII on 2009-07-10
If what you are doing is disk-intensive, changing to a 10,000 rpm disk might marginally speed read/write times IF your motherboard can handle the traffic.  But your read/write times are probably not going to be a limiting factor if you are not moving a lot of data anyway. 

You would have to consult your motherboard specifications to see if it would even support an SSD.

Your performance will definitely be affected by the type of RAM and it's speed (more capacity is always good), as well as your processor.

I would say the greatest limitation you currently have with making a "sleeper" is the Celeron processor.  I don't know if you could over-clock it and by how much before you cook it.

Probably not worth the risk.

---

### Post by jerrrys on 2009-07-10
take all of this with a grain of salt...

[http://ubuntudemon.wordpress.com/2006/07/14/desktop-performance-tweaks/](http://ubuntudemon.wordpress.com/2006/07/14/desktop-performance-tweaks/)

[http://ubuntuforums.org/showthread.php?t=1179967](http://ubuntuforums.org/showthread.php?t=1179967)

[http://www.cyberciti.biz/faq/cpu-usage-limiter-for-linux/](http://www.cyberciti.biz/faq/cpu-usage-limiter-for-linux/)

[http://quickstart.freeforums.org/quickstart-download-pics-t2.html](http://quickstart.freeforums.org/quickstart-download-pics-t2.html)

[http://www.tweakguides.com/](http://www.tweakguides.com/)

[http://ubuntu-unleashed.com/2008/03/tweak-ubuntu-boot-speed-and-application-startup-time-with-preload.html](http://ubuntu-unleashed.com/2008/03/tweak-ubuntu-boot-speed-and-application-startup-time-with-preload.html)

[http://www.zolved.com/synapse/view_content/28224/How_to_tune_your_Ubuntu_PC_for_faster_performance_](http://www.zolved.com/synapse/view_content/28224/How_to_tune_your_Ubuntu_PC_for_faster_performance_)

---

### Post by terry@softreq.com on 2009-07-10
I've run Ubuntu "dual boot" mode on my laptop (core duo 2.0 ghz processor with 2gb's of memory) and it's really fast. 

Perhaps the real limit to this machine (the Acer) is it's 533mhz FSB.

Generally I rate machines by their FSB rather than their flat out CPU speed.

However, I'm no hardware expert, so it's just some assumptions I've made.

---

### Post by tgalati4 on 2009-07-10
Install a faster disk drive (WD Raptor would be a good choice).  

If you want fast, run SLITAZ in ram.  Won't get any faster than that.

---

### Post by JohnLau on 2009-07-10
Can you tell us the model of yoru harddisk?

John

---

### Post by raymondh on 2009-07-10
> **terry@softreq.com said:**
> Perhaps the real limit to this machine (the Acer) is it's 533mhz FSB.


+1 .. believing that the bottleneck is in the FSB.

---

### Post by terry@softreq.com on 2009-07-10
Thanks Raymond :) 

The disk is a Hitachi Deskstar (80GB).  Here is the specs:

Deskstar 7K80 hard disk drives specifications

Deskstar 7K80 model summary 	Capacity (GB) 	RPM 	Interface

  HDS728080PLA380 	
80 	7200 	Serial-ATA
  	 
Configuration 	Parallel-ATA 	Serial-ATA
  	  	 
Interface 	ATA 133 	SATA 3.0Gb/s
Capacity (GB)1 	80 / 40 	
Data heads (physical) 	2 / 1 	
Data disks 	1 	
  	  	 
Performance 	  	 
Data buffer2 (MB) 	2 MB 	8 MB (80GB) / 2 MB (40GB)
Rotational speed (rpm) 	7,200 	
Media transfer rate (max. Mbits/sec) 	757 	
Interface transfer rate (max. MB/sec) 	133 	300
Sustained data rate (MB/sec) 	61.1 - 29.6 (zone 0 - 29) 	
Average seek time (ms) (read, typical)3 	8.8

---

### Post by {meecrob} on 2009-07-11
> **raymondhenson said:**
> +1 .. believing that the bottleneck is in the FSB.

+1 FSB

-1 10,000 rpm drive - this is unneeded unless you have a lot of continuous disk activity

-1 SSD - I use an SSD and the performace is terrible compared to my computers running SATA II

---

### Post by QIII on 2009-07-11
SSDs

-1 write fragmentation
-1 read/write cycle wear out

---

### Post by binbash on 2009-07-11
+1 fsb

---

### Post by terry@softreq.com on 2009-07-11
Thanks for your feedback so far. 

On the processor front, will Ubuntu make use of the processing capabilities of a dual core?  of a quad core?

I've always wanted to have a system with near instantaneous response (ie turn on machine and Ubuntu launches in under 3 seconds, click on the Epiphany icon and it launches in .5 of a second, click on a website link and the next page appears almost instantaneously). 

Has anyone approached this level of performance?  What would it take?

Thanks, Terry

---

### Post by raymondh on 2009-07-11
> **terry@softreq.com said:**
> Thanks for your feedback so far. 

On the processor front, will Ubuntu make use of the processing capabilities of a dual core?  of a quad core?

I've always wanted to have a system with near instantaneous response (ie turn on machine and Ubuntu launches in under 3 seconds, click on the Epiphany icon and it launches in .5 of a second, click on a website link and the next page appears almost instantaneously). 

Has anyone approached this level of performance?  What would it take?

Thanks, Terry

Hi Terry,

I've often wondered/dreamt about that.  Quad core power.  Researching it, there really is not much of a difference for everyday stuff.  The power of the Quad (it seems) is when we start to multi-task using resource-extensive apps (i.e. video-editing-while-listening-to-music-with-some-number-crunching-program-running-in-the-background).

[http://www.extremetech.com/article2/0,2845,2178787,00.asp](http://www.extremetech.com/article2/0,2845,2178787,00.asp)

I also say this because of the price delta existing between the 2.  Maybe if quad gets' cheaper, I will consider.

There was a time when I also wanted "the most responsiveness".  Responsiveness is quite subjective, anyway I digress.  In my quest for "instantaneous", I pumped up a Pentium 4 to 3.6ghz combined with a noteworthy Heatsink  (and liquid -cooled, in another instance).  It was fun ... but it did not last long.  I learned that there ought to be a happy medium between "fast" and "stability" and "durability".  That was also when I learned of the importance of having the FSB.  Don't get me wrong, it was a fun project and  I learned a lot.

Some reading material:

[http://www.directron.com/fsbguide.html](http://www.directron.com/fsbguide.html)

Right now, I am happy with what I have.  My test machine has the dual core E8400 (wolfdale, I think) at 3 Ghz and 1333 FSB. I think system clock is at 333 Mhz (but am not sure right now).  Ram is at 4GB and HD is WD 7200.  Boot times are good, responsiveness is there (not instant but no waiting long neither).  Heat is managed (good heatsink) and stability/durability is OK.

For travel, I use an MSI Wind with 2GB, 5400RPM HD, but with OC function up to 24% using the atom processor.

Why not go build one and experiment?  Start with the motherboard and go from there.  It will be fun.

Happy Ubuntu-ing.

---

### Post by TenPlus1 on 2009-07-11
I managed to get a speed tweak by disabling the Tracker applet in Sessions...

---

### Post by Ruhani04 on 2009-07-11
Yes, ubuntu makes good use of a dual core. 
I am running jaunty with a vertex ssd and the system boots up so fast that I hardly see the ubuntu boot screen. According to hdparm I get reads between 170-180MB/s.
Not to mention that the ssd is silent and no heat.
The key in my opinion is to run the OS and programs on your ssd and everything else an a second hard drive to maximize speed. I agree it is not a cheap option but performance has its price.

---

### Post by H3g3m0n on 2009-07-12
The BIOS will always take some time to initialize hardware, and no tweaking will help (unless you replace it, see the coreboot part). You can do things like disable the graphical BIOS logos and stuff to improve the speed by a few seconds. Maybe someone will develop a BIOS that does things in parallel (if they don't already).

You can try doing boot profiling, it analyses the boot up and makes it faster. Pass the 'profile' argument to the kernel in grub). [http://ubuntuforums.org/showthread.php?t=254263](http://ubuntuforums.org/showthread.php?t=254263) Not sure if its still useful, maybe its automagically done after install now. EDIT: Just tried this, it actually increased boot time from 15sec->27sec so its probably useless for people with SSDs.

Try out some lite weight apps instead of the full Gnome/KDE ones, for instance use Fluxbox instead of Gnome, thunar for the filemanager instead of Nautilus, mplayer instead of totem and so on.

If you want to make it boot in 3 seconds your probably going to need a RAID of 2 or more SSDs, or one of the extremely high priced and high performance PCIe ones (I'm not sure if you can boot from them or not). 1 SSD (mines a OCZ Vertex) will boot Ubuntu 9.04 in the 10-15 sec range from a 25-30sec, its fast enough that it doesn't feel like I'm waiting for it to boot.

Also most apps on a single SSD will load almost instantly, Blender is ready to use as soon as I click, Gimp loads in under 2 seconds, OO.org is about 2, Inkscape is around 3 seconds (it seems longer than it should be).

Look at not actually turning off the system, but suspending to ram or hibernating to SSD.

9.10 is apparently going to get a 10 second boot probably using some of the Moblin improvements (which should hopefully be much quicker on my SSD).

You can try compiling all the programs for the specific CPU architecture, Gentoo allows for this. Not sure how you would go about it under Ubuntu.

Another idea would be too look at using Moblin rather than Ubuntu, it is designed for embedded devices and has a very quick boot time.

If you really wanted to go to the full extreme, try looking at CoreBoot. It allows you to replace the BIOS on some systems with a Linux distro. It does require supported hardware, some special equipment like BIOS writers, making your own distro and so on.

---

