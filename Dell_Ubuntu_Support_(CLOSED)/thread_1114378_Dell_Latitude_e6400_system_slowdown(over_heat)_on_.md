---
title: "Dell Latitude e6400 system slowdown(over heat?) on 9.04Beta(x64) and 8.10(x32)"
date: 2009-04-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by d-_-b.za on 2009-04-02
Hi

I'm experiencing a problem with my Dell Latitude E6400 notebook(The one with the Nvida Quadro NVS 160m Screencard) where when I watch a movie or use Firefox, Firebug and Flash. It just slows down to unworkable speed. 

I installed acpi and did a "acpi -t" to get the temperature when it slowdowns and it only reports 44'c. I also installed Mandriva 2009.1 Beta(x64) and it seems to work fine without any slowdown. But with Ubuntu 9.04 Beta(x64) or Ubuntu 8.10(x32) it slows down. So I do believe its a Debian/Ubuntu related problem.

I also tested it using Windows Vista(x64) and Windows XP Pro(x32) and not one of the Microsoft products gives me this problem.

I honestly don't know where to start to diagnose this problem or what I must do next.

So any help will be appreciated and if you need more information just let me know what and I will reply to this thread.

Kind Regards,

---

### Post by moody_mark on 2009-04-03
I probably wont know how to fix your problem, but if you do a "sudo lshw" in a terminal and look for the "DISPLAY" section you should see what drivers its using. I have a E6400 with the intel display chipset and when I try to play an avi file the whole machine stops responding, my lshw shows my display as "UNCLAIMED". No one has yet given me an answer as to what this means, but when Ive seen similar postings on wireless cards "UNCLAIMED" means the kernel hasnt installed any modules or drivers for that piece of hardware i believe.

---

### Post by *Tasman* on 2009-06-19
I've been searching around for an answer to this same problem for some time as well.  I have the same setup as you with my e6400 and after wiping every unnecessary process from the startup group and disabling or setting to manual most trivial processes in the administative tools/services group I was becoming very frustrated.  The slowdown was almost always after a few minutes after powerup and usually after I had been watching video or other graphically intensive stuff.  I tried updating the nVidia drivers, tried looking for all know device conflicts, uninstalling everything that could conflict, ran every scan known to man and still found nothing that would explain the slowdown to a snails pace...

I did find one thing that I couldn't explain either, the system idle process would be at 90-100% with no programs running as the system was lagging terribly, and having the system idle process this high is normal when nothing is running, but it doesn't explain what is stealing all my processing power and making my system slow.  So that's when it hit me, its got to be a heat management issue.  I noticed as well that this issue was almost always while I had the laptop on its docking station (all chipsets run on full power settings when on AC power) and my docking station is located under the surface of my desk when air circulation probably isn't the best.  In addition I am a 24/7 power up type user so I don't routinely power down my laptop unless its going in my shoulder bag.  This contributes ALOT to dust build up on the fans and ventilation grates, thus degrading my machine's ability to rid itself of the performance draining heat buildup.  

I then downloaded a program found free on the web called Speedfan (you can find it easily by searching) and it will be able to show you what the temp readings are in realtime of all the various chips in your motherboard and hard drive and graphics cards.  Quite interesting the results.  almost all of mine were on fire with temps spiking as high as 165deg F.  I am not an expert on this but my understanding is that 120deg is about average with an occasional spike higher for the core processors under heavy load, such as when processing video.  I have now with this new information purchased a heat dissapating pad for my laptop to sit on when in the docking station that has 3 auxillary fans that remove the heat much more efficiently, and I believe this has eliminated the problem.  

My advice to you would be download the speedfan application and report back what your temps are at when you're in the lagging stage....my guess is you're running hot!

---

### Post by squaretie on 2009-08-21
So I ran into this problem today.  First I thought it was virtualbox as its process was hogging the cpu.  Then I thought it was firefox.  Then I noticed I had some papers on top of my laptop (its hooked up to external monitors) that were overhanging the fans on the left.  Oops.  I rebooted and noticed grub was slow.  Grub!  So I rebooted again and went into BIOS.  Yup, that was slow too.

Then I saw the CPU speed... 366Mhz.  Ooops.  The system downstepped its cpu to its bare minimum to cool off.

Five minutes without power cured the issue.  Watch those fans -- side to side cooling.  Have to make sure the intake (right) is clear, as well as the out (left) so the heat doesn't back into itself.

---

### Post by binwiederweg on 2009-09-19
Hey you guys,

I'm planning on buying a E6400. Would you say that it has a general heat problem? Or, in general, how does it work with Ubuntu? Any major things one should know?

What about driver support for bluetooth, wireless, webcam and integrated mic?
Any problems?

Regards,
Philipp

---

### Post by mkrate on 2010-01-13
I experience the same slowdown, and like others noted, it seems to be heat-related. CPU step-down may be a problem, but - if it is - leaving the comp alone for a while (even powered on, but without anything running) should take care of that. 

