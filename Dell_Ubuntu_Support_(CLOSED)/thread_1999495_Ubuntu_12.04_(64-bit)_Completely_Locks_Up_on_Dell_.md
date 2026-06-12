---
title: "Ubuntu 12.04 (64-bit) Completely Locks Up on Dell Vostro 470"
date: 2012-06-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by chienpo on 2012-06-08
So, we recently purchased a new Dell Vostro 470 with a Core i5 3450 processor and promptly installed Ubuntu 12.04 LTS, 64-bit on it. We've got two identical Dell displays connected to it and for the first couple days it ran beautifully.

Then it froze. After the first incident it pretty much happens every 2-4 hours or so when being used.

When frozen, the keyboard is completely unresponsive. The NUMLOCK key doesn't toggle the LED. No CTRL-SYSRQ-x key sequences (REISUB) work. CTRL-ALT-Fn sequences don't either, nor does CTRL-ALT-DEL. The mouse is likewise useless and the display is completely frozen with no screen updates -- not a single pixel ever changing.

We ran the full Dell Diagnostic suite that comes with the Dell BIOS which scans many hardware components, including doing their equivalent of a memory test (we did the "deep" or "detailed" version of their scan). No errors.

Then, while running Ubuntu I opened the Disk Manager and opened the Smart Data (or was it "Details") and had it do a surface scan (the most rigorous one) to check for bad sectors. No issues there.

We also ran [cpuburn]("http://packages.ubuntu.com/precise/cpuburn"), one instance for each of the four cores for about a half hour with not even the slightest glitch. Just for kicks I even used [debsums]("http://manpages.ubuntu.com/manpages/karmic/man1/debsums.1.html") to ensure no package files were corrupted.

I also took a gander at the log files to see if anything stood out. Having viewed a lot of log files through the years, I didn't see anything that wasn't the ordinary, verbose chatter of the various systems. Also no core dumps or such that I can see either.

In short, the hardware and the installation seemed to be fine and the system and all peripheral hardware worked great -- right up until the whole system froze.

What I haven't tried yet:

I haven't tried pinging or ssh-ing into the machine when frozen. When I though of this earlier today, I decided I'd do it next time it froze. Now, of course, it refuses to freeze and just works normally. I'll do this when I can.

