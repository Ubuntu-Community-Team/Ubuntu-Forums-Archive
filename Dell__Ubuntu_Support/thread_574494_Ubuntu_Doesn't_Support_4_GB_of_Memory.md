---
title: "Ubuntu Doesn't Support 4 GB of Memory"
date: 2007-10-12
forum: Dell  Ubuntu Support
---

### Post by rozen on 2007-10-12
I have just upgraded my Dell XPS 410 memory from 2 GB to 4 GB and the kernel recognizes only 3 GB. Looking in the Ubuntu Forums I found bug number 74179 which tells me that it is a confirmed bug reported 12/6/2006.  It apparently is related to the fact that CONFIG_HIGHMEM4G doesn't mean 4G and one needs a kernel with CONFIG_HIGHMEM64G enabled.

Does anyone know how I can  fix this problem without  having to rebuild the kernel.  I fear that the kernel configuration step is daunting.

If I have to rebuild the kernel, can someone point me to a good HOWTO?

This bug is pretty surprising since there is so much emphasis on virtual machines combined with really cheap memory.  

Thanks in Advance,
Don

---

### Post by saru411 on 2007-10-12
did you install 64 or 32 bit ubuntu, 32 bit does not support over 3 gb of memory.

---

### Post by Xenaco on 2007-10-13
The 3GB (4GB theoretical) limit is not an Ubuntu limitation it is a 32-bit processor limitation.  You need a 64-bit processor and a 64-bit version of Ubuntu or any OS to avoid this limitation.

---

### Post by Skweek on 2007-10-13
If this is true, (and I have no reason to doubt you) then why is Dell Inspiron 1720 Core 2 Duo upgradable to 4Gb mem?

---

### Post by Lord Illidan on 2007-10-13
> **Skweek said:**
> If this is true, (and I have no reason to doubt you) then why is Dell Inspiron 1720 Core 2 Duo upgradable to 4Gb mem?

For people who use 64 bit operating systems? Both Windows and Linux work in 64 bit. I believe Windows has a hack somewhere where you can use the 4 gb of RAM, but I'm not sure about Linux. Nevertheless, 32 bit has it's own limitations.

---

### Post by Skweek on 2007-10-13
Ah,  Forgive my ignorance, I thought a Core 2 duo was a 32 bit processor(s).

---

### Post by Lord Illidan on 2007-10-13
> **Skweek said:**
> Ah,  Forgive my ignorance, I thought a Core 2 duo was a 32 bit processor(s).

Understandable : [http://en.wikipedia.org/wiki/Intel_Core_2](http://en.wikipedia.org/wiki/Intel_Core_2)

I had the same misconception myself before..

---

### Post by Skweek on 2007-10-13
Hmmm.... I feel a reinstall coming on.  ;)

---

### Post by NotRoot:-) on 2007-10-13
I was not aware of a memory limitation either.  I guess I got lucky by installing 2.5 GB of memory.  My motherboard does support 4GB.

---

### Post by Skweek on 2007-10-13
The fact the the 64bit ubuntu iso is call ubuntu-7.04-desktop-**amd64**.iso doesn't help either.

---

### Post by saru411 on 2007-10-13
its amd64 because amd64 is the name of the technology that was developed by amd.

---

### Post by Squizzle on 2007-10-13
As said above, it's an architectural limitation, not an Ubuntu limitation. 32-bit Windows has the same problem.

---

### Post by rozen on 2007-10-14
The notion that 32 bit architecture will not support 4GB of memory is nonsense!  The 64 bit stuff affects the data paths not addressing. As proof, I installed the 7.04 server system and it recognized 4GB.  But I don´t want to run the server system.

I believe that the way the desktop kernel is built is the reason that it will not recognize 4GB of memory.

Don´t buy 4GB of memory unless you are willing to rebuild the kernel and that seems pretty tricky to me.  I haven´t found a confidence-building tutorial for building the kernel yet.

---

### Post by Lord Illidan on 2007-10-14
> **rozen said:**
> The notion that 32 bit architecture will not support 4GB of memory is nonsense!  The 64 bit stuff affects the data paths not addressing. As proof, I installed the 7.04 server system and it recognized 4GB.  But I don´t want to run the server system.

I believe that the way the desktop kernel is built is the reason that it will not recognize 4GB of memory.

