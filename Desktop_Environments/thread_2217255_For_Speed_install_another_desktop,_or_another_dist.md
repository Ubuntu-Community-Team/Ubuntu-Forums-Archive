---
title: "For Speed: install another desktop, or another distro?"
date: 2014-04-16
forum: Desktop Environments
---

### Post by Ace..... on 2014-04-16
My laptop is sluggish.

Ubuntu 12.04 LTS
AMD dual-core C-50
AMD Radeon HD6250
3Gb DDR3 memory
5Mbps internet connection

I believe it all started when I upgraded to v12.
Everything ran slower.... software centre typically 'clouds over' and hangs for a few seconds before continuing to load.
Open a few tabs in chrome and scrolling becomes a nightmare.

I installed system-monitor, and noticed that my memory and swap graph barely budged from 55% and 7% respectively whatever I did..... meaning that there were no wild swings - open another tab ....... a bit more memory is used.

However, the CPU shoots straight to 100%

Simply scrolling through the youtube.com standard page of thumbnails pushes cpu usage to 100%, and the page doesn't even scroll smoothly.

Should I be running a different distro, or is it the desktop, or does it look like my system has some issues?

---

### Post by baphomet2 on 2014-04-16
One thing right off the top is cutting down on the swap usage:  Edit /etc/sysctl.conf and add these lines to the bottom of the file 
vm.swappiness=10
vm.vfs_cache_pressure=50

You could also try switching to xubuntu.  It is less resource intensive and you don't have to reinstall from scratch.  Run - sudo apt-get install xubuntu-desktop After that you can select which interface you want from the login screen so you can fall back to Unity if you don't like XFCE.

---

### Post by Ace..... on 2014-04-16
Okay.... have downloaded xubuntu desktop and am now running with it.

1. It is faster.... youtube can now run at 480 without stuttering.
It still struggles with 720, but is better than when running ubuntu.

2. I note that gnome-system-monitor shows itself to be taking up to 98% of CPU resources, or as little (?) as 25%.

(I have no idea how a system monitor can function as a monitor if it consumes such resources - when running, youtube stutters at 480!).

3. However, system monitor did highlight lots of unneeded progs running eg. ubuntu 1, and bluetooth.
It seems that xubuntu has better setup options - as in ubuntu, these items were set to off (in settings) yet I'm sure they were running.
Xubuntu has a startup config that I never discovered in ubuntu (even though I looked for it).

None of the progs are consuming cpu resources, only memory, and that doesn't seem to be my problem (but I'll switch them off).