So anyone else with similar Dell hardware having a similar issue on 12.04? Since the hardware looks good, my last option in order to be able to send it back to Dell is if the problem exists under Windows too (since it's supported by Dell). I really don't want to have to restore windows and waste time trying to get it to freeze or blue screen, and there's a good chance it is some obscure driver issue.

So, if you have any diagnostic ideas or can report a similar problem, please let me know.

Thanks.

---

### Post by sanderj on 2012-06-08
My ideas:

- run memtest86 from the GRUB boot menu. Run for one night and see if it reports something bad
- monitor CPU temperature
- install Ubuntu 11.10 (with its older kernel), to see if that changes anything
- you haven't said which video hardware is in your Dell Vostro. Did you install proprietary drivers for that?

---

### Post by chienpo on 2012-06-08
Here's the latest update.

First of all, thank you sanderj for responding with your recommendations.

Last night I went ahead and ran memtest86 on it all night (12+ hours). No errors. Additionally, I ran cpuburn again for some time (1 hour or so) with no issues (again, one instance for each core). While doing so, I watched the output of the "sensors" command provided by installing the "lm-sensors" package (I also used "acpi -V" to monitor temperature information, but the low, unchanging temps of 27.8 C and 29.8 C seemed wrong for the temps. of a CPU under load). The four CPU core temperature readings and the "Physical id 0" entry from the "sensors" command all stayed within a range of 63 C up to 68 C while running cpuburn. The temperatures never got close the "high" mark of 85 C. So, unless my understanding of what constitutes an overheated CPU is wrong then I'd say that temperature isn't an issue. I'd also say that raw CPU load of basic instructions isn't an issue either.

Also, I had the opportunity to see if the Vostro would respond on the network when frozen. It doesn't. The network stack is definitely down.

Also (possibly) of interest is that the last time it froze on the user who uses it, he was listening to music at the time (first time it's done that while listening). It kept replaying the same short clip of music over and over. I assume this is because the audio processor at some low level just processes an internal memory buffer through a DAC. With the system locked up, there weren't any updates to said memory buffer or any new "instructions" on what to do, hence the endless loop.

Finally, as per another item that sanderj pointed out, the system is running stock Ubuntu 12.04 (64-bit) last updated yesterday. We have performed _zero_ customization to it beyond installing basic end-user packages. No updated drivers, no packages installed from any repository other that those enabled during install by default.

More complete hardware details of the machine (specifically graphics) is as follows:

```
$ lspci
00:00.0 Host bridge: Intel Corporation Ivy Bridge DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)
00:1c.3 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 4 (rev c4)
00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
01:00.0 Network controller: Atheros Communications Inc. AR9485 Wireless Network Adapter (rev 01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 07)

$ sudo hwinfo --gfxcard
> hal.1: read hal dataprocess 6428: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file ../../dbus/dbus-errors.c line 282.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
09: PCI 02.0: 0300 VGA compatible controller (VGA)              
  [Created at pci.318]
  Unique ID: _Znp.y1_HW635yXC
  SysFS ID: /devices/pci0000:00/0000:00:02.0
  SysFS BusID: 0000:00:02.0
  Hardware Class: graphics card
  Model: "Intel VGA compatible controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x0152 
  SubVendor: pci 0x1028 "Dell"
  SubDevice: pci 0x0546 
  Revision: 0x09
  Driver: "i915"
  Driver Modules: "drm"
  Memory Range: 0xf7800000-0xf7bfffff (rw,non-prefetchable)
  Memory Range: 0xe0000000-0xefffffff (ro,non-prefetchable)
  I/O Ports: 0xf000-0xf03f (rw)
  IRQ: 44 (319969 events)
  Module Alias: "pci:v00008086d00000152sv00001028sd00000546bc03sc00i00"
  Driver Info #0:
    Driver Status: i915 is active
    Driver Activation Cmd: "modprobe i915"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

Primary display adapter: #9
```So the graphics adapter is the built-in Intel HD Graphic adapter that comes with Ivy Bridge chips, using the i915 driver. The machine has a VGA and an HDMI output. Both are used and connected to a Dell moniter. The HDMI output has a HDMI-to-DVI adapter since the monitors don't have HDMI inputs.

Also of note is that I just noticed that the /var/crash directory has the following in it:

```
kendall@strife:~$ ls -al /var/crash/
total 252
drwxrwsrwt  2 root     whoopsie   4096 Jun  6 07:35 .
drwxr-xr-x 13 root     root       4096 Jun  8 03:34 ..
-rw-r-----  1 chase    whoopsie  62977 Jun  5 17:56 _usr_bin_session-installer.1000.crash
-rw-r-----  1 root     whoopsie 184233 Jun  5 15:28 _usr_bin_Xorg.0.crash
-rw-r--r--  1 root     whoopsie      0 Jun  5 15:29 _usr_bin_Xorg.0.upload
-rw-------  1 whoopsie whoopsie      0 Jun  8 17:58 _usr_bin_Xorg.0.uploaded
```So, perhaps it is ultimately a graphics/Xorg problem? However, this machine has frozen several times since the June 5th timestamps on all those files, so... I'm stumped.

Anyhow, thanks anyone for even taking any time to read this novel.

P.S. - For full disclosure, I've also been posting this same stuff in Dell's community support forums:

[http://en.community.dell.com/support-forums/software-os/f/3525/t/19452199.aspx](http://en.community.dell.com/support-forums/software-os/f/3525/t/19452199.aspx)

The information is the same though I've been a bit more detailed here.

---

### Post by sanderj on 2012-06-09
If it were an X problem, the network should still be responding.

I don't understand the audio thing; AFAIK there is no audio processor and everything is handled by the CPU

I guess the REISUB method does not work anymore? 

Have you tried running an older Ubuntu (11.10) or a different distribution?

Has the system still Windows installed? If so, is that stable (I can't imagine)?

Finally: have you contacted Dell by phone about this?

---

### Post by chienpo on 2012-06-10
> **sanderj said:**
> If it were an X problem, the network should still be responding.

I agree.

> **sanderj said:**
> I don't understand the audio thing; AFAIK there is no audio processor and everything is handled by the CPU

Well, at some point there's got to be some kind of a digital-to-analog converter (DAC) that itself is likely a simple, independent component that feeds/controls the physical, analog audio output.

> **sanderj said:**
> I guess the REISUB method does not work anymore?

Nope, that was one of the first things I tried.

> **sanderj said:**
> Have you tried running an older Ubuntu (11.10) or a different distribution?

Has the system still Windows installed? If so, is that stable (I can't imagine)?

I have not yet tried a different distribution, and no, I completely replaced Windows when I installed Ubuntu.

However, I like your idea of installing an older version and/or another distribution. I'll probably try that next. At some point I'll also likely restore Windows to the machine using the restore disks to see if it freezes too. Trying different OS versions and completely different OSes entirely will help me identify whether this is a hardware or software problem.

> **sanderj said:**
> Finally: have you contacted Dell by phone about this?

Dell's support just directed me to the "software vendor" (here) when, according to their diagnostics, the hardware was determined to be fine. According to Dell this is a software problem since the Dell Diagnostics software that's built into the BIOS indicated that everything was fine. The tech. basically directed me to the Dell equivalent of this forum for "software support". However, my post on Dell's forum has garnered zero responses. In all fairness, this is a tricky problem. But at least here you (sanderj) responded (thanks for that, by the way). In other words, the story of the problem here is that if you're not running the official Dell-supported OS then don't expect too much unless it is an obvious hardware problem. In all fairness, it might not be a hardware problem anyway. So, unless I restore Windows 7 to the machine and demonstrate that it freezes too, then it's all on me to get this fixed.

This is why I'm kicking myself for not originally buying one of the "[Certified Hardware]("http://www.ubuntu.com/certification/desktop/")" models. At least that way I'd know that the specific configuration of hardware had presumably  worked with the specified version of Ubuntu and that any ensuing problems with the machine was definitely due to hardware.

Anyhow, I'll update the thread after I've tested with other versions/distros/Windows.

Thanks again for the help!

---

### Post by logophile on 2012-06-11
Of interest to this issue, I've noticed that on the Dell Singapore Vostro 470 information page under Tech Specs, the "Operating System" header lists:

> 
Genuine Windows® 7 Home Premium SP1 64bit (English)
Genuine Windows® 7 Professional SP1 64bit (English)
Genuine Windows® 7 Professional SP1 64bit with XP Mode installed (English)
Ubuntu Linux 11.10


Here's the link: [http://www.dell.com/sg/p/vostro-470/pd]("http://www.dell.com/sg/p/vostro-470/pd")

I also checked the Dell website of other countries and many Asian countries also list Ubuntu Linux 11.10. The tech specs are otherwise quite similar between countries (i.e. all have "ivy bridge" processors and Intel H77 Express chipsets), but the choice of video card and some other options does vary from country to country.

Anyhow, all that to say definitely try running 11.10 as there are good chances it will work. I'm also very much interested in this issue as I intend on getting this machine to run Ubuntu, so I'm keen to see what you find out!

---

### Post by chienpo on 2012-06-11
Wow logophile, that *is* interesting. It had definitely been determined that we will be downgrading the machine to 11.10 and trying that out. However, I probably won't get to it for several days. However, I will update the thread when I do to let you know how it works.

Thanks for that *very* interesting information!

---

### Post by greenm01 on 2012-06-12
I'm having the exact same problem on my Dell Studio1569 notebook, under Ubuntu 12.04 x64.

Whenever I leave my system inactive for several hours my system locks up. I have a black screen and the system is completely frozen. I have to turn off the power and reboot my machine. 

I have the 'suspend' power settings turned off. My notebooks is plugged into the AC power adapter. It appears the computer goes into suspend/hibernate mode, and will not wake back up without a hard reboot.

---

### Post by chienpo on 2012-06-12
> **greenm01 said:**
> I'm having the exact same problem on my Dell Studio1569 notebook, under Ubuntu 12.04 x64.

Whenever I leave my system inactive for several hours my system locks up. I have a black screen and the system is completely frozen. I have to turn off the power and reboot my machine.

It does sound similar. However, our system doesn't seem to ever freeze when we're ***not*** using it. Our freezes specifically seem to happen while it is actively being used in one capacity or another. As such, our screen is never black when it freezes. It is frozen with the last state of the desktop, showing whatever apps that were open when it froze.

> **greenm01 said:**
> I have the 'suspend' power settings turned off. My notebooks is plugged into the AC power adapter. It appears the computer goes into suspend/hibernate mode, and will not wake back up without a hard reboot.

Despite the differences in our situation, it still could be a similar or related problem. Have you also performed extensive diagnostics so that you can cancel out hardware problems? Also, just so that we can see if there is any correlation with our hardware, what does the (your) Dell Studio1569 notebook come with (processor, graphics hardware, etc.).

My system (Vostro 470 CTO Desktop) has a 3rd generation Intel Core i5-3450 processor ("Ivy Bridge" 3.10 GHz "with Turbo Boost 2.0 up to 3.5 GHz" and 4 cores) with Intel HD 2500 Graphics. We have no other graphics adapter besides the built-in Intel HD 2500 Graphics.

If you need info on your hardware, try the "lspci", "lscpu" and "hwinfo" commands. You will probably have to install packages to get "lscpu" and "hwinfo" but I think "lspci" comes with Ubuntu by default.

---

### Post by amilkh on 2012-06-13
I am having the same black screen problem with my Dell Vostro 1510. I have a dual-boot configuration with Windows 7 Ultimate(32-bit) and Ubuntu 12.04 (64-bit).
The issue happens randomly, but usually when I connect/disconnect from external VGA monitor, open/close the lid, flip the wireless switch on/off. Also, if I boot up with my wireless switch off, the wireless won't work until I reboot my Ubuntu.
No key combinations work like in your case.

A little background information is that my hibernate/suspend don't work properly on this machine, even under Windows. In Vista (I had previously), hibernate worked, but suspend didn't. In 7, suspend works but hibernate doesn't! Also, my wireless had some problem of not connecting to certain old routers, but 7 seemed to fix this.
I am using the proprietary drivers under Ubuntu and have disabled automatic suspend/hibernate in power options, as well as screen saver.

Here is my system log (from Windows):
> OS Name	Microsoft Windows 7 Ultimate
Version	6.1.7601 Service Pack 1 Build 7601
Other OS Description 	Not Available
OS Manufacturer	Microsoft Corporation
System Name	MY-PC
System Manufacturer	Dell Inc.
System Model	Vostro1510
System Type	X86-based PC
Processor	Intel(R) Core(TM)2 Duo CPU     T5670  @ 1.80GHz, 1801 Mhz, 2 Core(s), 2 Logical Processor(s)
BIOS Version/Date	Dell Inc. A15, 3/18/2009
SMBIOS Version	2.4
Windows Directory	C:\Windows
System Directory	C:\Windows\system32
Boot Device	\Device\HarddiskVolume1
Locale	United States
Hardware Abstraction Layer	Version = "6.1.7601.17514"
User Name	MY-PC\MY
Time Zone	Pacific Daylight Time
Installed Physical Memory (RAM)	4.00 GB
Total Physical Memory	2.99 GB
Available Physical Memory	1.67 GB
Total Virtual Memory	5.98 GB
Available Virtual Memory	4.66 GB
Page File Space	2.99 GB
Page File	C:\pagefile.sys



Any help appreciated! I think our issues are linked.

PS: I found [this post about blank screen]("http://ubuntuforums.org/showthread.php?t=1743535"), which I'll check out later.

---

### Post by theBrand on 2012-06-16
Hi, I'm experiencing the same problem. Complete system lockup, nothing responds, not even alt+sysrq.
For me the lockup happens when ever there is intensive graphics on screen, mainly while watching videos. It seems to worse the bigger the size of video window.

I have a HP tx2500 laptop, with a dual core AMD and AMD/Radeon graphics. I have run memtests, have no problems in windows, nor did I experience this problem before updating to 12.04.

It also seems there are several users having the same issue:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/993187](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/993187)

All with different kinds of hardware, though I guess we all would be having a PCI-bus? Perhaps thats the link?

Anyway, I don't think you will be getting anywhere by trying to find faults with you hardware, since we seem to be many people experiencing this since 12.04.

---

### Post by greenm01 on 2012-06-16
I managed to take a photo of the screen dump:
[http://imageshack.us/photo/my-images/214/crasheg.png/](http://imageshack.us/photo/my-images/214/crasheg.png/)

Any ideas?

---

### Post by theBrand on 2012-06-17
No, not really, how did you get that log? Is it from after the system froze? (I haven't managed to get any type of response from the system when it freezes, not even sysrq)

From what the call trace shows it stops in the scsi drivers allocation function, I can't see any reason why that would freeze the system completely? 
What I have found how ever is that 12.04 brings a bunch of new features for power saving modes in PCI and USB, I'm going to try and shut them of and see how that goes, probably tomorrow. I'll report back when I've fiddled around a bit...

---

### Post by theBrand on 2012-06-17
Sorry, I read the back trace up side down :D 
It ends in gs_change, which is about changing context to/from userspace. The documentation mentions it as very fragile, and there are two different methods to be used, depending on what context  you come from. 
When googling the thing I got lots of hits on bugs regarding ACPI.
Correlating this information with the newly added features for USB and PCI, and the fact that many users seems to have less problem with this bug when disconnecting all usb devices...  I think it's time to turn of the ACPI...  (Though now it's bedtime :))

---

### Post by amilkh on 2012-06-17
> **theBrand said:**
> Sorry, I read the back trace up side down :D 
It ends in gs_change, which is about changing context to/from userspace. The documentation mentions it as very fragile, and there are two different methods to be used, depending on what context  you come from. 
When googling the thing I got lots of hits on bugs regarding ACPI.
Correlating this information with the newly added features for USB and PCI, and the fact that many users seems to have less problem with this bug when disconnecting all usb devices...  I think it's time to turn of the ACPI...  (Though now it's bedtime :))
Yes, I think it does have something to with USB devices based on the [bug tracker]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/993187"). I am actually using a Microsoft USB wireless mouse and Inland USB keyboard.

Please let us know how to turn off ACPI and whatever you do, so I'll try it as well.

---

### Post by tvb23 on 2012-06-18
Hello,
Well lemme start off by saying I know pretty much nothing about computers but i can try to help cause I had a similar problem and found how to fix it. I bought a new computer with an Ivy bridge core i7 and a mother board with a Z77 chipset. It worked fine when I installed a fresh version of Ubuntu 12.04 for a little bit and then i noticed that it would freeze. The freezing seemed to be random and unrelated to heavy jobs or RAM usage. I notice the freeze would always occur when I was using the Interface, either moving the mouse, clicking something or typing. I could calculate 20 Billion Discrete Cosine Transforms, leave, and come back in several hours and it would still be running, but if i was interacting with computer it would freez.  When the freeze occurred there was absolutely no response from anything, no REISUB, nothing. only way to restart was to pull the plug. literally. 

Well I realized it wasn't an Xorg failure Because i couldn't even toggle the caps or numlock. This is a pretty good indicator of kernel panic. So i got that new kernel. if you enter 

uname -a 

in a terminal it will print your kernel version. Ubuntu 12.04 ships with kernel 3.2.xx. if u got kernel 3.2.xx or below i would try upgrading to kernel 3.4.xx. Thats what i did and my computer never froze again. 

you can do this by going to 
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4-precise/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4-precise/)

from there download the three files:
linux-headers-3.4.0-blahblahblah_all.deb
linux-headers-3.4.0-blahblahblah_amd64.deb
linux-image-3.4.0-blahblahblah_amd64.deb

use the ones with "amd64" for 64 bit OS and "i386" for 32 bit OS
use the "all" one regardless of architecture.

now just cd to the directory where u downloaded them and dpkg each one individually in the terminal with 

sudo dpkg -i <put the name of the file here>.deb

once thats done restart with 

sudo init 6

when ur system reboots check uname -a and see if u have kernel 3.4

Well thats my two cents. im sorry if its not helpful, but good luck.

---

### Post by chienpo on 2012-06-21
Hello, this is the original poster with some follow-up information.

First of all, I promised I'd post the results of our system's behavior after we downgraded the OS to Ubuntu 11.10. We did the downgrade last week and the system froze, if anything, with greater frequency under 11.10. So, that idea as a solution is out. Note that we tried both the 32-bit and 64-bit versions of 11.10 and 12.04 of Ubuntu with the same results. As such, we elected to just return the system and get a different one. We were lucky enough to be within the period where we still could return it. Unfortunately, this means I can't help with further diagnostics.

Next, thanks to all those who helped out. Thanks to *theBrand* for sharing the link to the bug that's been filed for this issue: **[#993187]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/993187")**.

If anyone's symptoms match mine or others who've posted here (that also match mine), this bug is the place to go to continue following this issue. Note that my issue here and the one described in the bug *only* involves freezes that are *absolute*, meaning there's no opportunity to REISUB, ping, ssh, telnet, access a terminal, get a crash dump, etc. Also, the screen just locks. There's no black screen, no terminal output, no error window or other messages, etc. Finally, it would appear that the other common aspect mentioned in the bug and by some in this thread, is that the system might work fine when doing simple computation (raw CPU work and even handling SSH session work) but instead tends to freeze when there's direct user interaction on the desktop via the directly connected mouse or keyboard.

On this note, thanks to *tvb23* with the kernel upgrade suggestion. I wish I could try that out and post the results but it's too late for that. Perhaps someone else will find this thread, try it out, and provide a confirmation for the solution that worked for you.

Anyhow, I'm going to go ahead and marked this "resolved". However, this post's purpose is to explain my justification for marking it so. After all, I didn't really "solve" the problem for myself (though I might have if I'd been able to test *tvb23*'s suggestion). What we did get, though is a link to a launchpad bug report where further discussion and analysis can go (and a possible solution above from *tvb23*).

Thanks again to all who helped and good luck to future forum users who come across this thread!

---

### Post by DonKaron on 2012-07-13
I was having the exact same symptoms as you, only this computer is a T430s: lockups during keyboard use and then no response to any keyboard or mouse input. 

I followed your directions and it appears to have solved the lockup problem. 

One thing I found was that I had to install the three sections in the order 

          1) linux-image <xxxxxx> 
          2) linux-headers <xxxxxxx>-all 
          3) linux-headers <xxxxxxx>-amd64  

because otherwise I was getting told that the install did not occur due to unsatisfied dependencies.

Thanks for the help.

          Don

---

### Post by AxMstrLP on 2013-02-12
I'm experiencing very similar problems with my Dell E6420.  

A few data points:

1. X is running but I rarely interact with the machine via the console.  I always SSH to it.  The point is:  no keyboard use, and no USB plug/unplug events.  The lid is open but the screen is almost always off.
2. It seemed to only crash over the weekends, then only at night but now it seems it'll crash any time.  I can't scientifically say that the problem is actually worsening (as compared to my habits changing).
3.  Running VirtualBOX with a WinXP guest seems to exacerbate the problem (from crashing once every two days to crashing twice/day).
4.  I'm docked, using wired ethernet, wireless disabled.

But the most interesting bit is:  when it crashes it seems the ethernet interface chatters away and I have to reboot my ethernet switch after rebooting the machine.  The network interruption seems to happen without fail when the machine locks up.  It's quite noticeable since it interrupts all the other machines on the switch.  There's never anything useful in the log.  Maybe this is an interrupt storm and the int-handler keeps re-sending the last packet?

I've just switched from using the dock ethernet to using the on-board ethernet.  We'll see if that cures it.

--Miles

---