Don´t buy 4GB of memory unless you are willing to rebuild the kernel and that seems pretty tricky to me.  I haven´t found a confidence-building tutorial for building the kernel yet.

Well, I've seen this : [http://www.codinghorror.com/blog/archives/000811.html](http://www.codinghorror.com/blog/archives/000811.html)

It recognised 4GB, but were you able to use them?

---

### Post by saru411 on 2007-10-14
rozen please do some research before you post FUD! Its a well know issue with any 32 bit o/s. sure you might see 4 gb installed but how much can actually be used? here some reading for you. do us a favor and do some research before you post some more ramblings of misinformation.

[http://www.cakewalk.com/x64/whitepaper.asp](http://www.cakewalk.com/x64/whitepaper.asp)

>  More Physical Memory

In current 32-bit processors an application can theoretically utilize a maximum of 2 32 bytes of RAM, or 4 gigabytes (GB).  By default, however, the Windows operating system will give a 32-bit application only half as much, or 2 GB.  This can be increased to 3 GB by setting a "large address aware" bit in an application, a change which actually requires no other coding changes or special work.  So the practical physical memory limit for a 32-bit application is 3 GB.

[http://chris.pirillo.com/2007/08/30/32-bit-windows-and-4gb-of-ram/](http://chris.pirillo.com/2007/08/30/32-bit-windows-and-4gb-of-ram/)

> Getting 32-bit Windows to recognize anything beyond 2GB of installed RAM is a seemingly futile effort. Even if your hardware supports the possibility, the software may hold you back - and performance gains are questionable:

    The reduction in available system memory depends on the devices that are installed in the computer. However, to avoid potential driver compatibility issues, the 32-bit versions of Windows Vista limit the total available memory to 3.12 GB. If a computer has many installed devices, the available memory may be reduced to 3 GB or less. However, the maximum memory available in 32-bit versions of Windows Vista is typically 3.12 GB.

So, people use a PAE switch to get past the imposed 2GB barrier. Here&#8217;s a description of the 4 GB RAM Tuning feature and the Physical Address Extension switch:

    When the /3GB switch is used with Windows XP Professional, with Windows Server 2003, Datacenter Edition, with Windows Server 2003, Enterprise Edition, the /3GB switch works identically across versions. This functionality lets device-driver developers test their drivers in this configuration without having to install one of the Windows Server 2003 products just listed. The user-mode memory space is now limited to 3 GB. 

Sounds good, right? Not so fast:

    The /3GB switch can cause some applications to have problems that are related to address dependencies or to a reduction in kernel space.

Bottom line: if you have 4GB of RAM in your system (or more), and you want to take full advantage of it, start using a 64-bit OS.

[http://en.wikipedia.org/wiki/Windows_XP_Professional_x64_Edition](http://en.wikipedia.org/wiki/Windows_XP_Professional_x64_Edition)

> The primary benefit of moving to 64-bit is the increase in the maximum allocatable system memory (RAM). Windows XP 32-bit is limited to a total of 4 GB, which is, by default, equally divided between Kernel and application usage. Using the /3GB switch in the boot.ini file forces Windows to limit the kernel to the upper 1GB and provides up to 3GB for applications. Windows XP x64 can support much more memory; although the theoretical memory limit a 64-bit computer can address is about 16 exabytes (16 billion gigabytes), Windows XP x64 is currently limited to 128 GB of physical memory and 16 TB of virtual memory. Microsoft claims this limit will be increased as hardware capabilities improve. In practice, most motherboards compatible with 64-bit processors do not support anywhere close to the maximum limit, and often retain the 4 GB limit, though motherboards capable of 8GB are becoming more common.

this was all found on the first page of one google seach. do i really have to go on? or are you going to post something useful rather than your misinformation?

---

### Post by Steveway on 2007-10-14
[http://linux-mm.org/HighMemory](http://linux-mm.org/HighMemory)

---

### Post by saru411 on 2007-10-14
> **Steveway said:**
> [http://linux-mm.org/HighMemory](http://linux-mm.org/HighMemory)

interesting page.

---

### Post by rozen on 2007-10-14
I apologize if I have posted misinformation. 

I did run top and dmesg on the server kernel and on the desktop kernel and here is what I saw:

with desktop kernel:
top:
Mem: 3106588k total, 1642996k used, 1463592k free

dmesg:
[    0.000000] 3200MB HIGHMEM available.


with server kernel:
top:
Mem: 4081920k total, 49712k used, 403220k free,

dmesg:
[    0.000000] 4160MB HIGHMEM available.

It certainly looks to me as though the server kernel finds more memory available than does the desktop kernel.  The difference is nearly a GB.  

I would really like to know what is happening here.  It certainly does confuse me. I merely would like to be able to use all my memory.

I also find the Bug #74179 
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/74179](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/74179)
at least as relevant as quotations based on Windows XP experience. Note that the status of Bug # 74179 is confirmed.

---

### Post by thecure on 2007-10-14
Hmmm. With my XPS410 I have 4 gigs and it is shown on both the 32bit side and on the 64bit side. (I installed another HD with 64 bit which I eneded up only using.) Doesn't your BIOS show 4gigs?

Incidentally, looks like Dell droped the XPS410 Ubuntu off their site.

---

### Post by iMerlin on 2007-10-21
I just reinstalled Ubuntu on my desktop machine with a 64bit version because I read that this was a 32bit problem.

I have a fresh install of Gutsy and it still only recognizes 3GB af my 4GB (as reported by my bios).

Specs:
- AMD Athlon 3000+
- 4GB RAM (4 slots, paired)

I know this is not related to Dell support, but the only descent forum post I've seen about the subject.

---

### Post by tturrisi on 2007-10-21
re RAM in Linux:
I have a notebook w/ 1 GB ram, the swap partition is never ever used.  My other notebook has 2 GB ram and the swap has yet to be used.  In fact, on either notebook, I have never seen RAM usage above 160 MB at any one time.  usually RAM use averages at around 110 MB with several browser windows and email client running.

re 4 GB RAM and Windows XP.

Windows XP 32bit ops sys cannot ever use more than 3.0 GB RAM...period.  Tha's the max it can ever use, even if one applies hacks that get the op sys to see & report that 4 GB RAM is installed.  It's not entirely a 32 bit limitation, it's a limitation by design in XP.   XP 64bit op sys can see, report and use more than 4 GB RAM.

I'd responded to a member at a Windows forum in a thread about XP memory tweaking applications such as CachemanXP.  Here's what I posted:

^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Best to let xp manage memory, 3rd party memory tweakers for xp are unnecessary and often a burden because they too must use memory to work.

Most people don't really understand what memory and how xp manages it.

Here's a quick write up I did for a friend's kid who was tickled when his new 4 GB ram arrived for his gaming pc. (in my original effort to explain to him that the 4 GB won't get used by xp, he felt invalidated, so I clarified it all in an email to him)

Most people, including tech trained, don't really understand how a computer uses RAM and other types of memory. Yes, there are several types of memory.

A normal XP system can have a maximum of 4 GB of installed ram. However, by design, XP will never utilize and cannot utilize more than 3 GB of ram. This is by design, since no one will ever need more than 3 GB of ram in use at one time. Windows XP 64 bit edition can use 128 GB or ram, as can some server operating systems use terabytes of ram. The home or office workstation will never need more than 3 GB of ram, no software or games will ever require that much ram in XP.

XP won't even recognize if 4 GB of ram is installed, it will report anywhere from 2.5 GB to 3.5 GB of installed ram. This, apparently abberated, is by design (actual). This leads to the second type of memory a computer uses.

XP automatically sections off a part of the hard drive to be used exclusively as "virtual memory" called the "page file". The amount of virtual memory (page file) is automatically set at 1.5x the amount of installed ram. The size can be adjusted by the user via a XP advanced settings dialog.

**keywords:**
page - a fixed number of bytes recognized by the operating system.
address - A location of data, usually in main memory or on a disk. You can think of computer memory as an array of storage boxes, each of which is one byte in length. Each box has an address (a unique number) assigned to it. By specifying a memory address, programmers can access a particular byte of data.
address space - The set of all legal (allowed) addresses in memory for a given application. The address space represents the amount of memory available to a program.

When the computer is booted, essential operating system programs and files are loaded into ram. When a program is run, only the necessary parts of the program are loaded into physical ram, meaning only those parts of the program which are currently active. The rest of the program gets loaded into virtual memory (the page file). These parts of the program are stored in ram or on the disk in sections. Each section has an address.

For example, one loads a Word document and the text, window decorations, menus, etc. are loaded into ram, but all else (such as Word Help program) is loaded into virtual memory (page file). What you see on the screen is in ram, what you don't see is in the page file (virtual memory). When the user attempts to use a currently inactive part of the program, such as Help, the program "interupts" memory and the operating system reaches into virtual memory (page file) and "pulls" the Help program into physical ram, and puts other programs' components into virtual memory. This is called "swapping" or "paging".

The program tells the operating system, "I need the Help program located at address 4". This is known as the program generating what is called a "page fault". Because Help is not located in ram at address 4, the operating system looks to virtual memory for address 4. This all goes on invisibly and smoothly. A page fault is not a bad thing.

When the program's code (instructions) are corrupted/damaged or poorly designed, and the program generates a page fault, and "address 4" cannot be located by the operating system, you get what is knows as an "invalid page fault". I think everybody has seen an error message at one time or another: "xyz.dll caused an incvalid page fault at address 000xxxxxx."

**How does this all apply to XP?**

Now, by design in XP, the maximum amount of virtual memory (the page file) that can be used by any one program is 2 GB. Therefore, the maximum amount of physical ram that can be used by one program is 2 GB, this is so "paging/swapping" has the potential to "add up". Since 2 GB will never be needed by any single program of a home or business workstation, this is all fine and dandy.

Will installing 4 GB of ram improve the computer's performance? Yes, potentially.

Will the XP operating system ever use the full 4 GB ram? No, it cannot use it, by design.

Then what is the benefit of having 4 GB ram? An XP file can be edited that changes the "max use of the page file by one program" from 2 Gb to 3 GB. And since certain types of ram perform best when installed in "matched pairs", using 2 pairs of 1 GB ram modules will perform better than using 3 GB of ram (3 modules). Thus the performance increase is noticed "in speed of page faults", meaning the inactive parts of a program get loaded faster when the program requests them.

**Caveats:**

Since the page file (virtual memory) is located on the hard drive, then performance is also dependant upon the speed and qualities of the drive, despite having a lot of ram. XP will always use virtual memory. The user cannot instruct XP when and what is to be paged, or what is to be put in or out of virtual memory.

However, the user can turn off the page file completely and force XP not to use a page file at all. Doing so requires the computer have a lot of ram, at least 2 GB. The computer will perform just fine and invalid page faults will not be encountered, provided the user is not doing heavy multi-tasking, meaning the computer has enouh ram where ALL the programs' active and inactive components can be loaded.

When the page file is enabled, XP will "swap" data back and forth between the page file and ram, even if the computer has enough ram that a page file is not needed. The user cannot control this activity. This is visible by observing the led lights on the computer. There's usually a light that indicates hard drive activity. One will see this light blink from time to time even when one is not interacting with a program. Sometimes you can even hear the hard drive making noise when this occurs.

**32bit or 64bit operating systems:**

XP is a 32 bit operating system. A program instruction can address up to 4GB of memory, using its full 32 bits. (The 32nd exponent of 2 is exactly 4,294,967,296, or 4 GB.

Newer Intel and AMD processors have support far more than 32 bits (2 to the 64th power). Thus there exists 64bit versions of XP and other operating systems. A program installed on such an operating system can address much more than 4 GB, thus more ram can be installed and more ram can be used by the operating system. However, the program must be coded with 64bit support, and most software is coded only for 32bit support. Thus, it does not pay to use a 64 bit operating system because the only software that will utilize the potential performance increase are specialty software, such as server software, databases and certain software that is used to build new software.

**What's the bottom line?**

There's nothing wrong with having 4 GB ram. If anything, it's just nifty kewl to be able to say "I have 4 GB ram!"
Vista operating system is also limited to the same memory restrictions as XP, but future changes to Vista may include support for the full 4 GB ram

---

### Post by rozen on 2007-10-21
I too just installed the 386 Gutsy Desktop Version. It only recognized 3GB of my 4GB.  So I recompiled the Kernel with CONFIG_HIGHMEM64G=y and that kernel does recognize 4GB on my machine.  It appears that CONFIG_HIGHMEM4G really doesn't mean 4GB after all.

Here are some of the data points:

With my kernel configured with CONFIG_HIGHMEM64G=y

top command:
Mem:   4081788k total,   378372k used,  3703416k free,    12120k buffers

dmesg command:

[    0.000000] 4160MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.

KInfoCenter:
Total physical memory 4179750912 bytes = 3.89 GB


With my kernel configured with CONFIG_HIGHMEM4G=y

top command:
Mem:   3106456k total,   361136k used,  2745320k free,    12132k buffers


dmesg command:

[    0.000000] Warning only 4GB will be used.
[    0.000000] Use a PAE enabled kernel.
[    0.000000] 3200MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.


KInfoCenter:

Total physical memory 3181010944 = 2.96 GB


I think that this is really important because of the popularity of virtual machines.  I want to run XP in a virtual machine; that is why I went to 4GB of memory. The additional 2GB of memory cost only $40 after rebate.  So a lot of people will be doing the same thing.

---

### Post by misfitpierce on 2007-10-21
Need that 64 bit :)

---

### Post by blakeg on 2007-10-28
I would like to add to this conversation and also ask a question.

64bit seems to be the best way to use all of 4gb+ but it seems that the 64bit ubuntu isnt quite ready for primetime yet... 

From what i've seen, it needs some work. Am I right or wrong about that one?

BlakeG

---

### Post by tturrisi on 2007-10-28
Also, FYI, -686 kernels can use up to 4 G RAM, -386 & -486 kernels won't.

---

### Post by cooliohus on 2007-11-02
I just saw this thread and would like to offer the following Windows related information.  32-Bit Windows machines can utilize more than 4GB of memory - I believe the supported limit on Enterprise edition is currently 32GB.  The confusion may be that any given process cannot exceed 3GB.

There are two configuration options involved.  The PAE switch enables large memory support (changes page size from 4K to 4M I think??) and the 3GB switch changes the per process limit from 2GB to 3GB.  The upshot is that a 32-bit machine with 16GB of memory can [simplistically] have 32 2GB processes running without paging.

I am memory poor so I haven't had to look at Ubuntu memory configuration options but I would assume the equivalent PAE and 3GB settings would exist in the 32-bit world

---

### Post by tturrisi on 2007-11-02
> **cooliohus said:**
> I just saw this thread and would like to offer the following Windows related information.  32-Bit Windows machines can utilize more than 4GB of memory - I believe the supported limit on Enterprise edition is currently 32GB.  The confusion may be that any given process cannot exceed 3GB.

There are two configuration options involved.  The PAE switch enables large memory support (changes page size from 4K to 4M I think??) and the 3GB switch changes the per process limit from 2GB to 3GB.  The upshot is that a 32-bit machine with 16GB of memory can [simplistically] have 32 2GB processes running without paging.

I am memory poor so I haven't had to look at Ubuntu memory configuration options but I would assume the equivalent PAE and 3GB settings would exist in the 32-bit world
The max for XP is still 4GB, though all 4GB can never everf be used at one time.
[http://www.microsoft.com/whdc/system/platform/server/PAE/PAEmem.mspx](http://www.microsoft.com/whdc/system/platform/server/PAE/PAEmem.mspx)

---

### Post by jimbo2150 on 2007-11-02
> **blakeg said:**
> 64bit seems to be the best way to use all of 4gb+ but it seems that the 64bit ubuntu isnt quite ready for primetime yet... 

From what i've seen, it needs some work. Am I right or wrong about that one?

Correct. I was running 64-bit Ubuntu for about a month. Even though it works well with most programs, getting things like web Java applets to run is near impossible unless you spend the time uninstalling firefox and installing the 32-bit version along with the 32-bit version of Java with the plugin. Same with Flash. The nswrapper has some major issues yet and often crashes and is not really compatible at all with the upcoming release (Movie Star). Installing 32-bit Firefox, once again, fixes this but is a bit of a pain. 32-bit packages are not offered in the reps in 64-bit Ubuntu.

Other than that, most other programs will work, but you are a bit limited as many older programs that are compiled on 32-bit but are no longer developed are not available in the 64-bit reps, so there are a few less packages (application) available through the reps compared to the 32-bit version.

Most claim that it is because the lack of performance increase between 32 and 64 but, as we see in this post, people are running into memory limitations. Oddly enough there doesn't seem to be much of any push overall to get people moved over to 64-bit or to get the remaining programs (like Flash / Java plugins as well as some other apps/drivers) ported to 64-bit. Even the M$ deadline for 64-bit support is fast approaching and many Winblows developers, from what I have heard, who make drivers, codecs, and programs are not even thinking of moving to 64-bit.

As for now, I am sticking with 32-bit until better support comes for 64-bit, but I will continue to advocate the importance! :)

---

### Post by bluedragon436 on 2007-11-03
I was thinking the same thing that I know has been said before is the computer upgradeable to 4gb???  I have a D610 and am getting ready to see if it will support 3gb, and hopefully it will...I mean it runs quite well with just the 1.5gb's it has now....but that was one thing i was worried about was what the max amount of memory Ubuntu will support....I am hoping your issue isn't an Ubuntu issue, as I am looking to go to four gigs on my desktop a bit later

---

### Post by rozen on 2008-02-02
Latest report describing how I got 32bit version of the system to recognize my 4GM of memory.

I installed the 64bit version and ran it for a while but stopped for the same reasons stated by jimbo2150 in # 28 above.  I then rebuild the kernel from the 32bit sources. I configured the build to use CONFIG_HIGHMEM64G. It took about 40 minutes to build and install the system.  

I have been using that kernel for about a month without seeing any problems and it does indeed recognize my 4GB of ram.  The Windows, XP, and architecture arguments posted above seemingly do not apply.

By the way, I saw on Slashdot that Vista does not recognize 4GB and it is considered a bug.  The fix reported is to change the message to report the amount of memory installed rather than the amount recognized.

Thanks for your indulgence,
Don

---

### Post by dschaller on 2008-02-05
rozen, If you would, I'd like to see a little more detail on how you compiled and installed that kernel. I haven't had the nerve to try it yet, but I do think you have the correct solution.

---

### Post by Truin on 2008-02-06
[http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

You can find from the address above, memory limits after kernel recompiling if your cpu is newer than Pentium Pro and Athlon
Then again I doubt that you would pump a rig with older processor with 4+ GB ram :)
It's actually as high as 64 GB due to PAE:s ability to increase physical memory address size from 32-bits to 36-bits.

---

### Post by rozen on 2008-02-08
In response to dschaller, some notes on my building of the kernel.

I didn't have too much trouble building the kernel but there were a couple gotyous.  I will point them out.  I acknowledge that I am not an expert. You can probably get better advice elsewhere.

Basically, I followed the steps outlined in the web pages:

[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

and 

[http://www.beginlinux.com/index.php/desktop_training/ubuntu/ubfile_m/ub_compile](http://www.beginlinux.com/index.php/desktop_training/ubuntu/ubfile_m/ub_compile)


The most confusing part is the kernel configuration. This step is done with the command:

make menuconfig

The main thing I wanted to do was set the High Memory Support.

Processor type and features >  High Memory Support > 64GB

Gotyou 1. After I built my first kernel there was no sound.  My machine has onboard intel sound support and I found that it was necessary to include that in the kernel configuration

Navigate to Device Drivers > Sound > Advanced Linux Sound Architecture > PCI Devices. Select Intel HD Audio and press M. 

(As an aside, I think that the kernel source distribution should include the configuration file used to build the kernel.  Since the distributed kernel supports Intel HD Audio they just shipped a configuration file they had lying around.)


Gotyou 2. When you try to bring up the new kernel, remember that it will not have any proprietary modules like, for instance, the nvidia driver.  So if your /etc/X11/xorg.conf calls for a proprietary graphics driver, it won't come up.  So go into /etc/X11/xorg.conf and make sure you are not calling for a proprietary graphics drive. In my case I changed :

Driver		"nvidia"

to 

Driver      "nv"

booted the new kernel and then installed the proprietary driver.

---

### Post by dschaller on 2008-02-13
rozen, thanks for the reply. Were you able to install the proprietary nvidia driver with your new kernel? I thought maybe any external drivers would have to be built from source to match the new kernel.

---

### Post by rozen on 2008-02-13
I downloaded the latest driver, 169.09, from the NVIDIA site and installed it from a console session and am using it now with my 64GB kernel which recognizes my 4GB of memory.  The last time I tried suspend/resume were even working.  This is the happiest that I have been with Gutsy.

---

### Post by irwinr on 2008-04-22
I am blown away at just how many people continue to spread the misconception that 32 bit has a 2GB or 3GB or 4GB limitation. (The limit seems to change from forum to forum too.)

THIS IS NOT TRUE!

32 bit Linux and Windows can address up to 64 GB of memory using Physical Address Extension.  Physical Address Extension, or PAE, increases the address space the CPU can use up to 36 bits.  2^36 = 68,719,476,736 or 64GB

The '32 bit limitation' ONLY applies to individual processes running within the system.  So yeah, Firefox can only address up to 4GB of memory, but if you had 64GB of RAM total, you could have up to 16 different processes running, each using it's full 4GB of memory (in theory, it's actually less than 4GB, but how much less depends on whether it's Windows or Linux, and even in Linux it depends on which kernel and how it's configured.)  But regardless of what each individual process can use, the entire system can certainly support up to 64GB of memory without needing a 64 bit OS.

So rather than accusing people of spreading FUD when they say their systems can handle 4GB of memory, why not do a bit of basic research before attacking them?  Or better yet, try to help them rather than tell them they need to upgrade to a 64 bit OS, which is simply not true.  I've seen dozens of 32 bit Windows server machines running with 64GB of memory.

Windows XP and Windows Server Standard Edition are limited to 4GB of memory, but not because they are 32 bit.  Microsoft disables PAE on these versions so they can charge more for the higher end server versions.  

Linux on the other hand only needs a kernel configuration option set to enable PAE and address up to 64GB.

-Jeremy

---

### Post by pzearfoss on 2008-04-24
Hello all, I tried recompiling the kernel to see my 4GB.  The recompiled version still shows only three.  I also tried a suggestion on another thread about recompiling grub to handle this.  Still no luck.  

As far as I know I did everything correctly.  Anyone have any thoughts as to what more I can do?  I'll be happy to post any configs or anything here.

---

### Post by Outworlder on 2008-05-02
> **irwinr said:**
> I am blown away at just how many people continue to spread the misconception that 32 bit has a 2GB or 3GB or 4GB limitation. (The limit seems to change from forum to forum too.)

THIS IS NOT TRUE!

32 bit Linux and Windows can address up to 64 GB of memory using Physical Address Extension.  Physical Address Extension, or PAE, increases the address space the CPU can use up to 36 bits.  2^36 = 68,719,476,736 or 64GB

The '32 bit limitation' ONLY applies to individual processes running within the system.  So yeah, Firefox can only address up to 4GB of memory, but if you had 64GB of RAM total, you could have up to 16 different processes running, each using it's full 4GB of memory (in theory, it's actually less than 4GB, but how much less depends on whether it's Windows or Linux, and even in Linux it depends on which kernel and how it's configured.)  But regardless of what each individual process can use, the entire system can certainly support up to 64GB of memory without needing a 64 bit OS.

So rather than accusing people of spreading FUD when they say their systems can handle 4GB of memory, why not do a bit of basic research before attacking them?  Or better yet, try to help them rather than tell them they need to upgrade to a 64 bit OS, which is simply not true.  I've seen dozens of 32 bit Windows server machines running with 64GB of memory.

Windows XP and Windows Server Standard Edition are limited to 4GB of memory, but not because they are 32 bit.  Microsoft disables PAE on these versions so they can charge more for the higher end server versions.  

Linux on the other hand only needs a kernel configuration option set to enable PAE and address up to 64GB.

-Jeremy

Also, Vista can only use *up to* 4GB. In reality, the available memory will probably be less than that, since drivers are mapped in the 4GB address space. That also includes your video card memory.

And that's with PAE.

---

### Post by andydread on 2008-05-19
My question is why the limitation in ubuntu?  On can easily do 

apt-get install linux-image-bigmem in Debian and this Kernel was available with earlier versions of Ubuntu.  So who's smart Idea was it to remove it?  
It seems the ubuntu people think that only servers need 32bit and >4GB support.   Workstations be dammed, they have to use 64bit and deal with flash and skype issues along with all the apps that you have to fiddle with to get going under 64bit.  This is a terrible oversight.  I cannot find one reason for not providing a 32bit Kernel with >3BG support.  Even Debian does it..

---

### Post by cscutt on 2008-05-19
Memory Limitation is not part of the Distro ( Ubuntu ) but how that distro may have compiled Linux ( linux-image-2.6.2x....). Linux that OS that the Ubuntu distro is based on does indeed support upto 64G of memory in it's raw x86 form with the use of bounce buffers, also know has High-mem support in the kernel config. You do not have to run an amd64 ( X86_64 ) version of distro to see the 4G of memory, however there are many limitation that drain a system using bounce buffers, but since your using a desktop system and probably not doing graphics intensive things, you should never see them. Best advice for users of bounce buffers, make sure your BIOS is up to date, and watch that microcode.

---