4.  I failed to edit [COLOR=#000000]sysctl.conf - could you remind me how to disable its 'read-only' status?
It was currently set to swappines = 20
no '[/COLOR]vm.vfs_cache_pressure' existed.
[COLOR=#000000]
Overall, I think your advice has proved positive :)

I still think something is amiss - perhaps swappiness and cache pressure will again improve the situation.

On another note.... I noted for the first time [/COLOR]:redface: that there are a number of desktop options available.
[COLOR=#000000]
Ubuntu 2D
XMBC
XFCE session
Xubuntu session

Leaving aside XMBC.... which do you think should be the fastest?


I'm also wondering whether my display system is set up for optimum performance.
Failing to run BBC Documentaries at 720 is surely a fail for an HD enabled pc?

However, I am pleased with the progress so far..... perhaps there's more to come [/COLOR]:D[COLOR=#000000]

[/COLOR]

---

### Post by buzzingrobot on 2014-04-16
Look for alternative apps that use less memory and less CPU.  Many are more demanding than any interface or the underlying OS.

---

### Post by baphomet2 on 2014-04-17
Very cool.  I'm glad that I finally helped someone.  :)

So to edit the systcl.conf here are the steps:  
1.  sudo vi /etc/sysctl.conf 
2.  when you are done editing hit ESC then :wq!    (the bang (!) is what overrides the read-only state)

Not sure if you are fluent in vi.  If not let me know and I can type up the shortcut keys you need.  

As far as sessions are concerned my favorite is the XFCE session.  Here is a very good website to go through to make some more tweaks/get better performance out of xubuntu - [https://sites.google.com/site/easylinuxtipsproject/first-xubuntu](https://sites.google.com/site/easylinuxtipsproject/first-xubuntu)  

You don't have to do everything on that site, but there are some good steps like the swappiness, speed up wireless, speed up Firefox, etc.  

For help with your display you can run "lspci | grep -i vga" from the command line so we can be sure what video card you have and then check to see if you have the appropriate driver/module installed.

---

### Post by grahammechanical on 2014-04-17
I think that it is misleading to expect things to get faster if we install an alternative desktop. Install the full flavour - Xubuntu or Lubuntu. Alternative desktops add more code and increase the possibility of conflicts between the scripts that each desktop uses.

Oh, by the way, we may be pleasantly surprised by how better Ubuntu 14.04 is with the use of memory and CPU resources when compared with 12.04. It frees up memory much quicker. With my Intel Core 2 Duo 2.40 GHz CPU it uses both cores instead of just alternating between cores. I have only 1 GB of RAM and I have no complaints with how Ubuntu 14.04 is running on this machine. I think the amount of video memory has an important effect on our user experience.  I would say that 1GB of discrete video memory is necessary for a good visual user experience.

Regards.

---

### Post by baphomet2 on 2014-04-17
I do agree with what grahammechanical says.  My original advice was so you could try out xubuntu with the ability to back out if you didn't like it.  Now that you know you like it I would do a clean install of Xubuntu 14.04 LTS and go from there.

---

### Post by Ace..... on 2014-04-17
Thanks for the interest, everybody :)

**Points to note:- **


[LIST=1]
[*]It is extremely difficult to make specific comparisons, without a standard test that can be actioned in each distro/desktop (with log output).
[*]Grahammechanical raises the issue of 'adding desktops (code)' - I do note that baphomet2 accepts this....... I would say that in fact baps' original advice did pay dividends, in terms of introducing me to a whole new layer of ubuntu usage. However, there are clearly issues that arise from this testing of desktops on top of prime installed ubuntu.

Therefore; in this rare instance.... both positions taken, appear to be correct. :shock:
[/LIST]

[SIZE=3]**Back to the core thread:**[/SIZE]

**Regarding speed** - circumstances take over:


I also tried xfce and stupidly tried the option 'save session'.
I am guessing that this is what is preventing me from loading xubuntu.


I can load ubuntu 2d (am now working in 2d), but choosing xubuntu simply loads the 'saved session' dialogue box and XFCE is loaded.
IE. I can no longer test xubuntu!


Could this be a 'fun rivalry' thing, with XFCE getting one over Xubuntu?
I'd like to think so :)


Either way.... the joke is over, and I'd like to spend some time with Xubuntu if that is at all possible :)
However I must say... XFCE was pretty amazing, vis a vis enabling the user to setup an efficient work environment.
Speed arises, not only from raw computing power, but clearly also from desktop dynamics.


Having the 4 workspaces accessible from the menu bar, has opened up a whole new world of dynamic productivity.... if only the '2 monitor display' worked as it does in ubuntu and 2d.


Bizarrely, on XFCE both monitors (laptop and monitor) display the same image.
Here on Ubuntu, I have 'reference data' on one screen, while entering 'this' text on the other.
How is it possible that XFCE failed to offer 2 monitor desktop space, after it had offered so many useful customisation options????

**The Raw Computing speed:**

I managed to edit the sysctl.conf file.
As stated above.... hard to know for sure, but it 'seems' better, though being locked in to XFCE, maybe 'this' was the fix?
I was able to run chrome with 50 tabs open, without problem - note I was not running any video apps.

This leads me to believe that the problem is with the graphic display drivers for my 'Radeon HD 6250' graphics card.
Having browsed around the forum, I get the feeling that my Radeon HD 6250 graphics chip, may not be fully supported by my current drivers.
It works..... but without accessing the chip's full potential.

I loaded : [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

However to even try another driver, appears to be a highly complex and risky manouver, with [https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection#Problem:_Need_to_purge_-fglrx](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection#Problem:_Need_to_purge_-fglrx) listing 11 separate potential pitfalls, simply by purging ones existing drivers.

So I jumped that, and ran: ```
man radeon
```
This displays an enormous number of adjustable options for Radeon HD 6250 (around 60 config options).
Wow, I wish I truly knew what each option did (a good explanation accompanies each option, however this requires that you understand the explanation - many of which I didn't).

I figured that this was the moment to sit back and reflect on what had been achieved.
I was much further ahead than when I started.
Hopefully there is a way to stop XFCE from shafting Xubuntu. ;)

However, this is definitely a case of 'the performance potential is there'... "I want you"..... but I can't have you.
I can live with that.
480 on youtube is fine for the laptop. :)

Time for a glass of wine, and a video youtube test, with Elvis Costello "i want you" live at the Tim Festival.

His interpretation of our (my) angst is perfect, when related to PC problems. :)

.............. actually........... PC problems have gotta be far worse.   :cool:

---

### Post by baphomet2 on 2014-04-18
Glad to hear that you are having some great success and fun with the different desktops.

For your display.  I've tried both the repository fglrx drivers and the one direct from the AMD support website.  Both functioned just fine for me and I really didn't see a difference.  I would wipe out the driver you put in and go with the fglrx drivers.  Of course it is risky, but is well worth it if it works.  After that you can install the Catalyst Control Center.  (sudo apt-get install fglrx-amdcccle)  With the Catalyst Control Center you can configure the monitors for Spanning/Mirroring/etc.  All the stuff you get with any other OS/desktop.  I was able to setup XFCE with 2 monitors spanned at 1920x1200 resolution and didn't see any performance issues.  It does suck that XFCE/xubuntu does not do that natively, but at least there is a way.  

There's more information on installing fglrx drivers here - [https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)  

I haven't run into the issue of not being able to get back to xubuntu so I won't be a lot of help there.  

Good luck and I hope you enjoyed your wine.  :)

---

### Post by Ace..... on 2014-04-22
Yes, thanks...... the wine was very nice.
It should be written into the manual, that there are moments when you need to stop further work; reflect on what you've achieved; and then take a break.

The dual monitor fix came good.... was able to watch F1 China with the race on one, and the timing data on the the other.
I have yet to try modifying my drivers, primarily because my other PC has gone down with a presumed motherboard fault.
I tested the psu outputs with 'on signal' bridged, and all voltages reported correct (but without load).
Nothing at all displayed on the monitor, so It's likely to be the motherboard.
It should arrive anytime.

Xubuntu still doesn't load.

There is some relationship between xubuntu and xfce, but I don't fully understand it.
Talk seems to be that you load xubuntu and get xfce as an option.

Also, what is not clear, is this question of 'clean install'.

Okay.... so I have a variant of linux... it's ubuntu.

I think that ubuntu is a general GUI that sends commands to the O/S, plus a number of specific tool GUI's, and perhaps a repository bank for approved optional software, with a download centre.

I think that.... but I may be entirely, or partially incorrect.

XFCE still offers 'software centre', but the GUI interface is entirely different, as are some of the specific tools.

But is this not just a case of having a less cpu intensive method of launching programs OR is there something definitively different between separately installed ubuntu and xfce o/s's?

---

### Post by baphomet2 on 2014-04-24
Sorry it took so long to reply.  Work has been a nightmare as of late.

The relationship is xubuntu and xfce are just about the same thing.  xubuntu is built on the xfce interface which uses xserver.  To be honest I haven't really seen a noticeable difference between the two so I'm not really sure why they are listed separately.

You do have a variant of linux which is Ubuntu.  Ubuntu is a "debian based" variant.  What the community did after that was modify the interface and base packages making different "flavors" of Ubuntu.

What clean install means is they have iso's out there for each flavor of ubuntu (kubuntu, lubuntu, xubuntu, etc).  When you install Ubuntu you get the Unity interface and gnome.  If you then install xubuntu you have both gnome and xserver packages/libraries installed.  They do share some tools, but not all of them.  So for a "clean install" you download the xubuntu iso - [http://xubuntu.org/getxubuntu/](http://xubuntu.org/getxubuntu/) and install it.  Now what you would have is strictly xubuntu using xserver.  You will still have some gnome as they are needed for some tools, but it isn't full blown.  Is it really necessary at this point?  I don't think so, but in the future if you install a new computer you should start with the specific flavor you want instead of Ubuntu first.

I'm glad you got everything working the way you wanted it and are enjoying your introduction to xubuntu.

---

### Post by Ace..... on 2014-04-26
Enjoying xubuntu...
Well, apparently I am, according to your post (vis a vis xubuntu being the same as xfce), only that I have't seen xubuntu since launching xfce :)

Not that i mind, cos XFCE  seems to be the 'thinking man's o/s'..... not happy.... then change it.

The problem is: the scale and spread of knowledge.
An expert in one field of computing can be an imbecile in another.

Me... I started computing with IBM DOS, which then became MS DOS.
I've developed data recovery software, and can explain to any willing listener, how information is stored on a disk.

Yet.....
...... do I understand the linux world.
Er.... no, I don't.

I had previously thought of linux like DOS.
First we had DOS.
Then we had 'launch option lists'
ie. instead of changing dir to paradox, and then launching paradox.... we simply launched paradox.

Then we had Windows, which launched programs by clicking on a pictorial representation of a program (but that the click, merely enacted the typed command).

I always thought of ubuntu like windows....... effectively a GUI to replace typed commands
However, I guess it is more complicated than that

:)

