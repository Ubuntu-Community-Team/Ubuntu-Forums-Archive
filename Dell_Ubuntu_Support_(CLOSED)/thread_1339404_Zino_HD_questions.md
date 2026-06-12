---
title: "Zino HD questions"
date: 2009-11-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by reiki on 2009-11-27
Dell is supposed to offer the Zino HD with Ubuntu preinstalled, but that option isn't showing yet at Dell. Since I'm not the patient type, I ordered a Zino HD as follows:
Athlon Neo X2 6850e processor
8GB memory
ATI HD 4330 discrete 512MB graphics card
Win7 64-bit (had to upgrade the OS to 64-bit in order to get the 8GB of memory or Dell's system bounces it out as invalid)

I get Win7 Enterprise through my work for $14.95 so I'm a bit miffed at spending to upgrade to an OS I'll never use.

I plan on wiping this when I get it and installing Win7 Enterprise into about a 100GB partition and then give the rest to Ubuntu 9.10 since that's my primary OS. I just keep a windows partition in case I need to test something for work.

ANYWAYS .... anyone installed Ubuntu onto one of these yet? I've got no experience with AMD processors but don't expect that part to be a problem. I'm wondering about the ATI Mobility Radeon HD 4330 graphics card, the Broadcom BCM57780 10/100/1000, and I think it uses Conexant for audio.

I didn't order it with wireless so no concerns there.  Anyone see anything I might have to tinker with or do you think this should install Ubuntu 9.10 without a hiccup?

---

### Post by erlguta on 2009-11-30
Hello Rieki. I am thinking in buying this mini pc too, so i will wait for your comments about, when you recieive it, to see if all the things are supported.
What about the ATI card, network and sound?.
One more thing. Does the Athlon Neo X2 6850e processor support virtualizacion ('svm' extension I think is called...). You can see it in the BIOS or posting here one:
egrep '(vmx|svm)' --color=always /proc/cpuinfo

I will apreciate your help.

Thank you for all the help you can provide, because i am afraid you are one of the first trying to install Ubuntu in the Zino HD ;)

---

### Post by gamx on 2009-12-01
In principle it should work just fine. In the specs it says that it can come with Ubuntu 9.04 preinstalled, but of course, when you try to configure it, Ubuntu is nowhere to be found... Anyway, it probably means that everything is standard.
I was thinking of buying one to use as a HTPC/NAS. I have seen that power consumption is quite modest (65W). I wonder how low power consumption can be when idle. Any ideas?

Gamx

---

### Post by reiki on 2009-12-03
Go here for some good information on the Zino HD in terms of real life capabilities for HTPC useage and power consumption, etc

[http://blogs.amd.com/home/](http://blogs.amd.com/home/)

Mine is still showing as "in production" (since November 25th!).
I think Dell got bombarded with orders for these over thanksgiving weekend. Appears to be a backlog in getting orders cleared to ship.

---

### Post by gregconquest on 2009-12-06
DELL could conceivably offer the Zino with some components having no linux driver support. Maybe the bluetooth chip, maybe one of the wireless LAN chips, maybe the BluRay DVD player, etc. You choose ubuntu and some options would disappear that would be there if you were choosing Windows. So, don't assume everything is going to work with ubuntu just because they have said they will offer the system with ubuntu.

---

### Post by reiki on 2009-12-06
> **gregconquest said:**
> DELL could conceivably offer the Zino with some components having no linux driver support. Maybe the bluetooth chip, maybe one of the wireless LAN chips, maybe the BluRay DVD player, etc. You choose ubuntu and some options would disappear that would be there if you were choosing Windows. So, don't assume everything is going to work with ubuntu just because they have said they will offer the system with ubuntu.

Yes, I can't argue against you on this one. I know how Dell's system works as I sell about 3 to 5 million dollars in dell equipment a year. All in the business and comercial lines though. Not consumer lines. 

Right now it looks like if you don't order the discrete graphics card and instead opt for the integrated graphics, you do not get the MXM slot to upgrade to a discrete later.  Otherwise it appears to be a vary basic build with no hardware variations other than "add" options.... no "if this, then NOT this". 

This is going to be an Ubuntu box. If it won't run Ubuntu it goes back. It's that simple really. I'll evenn pay their ridiculous restocking fee and chalk it up to experience. But it's GOING to be an Ubuntu box.

First things first though.... it has to actually SHIP! :)

---

### Post by B34N on 2009-12-11
I just received mine today.  I installed Ubuntu on it right away.  The installation went just as easily as normal but I'm not getting sound (from onboard soundcard) and I can't get HDMI video or sound output.  With the HDMI video, I had output when booting off the Ubuntu disk, choose install and the first few moments of the installation.  It went black when it would have asked for the settings.

So I installed it using the vga output.  I went to add the monitor through HDMI and it gets recognized but it does not output.  I'm a beginner so I can be making some simple mistakes but I'm out of things to try.

Once I get it running I will be using it for MythTV and Hulu.

---

### Post by erlguta on 2009-12-12
st8ofmi9d, does your Zino have one Athlon Neo X2 6850e processor?
Can you post here one:
egrep '(vmx|svm)' --color=always /proc/cpuinfo

I will apreciate your help to know if this model support Virtualization...becuase if it does not have it. I will not buy it.

