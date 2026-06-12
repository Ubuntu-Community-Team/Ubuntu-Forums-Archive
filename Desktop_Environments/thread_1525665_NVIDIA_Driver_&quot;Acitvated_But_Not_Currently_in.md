---
title: "NVIDIA Driver &quot;Acitvated But Not Currently in Use&quot; Status Restricting Lucid"
date: 2010-07-07
forum: Desktop Environments
---

### Post by casparov on 2010-07-07
Hi, Everyone...  

I have had my share of trials w/ video in Lucid, but, overall, am very pleased w/ the OS.  

However, a current problem is restricting the ability of the PC to utilize certain features, which are only available through the installation of proprietary drivers.  For instance, I cannot run several Windows-based programs in WINE, given these limitations.

System-->Administration-->Hardware Drivers searches the system for drivers then produces the result: Current NVIDIA driver activated but not currently in use.  The resulting window allows an option to deactivate the driver, but I don't know how to go about installing the proprietary driver after this.  Does anyone have an idea how to resolve this?

I would greatly appreciate any insights pertaining to this issue. Many thanks to everyone who bothered to read and/or contribute to this post.  

C.

---

### Post by mikewhatever on 2010-07-07
What's the output of **sudo lshw -C display**?
Do keep in mind that some Windows programs will not work in wine regardless of the drivers you install.

---

### Post by exploder on 2010-07-07
I had massive issues with NVidea and the Lucid base. The solution was to install the 2.6.35-6 kernel, NVidea 256 drivers and turn off the disk check in /etc/fstab. Also, installed Compiz 8.6 from the ppa repo for good measure.

I had the issue where the mouse would move but nothing would respond and the system was going into low graphics mode pretty often. After 2 days of reading and experimenting I found that all of the above mentioned changes resolved all of the issues.

My computer has been running for two or three days without a single problem. I would provide links to where all of the packages I mentioned are but the site I posted all of the information on is down..... A few google searches should quickly provide all of the necessary ppa repos needed though. 

You will have to adjust plymouth to the proper resolution after making these changes.

---

### Post by Frogs Hair on 2010-07-07
Having the same issue here , Nvidia X server settings say I'm using 256.35 and there are no other drivers are installed I verified this via the synaptic pkg. manager   . My Compiz extra plugins from the PPA are all working .

When I try to use the command supplied by Mike whatever , I receive a command not found message . Every piece of monitoring software says I'm using the 256.35 driver except the hardware and driver jockey. PS: I am not running wine 
and have full function unlike the OP.

---

### Post by Frogs Hair on 2010-07-07
My issue began 7-6 2010 with kernel update  2.6.32-24 .

---

### Post by exploder on 2010-07-07
> My issue began 7-6 2010 with kernel update 2.6.32-24 .

I have had this issue from the beginning, it became very frequent with the stock updated kernel. The steps I mentioned earlier make the system stable and predictable.

Found the ppa for the new kernel!

[https://launchpad.net/~kernel-ppa/+archive/ppa](https://launchpad.net/~kernel-ppa/+archive/ppa)

Here is where to get the nvidea packages.

[http://www.ubuntuupdates.org/ppas/27](http://www.ubuntuupdates.org/ppas/27)

Edit: Here is how to upgrade compiz.

[http://www.webupd8.org/2010/06/upgrade-to-compiz-086-in-ubuntu-1004.html](http://www.webupd8.org/2010/06/upgrade-to-compiz-086-in-ubuntu-1004.html)

---

### Post by Frogs Hair on 2010-07-07
> **exploder said:**
> I have had this issue from the beginning, it became very frequent with the stock updated kernel. The steps I mentioned earlier make the system stable and predictable.

Found the ppa for the new kernel!

[https://launchpad.net/~kernel-ppa/+archive/ppa]("https://launchpad.net/%7Ekernel-ppa/+archive/ppa")

Here is where to get the nvidea packages.

[http://www.ubuntuupdates.org/ppas/27](http://www.ubuntuupdates.org/ppas/27)

Edit: Here is how to upgrade compiz.

[http://www.webupd8.org/2010/06/upgrade-to-compiz-086-in-ubuntu-1004.html](http://www.webupd8.org/2010/06/upgrade-to-compiz-086-in-ubuntu-1004.html)

Two of the three ppa's are currently in place on my computer  but have not tried the kernel yet.

---

### Post by casparov on 2010-07-07
Mike...

Here is the terminal text that you requested:

(My continuing appreciation is extended to all those reading and posting--I will investigate those other leads suggested this evening.)

C.

P.S.:  I am v. cloudy about what I run on this machine, but I don't believe it is supposed to be 64-bit anything.  Is that correct?  C.
[Addendum: After reviewing this link, [https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit), it appears that I don't have a problem there--just thought that it may have a bearing on things, somehow.]


*-display               
       description: VGA compatible controller
       product: G86 [GeForce 8400 GS]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: a1
       [COLOR="Blue"]width: 64 bits[/COLOR]
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:24 memory:fa000000-faffffff memory:c0000000-cfffffff memory:f8000000-f9ffffff ioport:bc00(size=128) memory:fb000000-fb01ffff

---

### Post by Frogs Hair on 2010-07-08
Hello casparov,

I have filed bug report # 602876 @ launchpad .net regarding the driver activated but not in use message . In my case the driver is working because there is no other driver installed. Feel free to add a comment to the report if you see fit. At least I will have confirmation of the message.

---

### Post by casparov on 2010-07-08
Frog...

That's terrific--I really appreciate it.  

The danger for me is that, if I go swimming around changing my kernel (and I've tried that, already--using *.34) and things, I reach the event horizon for my Linux aptitude in a nano.  

Thanks so much,

C.

---