---

### Post by monkeybrain20122 on 2014-04-26
You specs are more than enough to run Unity smoothly, you don't need a "light" desktop (it is a myth that Unity is super hungry on resources) If even with xfce you can only watch 480p on Youtube it is a graphic driver problem. Which driver do you use? For your card even the open driver supports vpdau decoding but you may have to get it from a ppa.

---

### Post by d-cosner on 2014-04-27
I agree, that is more than enough of a system to run Unity. Sounds to me like hardware acceleration needs to be turned off in Firefox. Also, make a flash video full size, right click and go into flash settings and turn off hardware acceleration too.

---

### Post by Ace..... on 2014-04-30
> **monkeybrain20122 said:**
> 
If even with xfce you can only watch 480p on Youtube it is a graphic driver problem. Which driver do you use? For your card even the open driver supports vpdau decoding but you may have to get it from a ppa.

I ran:

```
lspci | grep -i vga
```

This returned:

```
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Wrestler [Radeon HD 6250]
```

I believe this is describing the graphics chip and not the driver.

Here is the relevant output of 
```
sudo lshw
 
description: Notebook
    product: eME644 (123456789)
    vendor: eMachines
    version: V1.07
    serial: LXNCW020081131E14E1601
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall32
    configuration: boot=normal chassis=notebook family=Type1Family sku=123456789 uuid=1E118C95-56AA-11E0-987D-1C7508F91871
  *-core
       description: Motherboard
       product: eME644
       vendor: eMachines
       physical id: 0
       version: V1.07
       serial: LXNCW020081131E14E1601
       slot: Base Board Chassis Location
     *-firmware
          description: BIOS
          vendor: eMachines
          physical id: 0
          version: V1.07
          date: 03/07/2011
          size: 1MiB
          capacity: 1984KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb
     *-memory
          description: System Memory
          physical id: 24
          slot: System board or motherboard
          size: 3GiB
          capacity: 3GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1066 MHz (0.9 ns)
             product: NT1GC64BH4B0PS-CG
             vendor: Nanya Technology
             physical id: 0
             serial: C1FAC819
             slot: DIMM0
             size: 1GiB
             width: 16 bits
             clock: 1066MHz (0.9ns)
        *-bank:1
             description: SODIMM DDR3 Synchronous 1066 MHz (0.9 ns)
             product: HMT325S6BFR8C-H9
             vendor: Unknown
             physical id: 1
             serial: 6176FA8B
             slot: DIMM1
             size: 2GiB
             width: 8 bits
             clock: 1066MHz (0.9ns)
     *-cpu
          description: CPU
          product: AMD C-50 Processor
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 2d
          bus info: cpu@0
          version: AMD C-50 Processor
          serial: NotSupport
          slot: Socket FT1
          size: 1GHz
          capacity: 1GHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni monitor ssse3 cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch ibs skinit wdt arat npt lbrv svm_lock nrip_save pausefilter cpufreq
          configuration: cores=2 enabledcores=2 threads=2
     *-cache:0
          description: L1 cache
          physical id: 2e
          slot: L1 Cache
          size: 128KiB
          capacity: 128KiB
          capabilities: pipeline-burst internal write-back unified
     *-cache:1
          description: L2 cache
          physical id: 2f
          slot: L2 Cache
          size: 1MiB
          capacity: 1MiB
          capabilities: pipeline-burst internal write-back unified
     *-pci:0
          description: Host bridge
          product: Family 14h Processor Root Complex
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
        *-display
             description: VGA compatible controller
             product: Wrestler [Radeon HD 6250]
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
             configuration: driver=fglrx_pci latency=0
             resources: irq:42 memory:c0000000-cfffffff ioport:4000(size=256) memory:d0400000-d043ffff
        *-multimedia:0
             description: Audio device
             product: Wrestler HDMI Audio
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 1.1
             bus info: pci@0000:00:01.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm pciexpress msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:40 memory:d0444000-d0447fff

```

The conclusions are not clear to me.
The Wrestler appears to be 32bit, while my PC is 64bit, but maybe this is not significant?
```
configuration: driver=fglrx_pci latency=0
```
I'm out of my comfort zone here.
Is this the correct driver?

I loaded: 
[http://driverscollection.com/?H=Radeon%20HD%206250&By=AMD&SS=Linux%20x86_64](http://driverscollection.com/?H=Radeon%20HD%206250&By=AMD&SS=Linux%20x86_64)

and noted that the latest driver for 64bit linux is 13.12.

Yet there is no mention of this driver on:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

:confused:

---