Could it be possible that CPU knows how to step down, but does not know how to step *UP* correctly (i.e. one can only get slower :) - this may be Ubuntu issue if processor has step-down built in to prevent damage, and expects the OS to bring it back up when possible.

On the other hand, I have 100% CPU usage (on both CPUs, or sometimes alternating) in the 'resources' tab, but most of the times all applications show 0-1% CPU usage (with the system monitor being the 'hog' at 10% or so). Is this really consistent with the processor step-down theory (shouldn't then applications also show high CPU usage)?

The bottom line - if it indeed is a heat issue - stay away from e6400, laptops are supposed to get loud and hot, but not overheated. Great little laptop otherwise!

---

### Post by jartsa on 2010-02-06
This is a known problem for a few Dell models. The problem is not the machine getting hot, but the protection system to engage too early and throttle the cpu, gpu, memory and about everything. The protection system is working at the BIOS level. The present A20 (for E6400) somewhat alleviates the problem and already in A19 some thermal tables were rewritten in the BIOS.

Please have a look at the very extensive discussion in these two threads:
Dell forum: [http://en.community.dell.com/forums/p/19247293/19502938.aspx](http://en.community.dell.com/forums/p/19247293/19502938.aspx)
Notebookreview: [http://forum.notebookreview.com/showthread.php?t=348221](http://forum.notebookreview.com/showthread.php?t=348221)

The solution should be provided by dell with BIOS updates. Here is the first semi-official note from dell:
[http://en.community.dell.com/blogs/direct2dell/archive/2009/12/02/dell-on-laptops-and-throttling.aspx](http://en.community.dell.com/blogs/direct2dell/archive/2009/12/02/dell-on-laptops-and-throttling.aspx)
(This was apparently an attempt by dell to recover from the issue hitting first to some tech web pages and then to slashdot.)

So my advise is to
1. Update to the latest BIOS
2. Make sure that there is no dust blocking airflow (if you haven't opened the case and cleared the dust, there _definitely_ will be a thick layer of stuff blocking the flow! It makes a difference.).

I registered here to write this, because I noticed that not everybody knows this issue by now. So the issue is not a hot laptop, but the system throttling too early, as you can read from the the threads above. Here should be an extensive test report pdf by a user which shows the anatomy of the throttling and that the issue is not high temperatures: [http://www.sigmirror.com/files/44490_iweoz/throttlegate.pdf](http://www.sigmirror.com/files/44490_iweoz/throttlegate.pdf) (the report is 59 pages!)

I notice this issue in my E6400 while playing assault cube (in both Kubuntu jaunty and karmic). Very annoying effect is also the huge latency every time when the system goes through the next step in throttling, since that efects very much online gaming... ;) With the latest bios the notebook is not throttling so easily, and I'm not sure if it has actually throtteld. I've used A20 only a couple of days now. I've got intel GPU, and what I've read, the issue is more prominent with the Windows users. This was actually first post that I saw where linux users were discussing about this (in one of the threads there were also one linux user apparently).

Hope this helps, guys!

---

### Post by davehamptonusa on 2011-05-16
The problem is that the nvidia integrated card/chipset is not properly cooled.  This was the case with its predecessor, the d630 as well.  

No matter how much you engage the fans, they just dont give the nvidia chip the coverage that it needs.  Although a great computer, don't spend too long in any graphic intensive environment.  It just won't hack it.

---

### Post by allsteel on 2012-04-20
I've been using a Dell E6400 with a docking station for close to three years now. I'm currently running Debian Squeeze with backports. The Intel Speedstep, fan control and Nvidia graphics have always had issues. I finally nailed the problems using the following:

    Use the latest BIOS -  version: A32 (02/09/2012)
    Use the latest NVidia drivers - version 295.40
    Load kernel module needed to enable cpufreq scaling - acpi-cpufreq
    IMPORTANT - Disable any script that calls /usr/bin/cpufreq-set

I found that invoking /usr/bin/cpufreq-set will cause the cpus to step down to 800MHz! If you do not invoke cpufreq-set, the default governor (ondemand) works properly.

Lastly, I highly recommend using an external cooling fan. I'm using the Thermaltake Mobile Fan II External USB Cooling Fan P/N - A1888

---

### Post by yell0w on 2012-05-01
Bios A32 fixed the issue for me. (released 4/26/2012)

[http://www.dell.com/support/drivers/us/en/555/DriverDetails?driverId=909TW&fileId=2944386393]("http://www.dell.com/support/drivers/us/en/555/DriverDetails?driverId=909TW&fileId=2944386393")

This version got an updated thermal table which fix the cpu over-throttling issue.

Now my computer temperature runs up to 59oC without any freezing, whereas 45oC+ slowed it down to a crawl before.

---