...about the sound card. Wich version did you install?. Karmic?. Did you play with the volumen levels?.
For me the sound is a very important thing that i want to know that works before buying this mini pc :(

---

### Post by B34N on 2009-12-12
> **erlguta said:**
> st8ofmi9d, does your Zino have one Athlon Neo X2 6850e processor?

No, I only upgraded to the AMD Athlon 32050e.  The whole system was only $229 and they are giving me a $60 Dell gift card of some sort which will be good for 90-days.  The gift card was something about Napster not working with Vista or some stuff.
> **erlguta said:**
> 
Can you post here one:
egrep '(vmx|svm)' --color=always /proc/cpuinfo
Did I do this right?

```
egrep '(vmx|svm)' --color=always /proc/cpuinfo
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch
```

> **erlguta said:**
> 
...about the sound card. Wich version did you install?. Karmic?. Did you play with the volumen levels?.

9.10 desktop, yup Karmic.  I played with the volume levels and no luck.  I changed the cable from the back speaker output to the front headphone and I get sound.  Any thoughts on what might be the issue there?  Again, I'm a newbie so I can very likely be doing something wrong.

I'm 99% sure that the HDMI issue is because of the Dell W3706MC TV that I' have it hooked up to.  I also unboxed a Blu-ray player last night and that does not work through the HDMI inputs either.  I did some searches and it seems that the TV has issues taking in full resolution through the HDMI.  I'm hoping that there is a firmware upgrade or something that can solve that issue, but I'm not optimistic that Dell will be able to solve it since the TV is so old.  It's the only HDMI display that I have so I can't test the Zino with another screen. 

Once I get this thing up and running it should be a sweet mythTV HTPC frontend.  It is replacing a P4 that met my needs (at the time) so I can't see this being any worse.  It would be nice if this could play Blu-ray but am I correct that Blu-ray with Ubuntu isn't really a viable option yet?  Yes I realize that I would have to upgrade the drive if Blu-ray and Ubuntu eventually work well.

After I get all the kinks worked out I will likely try to take out the 250GB drive and replace it with the 8GB SSD that was in my A90 netbook.  Any thoughts on if that will work and what cables/adapters I will need.  The 250GB would be nice to add to my backend and the 8GB is more than enough for the frontend needs.

---

### Post by erlguta on 2009-12-12
> **st8ofmi9d said:**
> 
Did I do this right?


Perfect!. It support viatualization. It is a very nice and powerfull little machine.

About sound. If it works with the front headphone it means that the sound is supported and it is working.

Try to right click in the volumen icon and go to preferences > output and look at the conector to see if you have the properly option...something like 'analog output' and no 'analog headphones'


Thank you for your information. We will follow you experiences ;)

---

### Post by B34N on 2009-12-12
> **erlguta said:**
> 
About sound. If it works with the front headphone it means that the sound is supported and it is working.

Try to right click in the volumen icon and go to preferences > output and look at the conector to see if you have the properly option...something like 'analog output' and no 'analog headphones'

No luck.  I am only getting sound out of the headphone port no matter which settings I try.  I'm a bit worried that my speaker output might be dead.  How could I test without installing XP or Vista?  (Yuck!)  I hear a brief click/buzz/static upon entering the jack into the headphone and mic jacks but complete silence when plugging into the speaker jack.

I'm no longer 99% sure that the HDMI difficulty has to do with my TV.  I was able to get the Blu-ray playing by setting it to 1080i since that's all the TV supports.  Also, the HDMI works fine upon boot up until the Ubuntu circle logo but goes blank when I get to where the Ubuntu spelled out logo should be.  Also, I changed the sound output to be the HDMI and I didn't hear anything upon startup/shutdown.  I do also see the circle logo upon shotdown.

Thank you!

---

### Post by srt4play on 2009-12-13
> **st8ofmi9d said:**
> they are giving me a $60 Dell gift card of some sort which will be good for 90-days.  The gift card was something about Napster not working with Vista or some stuff.

That's a nice added bonus.. did you have something selected in your configuration that prompted the gift card? Also, can you try fullscreen youtube and hulu and report if it's smooth playback or not. Thanks

---

### Post by jdkchem on 2009-12-14
> **st8ofmi9d said:**
> 

9.10 desktop, yup Karmic.  I played with the volume levels and no luck.  I changed the cable from the back speaker output to the front headphone and I get sound.  Any thoughts on what might be the issue there?  Again, I'm a newbie so I can very likely be doing something wrong.



I am having the same issue.  It appears the rear jack is not being properly identified.  At the moment I am playing around with Pulse Audio Device Chooser to see if I can't get both jacks to work.  

Could this be the hold-up in getting Ubuntu pre-installed?

---

### Post by jdkchem on 2009-12-14
I just compared the Zino to my laptop.  The sound preferences do not show the rear jack as present.  On my laptop both headphone jacks are shown in the sound preferences output tab.  Only the headphone jack is being picked up.  The mic jack works fine.

---

### Post by jdkchem on 2009-12-15
If anyone cares to try the problem is with the snd-hda-intel module.  So far I've tried adding ```
options snd-hda-intel model=laptop
``` and ```
options snd-hda-intel model=laptop-eapd
``` with no luck.  The eapd option has the added bonus of causing banshee to crash.

This may be Conexant 5051 from what I've been able to gather from searching.
```
cat /proc/asound/card0/codec#* | grep Codec
[COLOR="Red"]Codec:[/COLOR] Conexant CX20561 (Hermosa)

``` 

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
```
lspci -v
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
	Subsystem: Dell Device 040f
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at fe7f4000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
	Subsystem: Dell Device 040f
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at fe9e8000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel


```

Hopefully someone will figure this out.

---

### Post by B34N on 2009-12-15
> **jdkchem said:**
> Hopefully someone will figure this out.

It's over my head but these units are starting to ship out so there will be more people working on it.

Did you have any luck with HDMI output?

---

### Post by jdkchem on 2009-12-15
> **st8ofmi9d said:**
> 
Did you have any luck with HDMI output?

I haven't tried HDMI.  It handles Hulu quite well on a 19in monitor.  Better than the old athlon xp Ideq it is replacing.

---

### Post by reiki on 2009-12-16
Having the same issue with the sound ports. I'm at work right now and can't try this... but what about adding model=dell-m92

I'm not CERTAIN that's a valid parameter, but there are other dell-m parameters. If you try it and it works, let me know :)

Meanwhile, when I'm home I'll try a few other troubleshooting things.

Hey did you get the HD4330 card? and if so, which video drivers are you using?

---

### Post by zobby22000 on 2009-12-17
Hello,

I received my Zino HD today. I installed Ubuntu 9.10 on it, but I have no sound and no wired network. For network, I tried to install linux drivers from broadcom. After it, I noticed that "manual" configuration, I could ping IP addresses of internet but no web addresses. I thinked about a problem of DNS. I tried many configurations (public DNS, my router's DNS, my ISP's DNS etc...), but no solution... Have you configured something special for the network?
Bye !

---

### Post by erlguta on 2009-12-17
No wired network???
mmm, can you post one 'lspci' please?

---

### Post by B34N on 2009-12-17
> **zobby22000 said:**
> Have you configured something special for the network?

No, that worked right out of the box.  I made no changes to or configured the NIC. Sounds like a DNS issue to me.

---

### Post by zobby22000 on 2009-12-17
Sorry, no lspci for this moment. I installed Windows Seven for test and no internet ! 
I will try to change my ISP box (I'm in France with Freebox) from router mode to bridge mode.

---

### Post by erlguta on 2009-12-17
> **zobby22000 said:**
> Sorry, no lspci for this moment. I installed Windows Seven for test and no internet ! 
I will try to change my ISP box (I'm in France with Freebox) from router mode to bridge mode.

If you don't have internet in windows 7, and st8ofmi9d confirm that it worked out of the box, it is confirmed that wired network is working properly in the Zino :)

---

### Post by zobby22000 on 2009-12-17
It's a problem of my ISP box. So, tomorrow I reinstall Ubuntu !
Thank you !

---

### Post by reiki on 2009-12-18
The new fglrx driver seems to work fine with the HD4330 graphics card in the Zino HD. 

Now if I can just get the rear analog audio jack working I'll be a happy camper.

---

### Post by reiki on 2009-12-20
I think I'm just going to use a USB "sound card" until I have time to figure out why the rear analog jack isn't working. I haven't tried the mic jack yet.  If I get a powered USB hub, I can plug my mouse, keyboard, sound card, and a USB external into teh powered USB hub without worrying about sucking too much power from the Zino itself.

---

### Post by candlerb on 2009-12-21
> **reiki said:**
> I think I'm just going to use a USB "sound card" until I have time to figure out why the rear analog jack isn't working

I'm using a rather simpler workaround, of just plugging the monitor audio cable into the front jack :-) I'm happy to wait until a better solution arrives.

On the whole I'm really happy with the Zino HD: it's tiny, quiet, low-power, and plenty fast enough with its dual-core 64 bit processor (with virtualisation support too).

I've only come across two other problems:

- suspend/resume doesn't seem to be reliable - sometimes it works, sometimes the machine just won't come out of suspend. (Hibernate doesn't work either, but I'm not so bothered about that).

- the internal CD/DVD is pretty slow to rip audio CDs. It's much faster if I plug in an external USB LiteOn DVD-ROM/CD-RW. I need to try some of the suggestions which Googling turns up.

My monitor has a DVI input but I haven't got a HDMI-DVI cable yet to try it, so I'm still on VGA.

Regards,

Brian.

EDIT: Problem 3: Canon PowerShot A430 won't USB attach, although other USB devices have been fine. Reported as [https://bugs.launchpad.net/bugs/499235](https://bugs.launchpad.net/bugs/499235)

---

### Post by parke on 2009-12-22
Yesterday I installed Ubuntu on my very low-end Dell Zino.  I have a single core AMD CPU and the integrated HD 3200 graphics.  I am using a 1080p HDTV for a screen, connected via an HDMI cable.

The wired networking did not work with Ubuntu 9.04.  It does work with 9.10.

After installing 9.10, there were problems with the graphics.  Specifically, the graphical login screen would not appear, and the text login screen kept on flickering.  I think the graphical login screen was trying to start, and failing, repeatedly, multiple times per second.

I rebooted into rescue mode and dropped down to a root shell.  I ran "apt-get update", "apt-get upgrade" and "apt-get dist-upgrade" and then rebooted again.

This time I got graphical warning messages telling me the graphics were misconfigured, and offering me a variety of choices.  I forget exactly what I chose, but I think the only option that worked was to choose to continue with limited graphics or "safe mode", or something like that.

A graphical login prompt appeared, and I logged in.  I selected "Hardware Drivers" (Devices?) from the Administration menu and installed the restricted/proprietary ATI driver.  I then rebooted, and graphics worked fine, including "special effects", if you want to turn them on.

I disabled the analog sound, and enabled the HDMI digital sound option, and sound started working.  As I said before, I am using my Zino with an HDMI cable plugged into a 1080p HDTV.  I have not tested the VGA video output, nor the analog audio outputs.

After installing VLC and the "restricted-extras" (as per [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) ), and then rebooting, I was able to play DVDs.

Video playback in Ubuntu is better than in Vista.  VLC on Vista struggled to play back a 720p video, with lots of video glitching and video freezing.  Ubuntu can play the same video almost perfectly.  However, there my be some slight horizontal "tearing" during DVD/720p video playback in Ubuntu.  Vista/Windows may or may not suffer from that horizontal tearing during DVD playback - I don't remember it, but it might have been there.  Perhaps Vista/Windows has tighter integration with the video driver.  However, Vista even had some occasional stuttering playing back DVDs, which was disappointing.  This is the first time I have ever used Vista.  (I think I set the display resolution to 720p to playback the 720p video.  This means the HDTV, and not the Zino, was handling the upscaling to 1080p.)

There were also "overscan/underscan" issues with the display in both Vista and Ubuntu.  Basically, there is about an inch wide black border around the outside of the screen.  Even when the resolution is set to 1080p, the entire screen is not used.  In Vista I found a setting buried in the Catalyst Control Center software that can solve this problem.  Hopefully there is a similar driver setting in Ubuntu somewhere, but I have not found it yet.

So, to summarize:

After some tinkering, updated Ubuntu 9.10 with the restricted ATI driver works well on my Zino with the HD 3200 graphics and HDMI video/audio out.  Wired networking works, DVD drive works, HDMI sound and video work.  The biggest problem is the black inch wide border around the edge of the screen, which can be fixed in Vista and I hope that with some more work it can be fixed in Ubuntu, too.  Horizontal tearing during video playback may be slightly worse in Ubuntu than in Vista.

---

### Post by parke on 2009-12-24
Here is an update on my progress working with Ubuntu 9.10 and Windows XP on my Dell Zino HD (single core AMD CPU, integrated ATI HD 3200 graphics).

I installed Ubuntu 9.10 again.  Previously I installed 9.10 onto a 6GB USB hard drive, and encountered some problems as described in my previous post.  This time I installed 9.10 from a live USB stick onto a 20GB partition on the internal 250GB SATA hard drive.  This time, everything (wired networking, graphics, sound via HDMI) worked smoothly without any tinkering.  After installing the restricted graphics driver, the black border can be removed via the Catalyst Control Center (in Applications -> Other).

Interestingly, video playback is smoother if "Visual Effects" (in Preferences -> Appearance) is set to none.  If "Visual Effects" is set to normal or full (extra?) there is slight but noticeable horizontal tearing during video playback.  Once "Visual Effects" is disabled, video playback in Ubuntu is just as smooth as (if not smoother than) Vista.

I have also installed Windows XP Pro SP2 on another 20GB partition.  In order to install XP, I had to go into the BIOS and in the Integrated Peripherals screen set the SATA mode to "ATA" (instead of the default "AHCI").  Otherwise the XP installer would crash with a fatal error.  I installed the wired network driver from the Broadcom site, and the ATI Integrated Catalyst driver from ATI/AMD's site.  Both wired networking and video are working fine in XP.  (I also had to install .NET as the Catalyst Control Center depends on it.)

I have not yet got sound working in XP.  I'm not sure where to get the driver and/or what specific sound hardware is in the Zino.  There is a Catalyst Audio driver, and I installed it, but there are still 2 audio devices on the system that do not have a driver, and no sound output via the HDMI.  I suspect that if I do some more research and work I will be able to find XP sound drivers.

So, to summarize:  Everything works in Ubuntu 9.10 (except the rear audio jack), and everything except audio is working in XP.

---

### Post by erlguta on 2009-12-24
Nice review Parke!.
Thank you very much.

---

### Post by jdkchem on 2009-12-25
A quick update - 
The microphone works quite well.
The option model=dell-m92 alsa-base.conf does nothing.
When I fiddled with vista :rolleyes: I noticed that vista "knew" that I had no speakers plugged in.  I suspect that there is some "switch" that needs to be flipped that does not get flipped in Ubuntu.  It could be that one of the super secret Dell partitions needed to remain.
Vista was/is dreadful.  Booting from a live cd was less tedious and faster.  And the anti-virus update was prone to crashing.  I thought I might fiddle around with vista.  I was so disgusted I completely wiped the drive 
I got the integrated HD 3200 graphics and I am using the restricted ATI driver.

---

### Post by reiki on 2009-12-27
I got a USB sound adapter so I didn't have to have my speakers plugged into the front port. Works with no problem. Just had to unmute it which seems to be kinda normal.

---

### Post by shedberg on 2010-01-04
Hello... and help!,

I just got the following Zino HD 

Inspiron 400 with MXM Graphics,with ODD
AMD Athlon 6850e 1.8GHz, 1MB
8GB DDR2 SDRAM AT 800MHZ
ATI Radeon HD 4330 512MB Graphics Card
320GB Serial ATA Hard Drive (7200RPM)

Using HDMI to connect to TV without issue.

It has a dual boot installation of Windows 7 Home and Ubuntu 9.10.

When I run Ubuntu, everything works great and then the Zino shuts down without any warning after about 15 minutes. The power management settings have been adjusted to "Never".

When I run Windows 7, I don't have this problem.

Anyone have any idea why the Zino wants to shut itself down while running Ubuntu?

---

### Post by reiki on 2010-01-05
> **shedberg said:**
> Hello... and help!,

I just got the following Zino HD 

Inspiron 400 with MXM Graphics,with ODD
AMD Athlon 6850e 1.8GHz, 1MB
8GB DDR2 SDRAM AT 800MHZ
ATI Radeon HD 4330 512MB Graphics Card
320GB Serial ATA Hard Drive (7200RPM)

Using HDMI to connect to TV without issue.

It has a dual boot installation of Windows 7 Home and Ubuntu 9.10.

When I run Ubuntu, everything works great and then the Zino shuts down without any warning after about 15 minutes. The power management settings have been adjusted to "Never".

When I run Windows 7, I don't have this problem.

Anyone have any idea why the Zino wants to shut itself down while running Ubuntu?

I have almost the exact same Zino but mine has the 750gig hard drive. 
Are you saying Ubuntu shuts down as in... a normal shutdown? Or is the machine turning off?

Mine works fine and I didn't touch any power management settings.

---

### Post by shedberg on 2010-01-05
The Zino just shuts off. I can then restart it, everything reboots normally, but then after about ~15 minutes the same thing happens again.

---

### Post by jrb114 on 2010-01-20
Hi,

I'm considering buying one of these Zino HDs.

I've noticed <reiki> only had problems with the rear headphone jack, which doesn't sound (excuse the pun) too severe, although others seem to have had different stories.

Of particular concern is the fact that I live in the UK, so Dell don't ship Zino HDs here with pre-installed Ubuntu. (Do they anywhere?)

I'm /reasonably/ happy to tinker to get it to work, but I'd rather it was more straight forward. (Perhaps Dell are just waiting for 10.04?)

I'd appreciate any further feedback or recommendations for alternatives to the Zino, if you have the time.

Many thanks,

J

---

### Post by candlerb on 2010-01-21
I'm very happy that I chose this device. It's fast, small and unobtrusive. I've had no problems with graphics using the proprietary driver which 9.10 installs, and a HDMI-DVI cable works fine into my monitor.

Downsides:
* suspend can lock up the machine, not usable
* USB2 doesn't work with my camera (workaround: force USB1)
* unable to use rear sound port (workaround: plug into front)
* shrinking the Windows 7 partition below 50% requires use of free-trial commercial software (blame Microsoft, not Dell)

I got the £329 bundle with dual-core processor, 3GB, 500GB, wireless keyboard and mouse. I didn't buy the Dell wireless card so I can't say whether that works or not under Ubuntu.

---

### Post by jrb114 on 2010-01-21
Thanks very much for the review. I'm seriously considering getting one.

---

### Post by reiki on 2010-01-21
> **candlerb said:**
> 
* shrinking the Windows 7 partition below 50% requires use of free-trial commercial software (blame Microsoft, not Dell)

I have the 750GB drive. When I bought my Zino it had Windows 7 Home Premium 64-bit on it. I used the Windows 7 disk utility to shrink the partition to 100GB. So I mae it quite a bit smaller than 50% and it worked just fine. I was honestly a bit surprised to find that Windows 7 could shrink its own active partition while running. :)

---

### Post by candlerb on 2010-01-22
> **reiki said:**
> I have the 750GB drive. When I bought my Zino it had Windows 7 Home Premium 64-bit on it. I used the Windows 7 disk utility to shrink the partition to 100GB. So I mae it quite a bit smaller than 50% and it worked just fine. I was honestly a bit surprised to find that Windows 7 could shrink its own active partition while running. :)

Then you're lucky. Perhaps I had played about with Windows 7 a little too much before shrinking it, but it wouldn't let me go below 250GB. I spent some hours trying to do it without resorting to commercial software, following these guidelines:
[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)

Still there must have been something halfway up the disk which wouldn't budge. The trial version of Perfect Disk sorted it with no problems.

So my suggestion would be for people with a new machine: boot into Windows 7 and shrink the partition *immediately*. Don't start up Internet Explorer, and ignore all prompts suggesting you activate the free antivirus or any other software bundled.

---

### Post by Toastie0815 on 2010-01-24
> **gamx said:**
> 
I was thinking of buying one to use as a HTPC/NAS. I have seen that power consumption is quite modest (65W). I wonder how low power consumption can be when idle. Any ideas?

Gamx

My Zino HD (Athlon X2 3250e) has 32W in idle and around 45W during startup. (measured with []"]VOLTCRAFT ENERGY-LOGGER 4000]("http://www.zanox-affiliate.de/ppc/?14487869C108954474T&ULP=[[125335))

I expect even less power consumption, but unfortunately CPU freq scaling don't work for me. If you've any suggestion or if it works for you, please post to [this]("http://ubuntuforums.org/showthread.php?p=8716115") thread:
[http://ubuntuforums.org/showthread.php?p=8716115](http://ubuntuforums.org/showthread.php?p=8716115)

---

### Post by Toastie0815 on 2010-01-24
> **jrb114 said:**
> 
I'd appreciate any further feedback or recommendations for alternatives to the Zino, if you have the time.


During the journey looking for a device hosting some basic server applications (mainly file and web server) I came across the Dell Zino HD. The system offers me exactly what I was looking for: A CPU supporting virtualization, 3.5" HDD (for 1 TB or more disk space) and energy efficiency.     In addition I've considered following: 

[LIST]
[*][QNAP TS-119 NAS]("http://www.qnap.com/pro_detail_feature.asp?p_id=112") (brilliant, but I didn't feel comfortable to have my private data and the public web server running on the same machine with separation using virtualization)
[*][Mac mini]("http://www.apple.com/macmini/") (nice, but too expensive and no 3.5" HDD)
[*][Fit PC]("http://www.fit-pc.com/") (poor availability, no integrated 3.5" HDD)
[*]Notebook (integrated USV ;-), but expensive, and no 3.5" HDD)
[/LIST]
Unfortunately I've still a [issue]("http://ubuntuforums.org/showthread.php?t=1389281") with frequency scaling what currently prevents that the system fulfills my energy efficiency requirement.

---

### Post by jrb114 on 2010-02-02
Just wanted to add further thanks to all for their comments.

I'm still a bit undecided, the show stoppers being the apparent lack of frequency scaling on the AMD cpu (which seems to be a wider problem than just the bios---https://bugs.launchpad.net/linux/+bug/364156) and the ever unpredictable suspend issue.

I suspect these issues will be fixed, eventually, since that's what happened previous laptops I've worked with. 

It's just a shame that there aren't more similar style machines that aren't chronically underpowered/ugly/expensive.

Thanks again, J.

---

### Post by Toastie0815 on 2010-02-03
> **jrb114 said:**
> 
I'm still a bit undecided, the show stoppers being the apparent lack of frequency scaling on the AMD cpu (which seems to be a wider problem than just the bios---https://bugs.launchpad.net/linux/+bug/364156) and the ever unpredictable suspend issue.


Thanks for linking the bug on launchpad. I've followed another one, but this is more promising.

_Short update:_

[LIST=1]
[*]Contact Dell Ubuntu Support Hotline in Germany: Dell Zino is not supported for Linux according to the hotline :-(
[*]Contacted Dell via E-Mail #1: Same answer as for 1. :-(
[*]Contacted Dell via E-Mail #2: I've mentioned that the box also don't scale with Windows 7 --> They will forward my request to technical support and may provide a bios update -- let's see
[/LIST]

---

### Post by carrot71 on 2010-02-17
zino400 audio driver on XP works now:
zino400 has the same driver from zino300, which works on xp (tks parke).

so get the driver from dell:
[http://support.dell.com/support/downloads/driverslist.aspx?c=us&cs=19&l=en&s=dhs&os=W732&osl=en&catid=&impid=&SystemID=INSP_DSKTP_300](http://support.dell.com/support/downloads/driverslist.aspx?c=us&cs=19&l=en&s=dhs&os=W732&osl=en&catid=&impid=&SystemID=INSP_DSKTP_300)

if u cant access it, the name of the file is
R230689.exe

and can be found at
[http://ftp.dell.com/audio/](http://ftp.dell.com/audio/)

have not tested hdmi sound yet.

---

### Post by xcruckx on 2010-03-02
Has any one had any problems with the live cd or the live usb completely freeze about 10 minutes into use with the Zino HD? I had it happen to me about twice, really everytime i used the live cd or the live usb. 

The disheartening thing is that this freeze up seemed to fry my hard drive, because i couldn't get the computer to reconize it after the freeze up.

Any one have any insight into this?

---

### Post by reiki on 2010-03-03
> **xcruckx said:**
> Has any one had any problems with the live cd or the live usb completely freeze about 10 minutes into use with the Zino HD? I had it happen to me about twice, really everytime i used the live cd or the live usb. 

The disheartening thing is that this freeze up seemed to fry my hard drive, because i couldn't get the computer to reconize it after the freeze up.

Any one have any insight into this?

Sounds like a hardware issue and not related to the liveCD or liveUSB. I used the liveCD on my ZinoHD for quite a while before I did the actual install.

---

### Post by xcruckx on 2010-03-04
> **reiki said:**
> Sounds like a hardware issue and not related to the liveCD or liveUSB. I used the liveCD on my ZinoHD for quite a while before I did the actual install.

Did you happen to turn on the wireless driver while you were trying the live cd out? because i did, and i wonder if that had anything to do with it. I doubt it very seriously, i think i just happened to get a lemon.

---

### Post by Toastie0815 on 2010-03-10
I've figured out meanwhile (AMD confirmed) that Cool'n'Quite don't work with the 3250e CPU. The 6850e seems to have Cool'n'Quite feature integrated. Could one of the happy 6850e owners please check if your powernow-k8 module loads correctly?

_Following error message should not pop up for:_ ```
dmesg | grep power
[    1.057713] powernow-k8: Found 1 AMD Athlon(tm) X2 Dual Core Processor 3250e processors (2 cpu cores) (version 2.20.00)
[    1.057731] [Firmware Bug]: powernow-k8: No compatible ACPI _PSS objects found.
[    1.057733] [Firmware Bug]: powernow-k8: Try again with latest BIOS.
```_In addtion cpufreq should appear for:_ ```
ls /sys/devices/system/cpu/cpu0/
cache  crash_notes  topology
```How about the fan noise with a 6850e system? Does the fan stop running in idle?
If someone with 6850e system has measured the power consumption in idle I would be interested too ;-)

---

### Post by reiki on 2010-03-12
answered in [http://ubuntuforums.org/showpost.php?p=8953263&postcount=11](http://ubuntuforums.org/showpost.php?p=8953263&postcount=11)

---

### Post by OneMillionMonkeys on 2010-03-14
For the benefit of anyone who is thinking of installing Ubuntu on a Zino HD, I just wanted to post a quick note saying that I installed 9.10 on mine and it worked "out of the box".  I should hasten to add, though, that I haven't checked if the sound is working, nor CPU frequency scaling.  But I didn't need to futz around with graphics drivers, or anything like that.

---

### Post by reiki on 2010-03-15
> **OneMillionMonkeys said:**
> For the benefit of anyone who is thinking of installing Ubuntu on a Zino HD, I just wanted to post a quick note saying that I installed 9.10 on mine and it worked "out of the box".  I should hasten to add, though, that I haven't checked if the sound is working, nor CPU frequency scaling.  But I didn't need to futz around with graphics drivers, or anything like that.

I have 9.10 on mine as well and sound works out of the box EXCEPT I have to plug my speakers into the front jack. The rear jack does not seem to be recognized. HDMI works as well and when you make the HDMI the active sound device, you get sound from the HDMI. So far I'm pretty happy with the ZinoHD.

---

### Post by OneMillionMonkeys on 2010-03-16
> **reiki said:**
> So far I'm pretty happy with the ZinoHD.

Me too.  For my purposes, it seems tough to beat.  I'm setting up a small Linux cluster to run a distributed application.  I just need a half-decent CPU, a half-decent hard drive, and ethernet.  For $250, I'm not sure I can do better, not even if I try to build a system from components.  Even though I'm paying for a copy of Windows that I immediately delete.

---

### Post by reiki on 2010-03-16
> **OneMillionMonkeys said:**
> Me too.  For my purposes, it seems tough to beat.  I'm setting up a small Linux cluster to run a distributed application.  I just need a half-decent CPU, a half-decent hard drive, and ethernet.  For $250, I'm not sure I can do better, not even if I try to build a system from components.  Even though I'm paying for a copy of Windows that I immediately delete.

Instead of immediately deleting it, let it start for the first time and get configured and registered and whatever. Don't install any third-party software. Now use the built-in windows disk tools to shrink the partition that Windows is using. I got mine with Windows7 Home Premium because that was the cheapest choice. I have the 750GB hard drive, shrunk Windows7 down to 100GB, and tehn used the remainder to install Ubuntu.

Why do this?
It just makes it a lot easier to do things like bios upgrades and stuff like that. And I really don't mind having a small Windows partition as I'm often helping people who AREN'T running ubuntu so I can boot to Windows and follow along with what they're doing. I've been using Ubuntu since 2005 so I don't remember all the ins and outs of windows sometimes. 

If it was NOT a factory built machine, I wouldn't have a windows partition. But since it is, it makes it easier to do maintenance when required.

---

### Post by bkayco on 2010-04-13
You're welcome to check out my installation at:

[http://bkayco.homelinux.net](http://bkayco.homelinux.net)

I got fed up with trying to convert old PC's into home servers that I broke down and bought this little Dell Zino.

It was the best thing I ever did.  I can actually work on programming the server instead of installing drivers, and this and that BS, etc....

It's a dual boot Vista/Ubuntu 9.10 system.

It sits on the bottom of our AV cabinet and shares a dongle with my larger CAD/GIS workstation so there is only one screen/keyboard/mouse that is shared.   The Zino is also hooked up to our Big Screen TV through the HDMI outs.  (Other than the video lagging a little for HD quality video, it's awesome.)  We can stream video to the TV through it while it still functions as a personal web server, no problem.  Plus I can control what my 5yo watches on the computer now.

HDMI sound works no problem in Ubuntu.  Vista was tricky to figure out but I have it down now.  (you have to know where to "right click" to turn it on)

I also installed a mapserver testing platform and run MySQL and POSTGIS databases,  
and two webcams(but they aren't shown on the website for obvious reasons).

Good Luck with yours!  Just wanted to let you know IT CAN BE DONE!

---

### Post by cpaige123 on 2010-04-13
how do u create a new post

---

### Post by B34N on 2010-04-13
I've been happy with my Zino as well. Except for a recent issue, which I'll detail below, the only "complaint" is that I can't take the old half mini PCI-E SSD from my Mini9 and put it into this machine. The way that they have the Mini-PCi-E slot that it can only fit something half of the half mini size. Bummer because I only use it for MythTV and I could re-purpose the HD in the machine.

Has anyone had problems with the machine overheating? Last week we had a warm front come through and my house went from 62F to about 74F. After watching HD MythTV content on my Zino for about 45-minutes, it started to overheat. Fortunately the temperatures dropped down again and it seems to be working fine. Dell is also sending a refurbished unit to replace mine. It didn't take much convincing from me so I'm wondering if this is a common issue. My Zino is not in a cabinet and it out in the open with plenty of space behind it.

---

### Post by mbrinkho on 2010-04-28
> **xcruckx said:**
> Did you happen to turn on the wireless driver while you were trying the live cd out? because i did, and i wonder if that had anything to do with it. I doubt it very seriously, i think i just happened to get a lemon.

I've been having problems with my Zino freezing up as well.  I thought maybe I had screwed up the install somehow by putting Zoneminder on it so I reinstalled 9.10 from scratch, updated everytyhing and then after I installed the wireless driver (sudo apt-get install bcmwl-kernel-source) it froze after I tried to login via the GUI.

I ended up having to power it off by holding the button and restarted it and it let me log in.  Seems OK now but I'd like to know why it froze the last time.  This machine is for a client and I'd rather not give it to them knowing it has issues. :(

---

### Post by B34N on 2010-05-11
Is anyone using their Zino as a MythTV frontend? I was for a few months but I must have had a defective unit because it started overheating. Dell sent me a new unit (came with Win 7 even though my original had Vista) and I installed Ubuntu 9.10 on it. I tried 10.04 but the version of MythTV wasn't compatible with my Mythbuntu backend and I'm not willing to mess with the backend at the moment. After installing 9.10 on the new unit, I decided that I would rather use HDMI for video and sound than VGA and the front audio jack (back audiojack didn't work for me before). I needed to use the restricted drivers but I am able to get sound over HDMI except for MythTV. I played around with the MythTV setup/general/audio output device settings but no luck. I have options for ALSA:default, ALSA:spdif, ALSA:surround 5.1, ALSA:analog, ALSA:digital, ALSA:mixed analog, ALSA:mixed digital, ALSA:hdmi, ALSA:plugwi0.3, /dev/dsp, /dev/adsp, Jack:output and NULL. I tried most of those options and I still don't get sound from MythTV. I went to Ubuntu's sound preferences and under hardware I have "RS780 Azalia controller" in addition to "Internal Audio" I have the RS780 checked off for sound output. However, when I play a recording under MythTV, I still see "No application is currently playing or recording audio" under the application tab of the sound preferences screen. What am I doing wrong? If I play sound from something like Pandora.com I see it listed int he applications tab. Has anyone else got MythTV to play sound over HDMI?

---

### Post by B34N on 2010-05-12
I got it working. It seems that MythTV and Pulse Audio do not play well together. All I needed to do was add "export EXPERIMENTALLY_ALLOW_PULSE_AUDIO=1" to my .profile file and now I get all sound over HDMI.

---

### Post by B34N on 2010-05-14
Is anyone else using their Zino as a MythTV frontend? Is so, are you having overheating problems?

My Zino overheats after approximately an hour of playing 720p content as a MythTV frontend. The box is out in the open so it has plenty of room to breath. Dell replaced the Zino once and after one day of use the replacement is experiencing the same problem. I called tech support, they tried upgrading the BIOS from A01 to A01 and they then decided to offer me three options:
[LIST]
[*]Replace defective part (I wonder which part is defective)
[*]Replace entire unit
[*]Refund purchase price
[/LIST]
I went for the replace entire unit option even though it will take 3-4 weeks. They explained to me that the refund option will still be there if the replacement has the same problem.

---

### Post by B34N on 2010-06-01
> **st8ofmi9d said:**
> Is anyone else using their Zino as a MythTV frontend? Is so, are you having overheating problems?

My Zino overheats after approximately an hour of playing 720p content as a MythTV frontend. The box is out in the open so it has plenty of room to breath. Dell replaced the Zino once and after one day of use the replacement is experiencing the same problem. I called tech support, they tried upgrading the BIOS from A01 to A01 and they then decided to offer me three options:
[LIST]
[*]Replace defective part (I wonder which part is defective)
[*]Replace entire unit
[*]Refund purchase price
[/LIST]
I went for the replace entire unit option even though it will take 3-4 weeks. They explained to me that the refund option will still be there if the replacement has the same problem.


My replacement came and I have the same problem. What I think is overheating is: The screen blanks, comes back, blanks, comes back and then eventually stays blanked until I wait for the machine to cool down. I noticed that this seems to happen even when I just leave the computer sitting idle. I ran "sensors" from the terminal and the highest I have been able to see any of the cores get is 58C. However, even after the cores got back down to mid 40s I still have the same problem. It's VERY annoying and I'm hoping that it's something that I can fix by setting a configuration. I have my second replacement Zino sitting in the box and ready to test.

Maybe it's not the CPU that's overheating since those temperatures don't seem that high to me. I have even taken the cover off and blown a fan directly on the unit. While it delays the onset, I still have the same issue come up.

Any suggestions would be greatly appreciated.

---

### Post by reiki on 2010-06-03
What graphics card do you have? Did you go with the 512MD ATI HD4330?

It almost sounds to me like the GPU is going out. Not the CPU. I've had my core temps as high as 80 to 83C and my Zino HD keeps on chugging along.

You might want to open it up I think from the bottom to see if the graphics card appears to be properly set. My whole unit had to be disassembled and reassembled because it had so many loose scews. If the heat sink for your GPU is not set correctly it WILL over heat and your CPU Core temps may remain fine.

---

### Post by B34N on 2010-06-03
> **reiki said:**
> What graphics card do you have? Did you go with the 512MD ATI HD4330?

It almost sounds to me like the GPU is going out. Not the CPU. I've had my core temps as high as 80 to 83C and my Zino HD keeps on chugging along.

You might want to open it up I think from the bottom to see if the graphics card appears to be properly set. My whole unit had to be disassembled and reassembled because it had so many loose scews. If the heat sink for your GPU is not set correctly it WILL over heat and your CPU Core temps may remain fine.

I have the standard video. The only thing I upgraded from the base unit was the CPU.

I'll try taking it apart. This is my 2nd unit and my 3rd is in a box in my office. The first one ran fine as the temperatures were cool (58-64F) in the house. It only started having troubles as it got warmer out. I use "sensors" to check the CPU temp. Is there an easy way to check the GPU temp?

Also, could the problem be due to an update on the system instead of just the warmer temperature outside?

Thank you.

---

### Post by B34N on 2010-06-11
My 3rd unit seems to be operating normally. However, it has been significantly cooler over the last few days of testing. 

I used "sensors" to check the temperature of the CPU. Is there an easy way to check the temperature of the GPU?

---

### Post by B34N on 2010-06-17
> **st8ofmi9d said:**
> My 3rd unit seems to be operating normally. However, it has been significantly cooler over the last few days of testing. 

I used "sensors" to check the temperature of the CPU. Is there an easy way to check the temperature of the GPU?

I spoke too soon. The third unit has the same exact issue. I am confident that it's a heat problem because it takes longer to happen when the room's ambient temperature is lower. Last night it was 78F in the room and it overheated in 15-minutes. 

To repeat the problem that I'm calling overheating:
The screen goes blank for a split second then returns for a few seconds then blank again and this repeats for 20-30 seconds with the time of the video returning shrinking until eventually the screen stays blank. The problem happens more quickly when I'm playing video but has also happened without playing any video and with my just running commands in a terminal window.

Someone suggested that it may be the GPU and not the CPU. Since I'm on my third unit and it seems that the problem is not very common, it would stand to reason that it's something unique that I'm doing. I'm using the VGA output and it's going to my Dell monitor which is 1366x768. Is that an odd resolution which may be causing my GPU to work harder thus causing it to overheat?

---

### Post by kgiusti on 2010-07-24
I've just bought a Dell Zino - base model (no tuner), but I upgraded to the dual core chip.

I've just installed Ubuntu 10.04 x86-64 (dual boot alongside Vista).  Graphics (X), wireless (installed proprietary broadcom drivers), ethernet all work fine.

I too am experiencing a problem with the rear audio jack.  The front audio jack works fine, but the rear jack produces no sound.   Both jacks work fine under Vista, so it's unlikely to be hardware related.

If interested, I've opened a bug against this:  

[COLOR=#888888][https://bugs.launchpad.net/bugs/609568](https://bugs.launchpad.net/bugs/609568)

-K
[/COLOR]

---

### Post by Paplec on 2010-09-14
> **shedberg said:**
> Hello... and help!,

I just got the following Zino HD 

Inspiron 400 with MXM Graphics,with ODD
AMD Athlon 6850e 1.8GHz, 1MB
8GB DDR2 SDRAM AT 800MHZ
ATI Radeon HD 4330 512MB Graphics Card
320GB Serial ATA Hard Drive (7200RPM)

Using HDMI to connect to TV without issue.

It has a dual boot installation of Windows 7 Home and Ubuntu 9.10.

When I run Ubuntu, everything works great and then the Zino shuts down without any warning after about 15 minutes. The power management settings have been adjusted to "Never".

When I run Windows 7, I don't have this problem.

Anyone have any idea why the Zino wants to shut itself down while running Ubuntu?
Same thing happens to me but not as regularly (not every 15 min.)
Have you found any answers to this problem?
Thanks in advance

---

### Post by reiki on 2010-09-16
My wife told me my Zino was powering off kinda randomly. I've never seen it happen. However, my wife is a teacher and at home all summer AND we don't have air conditioning and our house gets pretty hot.

So I stuck my Zino and external eSATA hard drive on top of one of the USB chill mats. Zino has not shut down since. Makes me wonder if you guys aren't having thermal issues.  Try a chill mat. They're not expensive.

---

### Post by bdoin on 2010-10-08
> **st8ofmi9d said:**
> Is anyone else using their Zino as a MythTV frontend? Is so, are you having overheating problems?


I also have a Zino HD and suffer also the overheating issue. Dell keeps replacing parts every 2 months until something else crash. I hope they will accept a full replacement.

---

### Post by reiki on 2010-10-10
I like my Zino. And I haven't really had issues with it. I *did* send it through my service department when I got it and they tightened up loose screws and generally checked it over pretty well. I think there are build quality issues with the original ones. Not sure if the new model suffers from the same issues or not.

---

### Post by tompit on 2011-02-03
Hi folks,

I'm looking to buy the Zino HD 410. As there is no optical output could you tell me if the sound (surround 5.1) works fine over the HDMI ? I have tried to find some informations about that without any success. 

Many thanks !

---

### Post by tompit on 2011-02-03
My bad, in fact there is an optical output on the Zino HD 410...

---

### Post by reiki on 2011-11-02
I know this is an old thread, but I have an update to the sound issue on the Zino HD.
Recently I switched to Kubuntu. I ran Kubuntu 11.04 and the rear analog sound jack still didn't work. I have upgraded to Kubuntu 11.10 and "Ta-Da!" the rear analog sound jack is working. So, somewhere along the line, something got updated and that rear analog jack is now recognized and functioning in Kubuntu 11.10.

---

