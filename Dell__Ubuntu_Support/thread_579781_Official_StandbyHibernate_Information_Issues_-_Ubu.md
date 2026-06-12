---
title: "Official Standby/Hibernate Information Issues - Ubuntu 7.10"
date: 2007-10-18
forum: Dell  Ubuntu Support
---

### Post by AaronMT on 2007-10-18
Hello,

I think it would be a wise idea to create an *official* thread containing all  the collective data received concerning this issue with Ubuntu 7.10 (Gutsy) rather than have an array of topics and threads posted many times pertaining to duplicate data.

I suppose one collective thread would be better.


On to the problem.

**Problem**

You own a Dell Desktop or Laptop. In my case I own a Dell Inspiron 1501. You installed Ubuntu 7.10 recently, today or last week on a clean install or an upgrade and now your machine is incapable of entering or returning from standby/hibernate.

If so, please post the following information.

**Dell Model (Laptop/Hibernate?)**
**Upgrade or Clean Install**

The goal of this *official* thread is to prevent the repeating of other threads, to collect all information in this thread and to hopefully resolve this issue with 7.10

Please post the information you've collected in this thread.

Moderators, feel free to sticky this.

---

### Post by Dellfan on 2007-10-18
1505 - upgrade - from Tribe 4  to Beta, kept up to date every night  - Suspend and Hibernate both working (have nvida card with restricted drivers with full desktop effects turned on). 

Occasionally have had  to iwconfig/dhclient3 the wireless interface after a suspend. Have not seen that after the latest Network Manager update.

---

### Post by fadain on 2007-10-18
Acer Aspire 5101, upgraded from feisty. Installed latest fglrx driver but still can't hibernate/suspend.

---

### Post by neptho on 2007-10-18
Inspiron 6400 
Both clean and upgrade installations.

If you have an ATI X1300 or X1400: fglrx driver does not work correctly with new memory allocation scheme.  It will crash on attempts to suspend.  There is currently _no workaround_ that does not involve not using the Suspend/Hibernate features of the system; hopefully a future driver update will alleviate this issue.

Solution: Continue using Feisty, or wait for the open source driver to stabilize.

---

### Post by odelay on 2007-10-18
> **neptho said:**
> Inspiron 6400 
If you have an ATI X1300 or X1400: fglrx driver does not work correctly
...
Solution: Continue using Feisty, or wait for the open source driver to stabilize.

Well then, that's terrible news.  Shame, it seems like there's always *something* with Ubuntu & ATI X1300/1400.  Feisty had the LiveCD/Graphical Install issue.  I guess Suspend didn't quite work either, but there was a workaround (which I forgot).

---

### Post by neptho on 2007-10-18
> **odelay said:**
> Well then, that's terrible news.  Shame, it seems like there's always *something* with Ubuntu & ATI X1300/1400.  Feisty had the LiveCD/Graphical Install issue.  I guess Suspend didn't quite work either, but there was a workaround (which I forgot).

This machine is a bear, I'm afraid.  The fix is to add "fglrx" (and ipw3945 if you have an intel wireless controller) to MODULES_WHITELIST in /etc/acpi/acpi-support.

I've fought Gutsy for about a week, and the only viable 'workaround' was to use a non-standard kernel with Gutsy.  I don't feel like rolling my own distribution with customized junk (if you will) on my laptop, so I'm going to wait for it to solidify.. or until I get a Vistro.  :)

---

### Post by outphase on 2007-10-19
Inspiron 700m

Beta - Suspend and Hibernate did not work
RC (via update-manager) - Both worked fine.
Final - Not tested, yet

---

### Post by carac on 2007-10-19
Dell X300 with Dell 1400 wireless mini-pci
Clean installs with both RC and FINAL

[COLOR="Red"]1)[/COLOR] bcm43xx can create problems on restore from both suspend and hibernate; since it also does NOT work OK with Dell wireless 1400 (I believe bcm4324) I have blacklisted bcm43xx and replaced it with ndiswrapper - and now suspend and hibernate works VERY WELL !!! (from applets, menus, CTL+ALT+DEL and even ACPI suspend button)

[COLOR="Red"]2) HOWEVER there is still a problem on the actions of the ACPI LID - no matter how that is set the system will hung on actions related to it !!![/COLOR] (and that is obviously very disturbing since most people are used to go to standby just by closing the lid)!

---

### Post by fredronn on 2007-10-19
**Dell Inspiron 1520**

Suspend to RAM worked a few kernels ago. Didn't work just before release. I did a clean install of the release. Suspend to RAM does not work.

Suspending to RAM does work if I quit X11, however it will not resume properly (display is blank).

---

### Post by phalkon30 on 2007-10-19
> **fredronn said:**
> **Dell Inspiron 1520**

Suspend to RAM worked a few kernels ago. Didn't work just before release. I did a clean install of the release. Suspend to RAM does not work.

Suspending to RAM does work if I quit X11, however it will not resume properly (display is blank).

That was my thoughts on this too. When I installed 7.04 last spring, hibernate/suspend worked. I dont' know when exactly because I don't often use it, but it stopped working on 7.04. When I upgraded to Gutsy, I was really hoping it would fix the problem, but it didn't.

Thought maybe the issue was only my own.

---

### Post by neptho on 2007-10-19
> **fredronn said:**
> **Dell Inspiron 1520**

Suspend to RAM worked a few kernels ago. Didn't work just before release. I did a clean install of the release. Suspend to RAM does not work.

Suspending to RAM does work if I quit X11, however it will not resume properly (display is blank).

I hate to further derail this thread, but hopefully this will also assist others:

What video are you using?  With fglrx, I have to set the screensaver to "Blank" only, as the suspend/resume scripts will lock the screen.  If something that uses GL is running, the machine locks hard and refuses to suspend.

---

### Post by phalkon30 on 2007-10-19
Personally I'm not using a Dell, maybe I should have specified that. I didn't touch any settings related to graphics, other than restricted drivers. How would I be able to tell if I"m using fglrx or other?

---

### Post by brandon30x on 2007-10-19
System:
Compaq V2000 (V2010US) Laptop
512 MB Ram
Intel integrated graphics
Pentium M (centrino)
Dual boot with WinXP

I installed Gutsy fresh from the live CD. When I suspend to ram, it wakes to a black screen and I have to hard power off the laptop. Suspending worked fine in Feisty. Have not tried hibernating yet. But I expect the same behavior. This is my only bug with Gutsy, so I hope I can fix it and have a perfect system! :)

---

### Post by dahen on 2007-10-19
Dell Inspiron 6000
ATI Mobility X300 (M300)
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON X300
OpenGL version string: 2.0.6473 (8.37.6)

Gutsy through stepwise upgrading from Feisty.
Stanby/HIbernate was working in Feisty.
In Gutsy the screen gets black when going to Standby (Suspend to RAM) but computer doesn't go to sleep. It gets stuck on the black screen and there is no way of getting it to unlock. I have to hold down the powerbutton to turn the computer off and then start it normally again.

---

### Post by electronox on 2007-10-19
> **dahen said:**
> 
Gutsy through stepwise upgrading from Feisty.
Stanby/HIbernate was working in Feisty.
In Gutsy the screen gets black when going to Standby (Suspend to RAM) but computer doesn't go to sleep. It gets stuck on the black screen and there is no way of getting it to unlock. I have to hold down the powerbutton to turn the computer off and then start it normally again.

Same exact problem. Worked in Fiesty, updated to Gutsy.

Mobility X700 Running restricted driver
Acer TM8100

---

### Post by Dellfan on 2007-10-19
This is doable... 

Unfortunately I did not document what I tweaked for the lid... definitely was in /etc/acpi... I think events/default. Google is your friend. 

Also need to tweak /etc/default/acpi-support:

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=false

With the tweaks my 1505 with an nvidia card both suspends and hibernates, from the Fn F1/F2 keys and shuts down the display when I close the lid. Come back rorm suspend and hibernate every time.

---

### Post by zotsf on 2007-10-19
Asus W2p
ATI Radeon x1700

Neither suspend nor hibernate worked for 7.04 and still does not in 7.10.

Asus built the thing for Vista...so I bought it and installed ubuntu :)  I won't lie though, I dual boot XP so I can run Adobe apps.

---

### Post by cvr on 2007-10-20
> **AaronMT said:**
> Hello,
**Problem**

You own a Dell Desktop or Laptop. In my case I own a Dell Inspiron 1501. You installed Ubuntu 7.10 recently, today or last week on a clean install or an upgrade and now your machine is incapable of entering or returning from standby/hibernate.

If so, please post the following information.

**Dell Model (Laptop/Hibernate?)**
**Upgrade or Clean Install**



Dell Model: Latitude D820 laptop
Clean install of 7.10

Suspend and hibernate do not work.  Both worked fine in 7.04.  Still I have another partition with 7.04 which is working like a charm.  But largely frustrated since suspend does not work in 7.10.

Radhakrishnan

---

### Post by GoodPanos on 2007-10-20
Tried Dellfan's solution...and a few others but it did not work. :(

System:
Dell Inspiron 8500
nVidia GeForce4 4200 Go (using restricted drivers)
Dell 1400 Wifi (Broadcom 43XX)

Suspend/hibernate thus far on this notebook has not worked with neither Feisty, Suse 10.3 nor PCLOS 2007.

Any other ideas?

---

### Post by finster on 2007-10-20
Suspend issues with Dell Inspiron 6000 (Intel 915GM/GMS, 901GML Express Graphics). Screen blanks when I close the lid but system doesn't suspend.

This was a clean install with Gutsy, Feisty was fine.

---

### Post by OpticalIllusion on 2007-10-20
Dell Inspiron 9300
Nvidia 6800 Ultra (restricted drivers)

Clean install of 7.10 Gutsy Gibbon with Beta and Final Release.

Computer would hang every time when trying to come out of suspend or hibernate.  I've had the same problem with the Beta and the Final.

---

### Post by Starman on 2007-10-20
Latitude D620
I have done both clean installs and upgrades. Suspend worked fine in feisty.

also,

Latitude D400
clean install and upgrade.

](*,)

---

### Post by Passenger on 2007-10-20
Dell Inspiron 6400
ATI Technologies Inc Radeon Mobility X1400
Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

Same problem over here. Screen blanks when suspending, but after that it somehow locks up (bluetooth and power lights both stay on?).
Had it working in 7.04 :(

---

### Post by ultimut on 2007-10-20
> **neptho said:**
> 
What video are you using?  With fglrx, I have to set the screensaver to "Blank" only, as the suspend/resume scripts will lock the screen.  If something that uses GL is running, the machine locks hard and refuses to suspend.

I have an ATI Mobility 9600 and i am using the fglrx driver.  I tried this, but it did not solve my problem.

suspend and hibernate are not working on my 7.10 system.  i upgraded from 7.04 using the upgrade manager and both suspend and hibernate were working on 7.04...  hope we can get a solution to this soon since i am a consultant and often have my computer suspended while i move around...

---

### Post by Jaxilian on 2007-10-20
model: Zepto Znote 2415W
Suspend and Hibernate not working at all in 7.10 (clean install). hangs up with lights on
Both used to work in Feisty 7.04

---

### Post by Childe on 2007-10-20
Model: Toshiba Satellite M55-S1001
Clean install
ATI Radeon Xpress 200M

Neither suspend nor hibernate work.  I'm not sure if this is related, but the bootup screen, with either the scrolling list of details or the loading (or unloading) graph don't show during bootup or shutdown, either.

---

### Post by AaronMT on 2007-10-20
**Official bug listed**

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/121653](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/121653)

---

### Post by Phoenix on 2007-10-20
Model: Dell Latitude D610
Graphics Card: ATI Radeon Mobility X300
Upgrade from freshly installed Feisty to Gutsy. Hibernate and suspend worked in Feisty, attempting them in gutsy simply takes me to a black screen with the harddrive still spinning and the lights still on, have to hold down power button to make system halt.

EDIT: I see the bug report (YAY!) however, it being wishlist seems a bit....off. A lot of people running ubuntu use laptops with ATI graphics and not having suspend/hibernate can really be a showstopper. Suggest upgrading importance from wishlist.

---

### Post by Starman on 2007-10-20
I did a clean install of 7.10 and now suspend is working. This time I did NOT activate the restricted (nvidia-glrx)  Nvidia driver the first time I logged in. This left me using the 'nv' nvidia driver which apparently is NOT impacted by the changes detailed in the bug report.

So now when I close the lid it suspends and when I open the lid...it wakes up...

---

### Post by LibertyShadow on 2007-10-20
I am running Dell Inspiron E1505
**Upgraded** last night from **clean** Feisty install. (There is a long story behind that)
I have an Nvidia Go 7300, and use the binary driver from their site 100.14.19
My wireless card is a Broadcom 1390, and I use ndiswrapper for the driver.

I had to edit the acpi-support file (POST_VIDEO=false}, but I got
**Before upgrade**:
Suspend works / Hibernate did not resume

**After upgrade**
Suspend works, but the network does not resume... ie I have to restart to switch networks
Hibernate shuts the computer down, which is failure to me.

---

### Post by moschops on 2007-10-21
Inspiron 700m with 7.10 RC1 clean install
Intel i855GM graphics with default "Intel experimental mode switching" driver.

Suspend and resume used to work beautifully with Feisty but in Gutsy I get black screen of death - have to power cycle to get machine back.  Probably seems to happen even if I just log out...

Discovered that disabling desktop effects makes things better but hibernate still fails occasionally, and suspend gets scrambled graphics on resume, and I've even see restart fail to shutdown properly so there are definitely some deeper problems with Gutsy.  Its a real shame because as I mentioned Feisty was rock solid in this regard.  

I think going back to the old Intel 810 driver may help me enable the desktop effects and still have suspend/hibernate work but unfortunately I then loose the ability to use my screen in the proper 1280x800 resolution (there is a i955 pacakge that worked in Feisty but I've read it no longer works with Gutsy).  Because this is a laptop LCD panel display I can't really take 1024x768  because it looks really bad and is hard to read text on.  

I really hope there is a patch for these problems soon...

---

### Post by fredronn on 2007-10-21
> **neptho said:**
> I hate to further derail this thread, but hopefully this will also assist others:

What video are you using?  With fglrx, I have to set the screensaver to "Blank" only, as the suspend/resume scripts will lock the screen.  If something that uses GL is running, the machine locks hard and refuses to suspend.

I'm using nvidia-new drivers for the 8600M GT in this laptop. As I said, suspend does work when running hibernate-ram in console. It does resume, but it will not turn on the display. It seems like it would only be the backlight, though, because when I hit the power button afterwards the system responds and Linux shuts down.

Suspend in X will not work.

---

### Post by KeithO on 2007-10-21
I have an Inspiron 8600.  I did an upgrade from feisty which was a clean install.  Suspend and hibernation are unavailable.  When the screensaver kicks on and shutsdown the screen, it does not come back without a hard boot.

---

### Post by kevin79 on 2007-10-21
> **Dellfan said:**
> This is doable... 

Unfortunately I did not document what I tweaked for the lid... definitely was in /etc/acpi... I think events/default. Google is your friend. 

Also need to tweak /etc/default/acpi-support:

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=false

With the tweaks my 1505 with an nvidia card both suspends and hibernates, from the Fn F1/F2 keys and shuts down the display when I close the lid. Come back rorm suspend and hibernate every time.

What do you suggest searching google on? Can you post your /etc/acpi and /etc/default/acpi-support files?

---

### Post by TheodoreWard on 2007-10-21
Latitude D810
ATI Technologies Inc M24 1P [Radeon Mobility X600]

Been using Ubuntu since at lease 6.06 and never had a suspdned or hibernate problem.

Did a clean install of 7.10, turned on restricted drivers (been using XGL or Beryl for at least a year with no problem) suspend didn't work. Usually when I suspend, the power light begins to glow on and off, after this procedure, it would never get to that point, power light stayed on and computer was frozen with a blank screen.

I reinstalled and did not turn on the restricted drivers and suspend works okay (haven't tried hibernate) though it is a bit slower than usual and often when unsuspending NetworkManager dies (takes 100% of CPU) and won't connect. If I kill NetworkManager from commandline and restart it works okay.

---

### Post by __Alex__ on 2007-10-22
XPS m1330 - neither suspend nor hibernate, although it happens that hibernate works once, but if I try to hibernate again, game over... running latest nvidia driver.
Edit clean 7.10 install

---

### Post by hades_6_6_6 on 2007-10-22
Dell Model: Inspiron 1501 laptop
Clean install of 7.10

Suspend and hibernate do not work.
Hibernate worked fine in 7.04 (but not Suspend)

---

### Post by staticsage on 2007-10-22
Dell Precision M60
Nvidia Quadro (using restricted Nvidia drivers from restricted drivers manager)
bcm43xx for wireless (installed from restricted drivers manager)

Gutsy clean install: Both suspend and hibernate do not work.

---

### Post by perstromgren on 2007-10-22
**Compaq Presario 2100**

Hibernate/wake up worked fine in Feisty, but does not in 7.10.

This was an upgrade from Feisty, not a clean install. Only power cycle will do to make computer wake up.

Per.

---

### Post by alex941021 on 2007-10-22
ACER Ferrari 5000

I am running 7.10 and I tried a fresh install, but the system fails to go into standby mode.  It attempts to shut down everything (x windows), the hard drive also spins down, but in the end the power light remains on and the only option that I have left is to do a hard powerdown.

The prior version 7.04 worked fine.

I am wondering if someone from M..T has infiltrated the Linux development community and they are trying to sabotage the development efforts. :-)

Thank you,

alex

---

### Post by ifixit on 2007-10-22
Inspiron 6000d, ATI x300, intel 2915ABG
Clean install

First problem is an apparently known issue between ATI's binary driver and the kernel included with 7.10, which totally prevents suspending.

This was fixed by building a new kernel with SLAB (Ubuntu's old default) enabled instead of SLUB (the new default).  I also upgraded to ATI's latest available driver at the same time, for good measure.

And now, a whole lot of research and compilation later, suspend seems to work almost as it should, instead of merely idling at a black screen with a blinking cursor....

But the second problem is that on resume, the wireless card is gone.  Network Manager can't find it.  It doesn't show up in ifconfig.  It's just gone.

dmesg shows the manner in which things explode:

ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq
ipw2200: Copyright(c) 2003-2006 Intel Corporation
ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
ipw2200: ipw2200-bss.fw request_firmware failed: Reason -2
ipw2200: Unable to load firmware: -2
ipw2200: failed to register network device
ipw2200: probe of 0000:03:03.0 failed with error -5
ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq

---

### Post by ifixit on 2007-10-22
Actually, scratch that --

It turns out that the problem with the intel wireless card was a symptom of the fix for the ATI card, above.  Compiling and installing the new (SLAB) kernel did not populate the correct directories under /lib/firmware, and so the modified kernel didn't know where to find the appropriate firmware images.

Manually copying the intel firmware made things behave nornally again.

To fix:

[I]mkdir /lib/firmware/`uname -r`
cp /lib/firmware/2.6.22-14-generic/ipw* /lib/firmware/`uname -r`[/I]

---

### Post by Skweek on 2007-10-22
Dell Inspiron 1720
nVidia 8600M GT

Clean install of 7.10 amd64, neither Suspend or Hibernate works.

No sound card detected, solved by $sudo apt-get install linux-backports-modules-generic

---

### Post by lurchi on 2007-10-22
> **ifixit said:**
> Inspiron 6000d, ATI x300, intel 2915ABG
Clean install

First problem is an apparently known issue between ATI's binary driver and the kernel included with 7.10, which totally prevents suspending.

This was fixed by building a new kernel with SLAB (Ubuntu's old default) enabled instead of SLUB (the new default).  I also upgraded to ATI's latest available driver at the same time, for good measure.

And now, a whole lot of research and compilation later, suspend seems to work almost as it should, instead of merely idling at a black screen with a blinking cursor....


I experience the same here. After a kernel-build using SLAB instead of SLUB, hibernation works again. 

For your ipw2200-problem, look at /lib/firmware/. You normally can copy or link the old firmware files into a directory named like your current (newly build) kernel ("uname -r").


lurchi

---

### Post by peterx14 on 2007-10-22
**Problem:** Hibernated my desktop (it's useful for desktop users too your know! ;) ) and on wakeup, the screen went back into power save. Mouse-waggling and key-pressing (return, escape) not really helping.. although the num/caps lock keys working so I guess the machine hadn't totally hung (I have sshd enabled so next time I might try to ssh in). I then tried ctrl-alt-F1 (no joy), ctrl-alt-F2 (no joy) and ctrl-alt-F7 ... and the screen wakes up!

BUT... it's completely messed up! It was just displaying "static noise" type stuff... but it was changing and the colour would change sometimes also. It looked like an old analogue detuned TV, except that the image to the monitor was stable (not rolling or anything).

Previously hibernate did work in Feisty (7.04) but about 50% of the time the network (wired) didn't come back up. And previous to that, Dapper? (6.10) worked perfectly. So, I'm not sure about this "upgrading" malarkey!!!

I should mention that I used to use the embedded Intel graphics and I only just added an nVidia card just prior to upgrade to Gutsy.

**Specs:**
Dell Dimension 3000  (Celeron 2.8GHz, 1GB RAM)
PNY GeForce 6 6200 PCI 256MB

Upgrade from Feisty.
Using "nvidia" restricted driver nvidia-glx-new.

---

### Post by staticsage on 2007-10-22
> **peterx14 said:**
> BUT... it's completely messed up! It was just displaying "static noise" type stuff... but it was changing and the colour would change sometimes also. It looked like an old analogue detuned TV, except that the image to the monitor was stable (not rolling or anything).

That describes exactly what happens to me. I didn't post that because I couldn't describe exactly what was happening, but that is it.

---

### Post by greg.hagen on 2007-10-22
GOT IT!

I have Gutsy working with fglrx 8.40, accelerated video and suspend to ram! I added the feisty main restricted repositories and installed the 2.6.20-15-generic kernel and modules, removed the repository, edited /boot/grub/menu.lst to run the older kernel, rebooted, compiled and installed the fglrx kernel module from ati's website using the wiki guide and rebooted.

A kernel downgrade is a really bad way to fix this problem but it WORKS! :D

If anyone is interested I can make a guide.

---

### Post by MeTheOrion on 2007-10-22
ifixit - i have a Dell 6000 with the exact same ATI card (X300) and have suspend and hibernate issues in Gutsy. Can you please elaborate a little on the exact steps you too to rectify this.

Thanx

---

### Post by moschops on 2007-10-22
> **moschops said:**
> Inspiron 700m with 7.10 RC1 clean install
Intel i855GM graphics with default "Intel experimental mode switching" driver.


As an update I switched to the i810 driver and loaded the 915resolution package to tweak my display resolution too 1280x800 as I had with my old Feisty install.  I have also turned on desktop effects (sweet) and as best I can tell both hibernate and suspend/resume are working fine now - at least no abherent behavior in the first day of use.

There was documentation that the 915resolution tweak is not necessary with the latest i810 driver and or Xorg server - instead you're supposed to be able to just put a "ForceBIOS" option in the xorg.conf file to redefine the 1024x768 video mode to 1280x800 (or whatever else applies for your system).  See: [http://www.geocities.com/stomljen/](http://www.geocities.com/stomljen/) - but I wasn't able to get it to work - however at least the 915resolution tweak did work okay in Gutsy.

I wish everyone else good luck with their issues.

---

### Post by Dellfan on 2007-10-22
In reply to kevin79 request:

/etc/acpi/events/default:

> 
event=button[ /]lid.*   
action=/etc/acpi/lid.sh
event=.*
action=/etc/acpi/default.sh %e


/etc/default/acpi-support:

> 
ACPI_SLEEP=true
ACPI_HIBERNATE=true
ACPI_SLEEP_MODE=mem
MODULES=""
MODULES_WHITELIST=""
SAVE_VBE_STATE=true
VBESTATE=/var/lib/acpi-support/vbestate
POST_VIDEO=false
# SAVE_VIDEO_PCI_STATE=true
USE_DPMS=true
# RADEON_LIGHT=true
# DOUBLE_CONSOLE_SWITCH=true
HIBERNATE_MODE=shutdown
LOCK_SCREEN=true
# DISABLE_DMA=true
# RESET_DRIVE=true
STOP_SERVICES=""
RESTART_IRDA=false
ENABLE_LAPTOP_MODE=false
SPINDOWN_TIME=12

End result is suspend & hibernate working on 1505 with Intel 3945 and Nvidia graphics

More info at:
[http://gentoo-wiki.com/HARDWARE_Dell_Inspiron_640m#ACPI:_LCD_ON.2FOFF]("http://gentoo-wiki.com/HARDWARE_Dell_Inspiron_640m#ACPI:_LCD_ON.2FOFF")

---

### Post by aznranndydraman on 2007-10-23
Dell insprion 6000, using ATI Radeon X300, refuse to suspend/hybernate. Booting and rebooting with black screen (X starts after 5 minutes of waiting). All console mode are black screen (Alt+F1-6) but is able to return to X with Alt+F7.

---

### Post by Ltselan on 2007-10-23
Dell Inspiron 710m
Intel Graphics 855GM using the Intel Experimental mode setting driver
Clean Install of Gutsy from downloaded Live CD

Suspend/Hibernate do not work properly by closing the lid nor using the buttons. System goes to a blank screen and the power light remains on. I need to force a power down with the power button to regain the computer.

Both functions worked In Feisty with the buttons, but did not work by closing the lid. Feisty did not recognize the little button by the keyboard that is supposed to cause the system to suspend when the lid is closed.

---

### Post by carac on 2007-10-23
> **Dellfan said:**
> In reply to kevin79 request:

/etc/acpi/events/default:
...



I believe in a clean 7.10 install there is no /etc/acpi/events/default , nor any /etc/acpi/default.sh !!!

Also many of the scripts (for instance sleep.sh) now have a line to check if gnome-power-manager or klaptopdaemon are active and in that case (like 99.99% of the time) those programs are left to choose the action !!! (quick question - where can be found the scripts for the actions for gnome-power-manager ???)

---

### Post by adam0509 on 2007-10-23
Dell ubuntu inspiron 6400 "n" (n is only a stick apposed lol)


Sometimes when I close the laptod, the PC don't return at all, sometime just a little bit, so I have to make a CTRL + ALT + F1 and "sudo halt"


pre-installed Feisty then upgraded to gutsy

---

### Post by teasum on 2007-10-23
Dell Inspiron 8600
Upgraded via internet from Feisty

I use full desktop effects, with the restricted driver (nvidia) for my card.  Suspend or hibernate do not work at all' after selecting them, the monitor blanks, and I end up with the login window (as if I selected 'lock screen').  

This has been a persistent problem for me since Feisty.  If anyone has any ideas, let me know.

---

### Post by Dellfan on 2007-10-23
> **carac said:**
> I believe in a clean 7.10 install there is no /etc/acpi/events/default , nor any /etc/acpi/default.sh !!!

Also many of the scripts (for instance sleep.sh) now have a line to check if gnome-power-manager or klaptopdaemon are active and in that case (like 99.99% of the time) those programs are left to choose the action !!! (quick question - where can be found the scripts for the actions for gnome-power-manager ???)

My system is definitely a stock 7.04 install, upgraded to Tribe3, then Beta, with all updates except the latest Network Manager applied. Only tweaks, that I can recall, are the ones I listed.

Will try and compare against a fresh install and see what the differences are. The bottom line is whatever configuration I have works (with intel 3945 and Nvidia graphics)... :lolflag:

---

### Post by horrendo on 2007-10-23
I have a Dell Latitude D820 with nvidia restricted driver and visual effects at normal.  My experience is that choosing either suspend or hibernate goes to the blank screen with the "Unlock" dialog.

I had a look at the "Official" bug for this and it appears to only relate to ATi cards.  Does anyone know if there is solution for nvidia cards?

My machine would suspend, hibernate and resume just fine with 7.04.  I did a clean install of 7.10, not an upgrade.

Most annoying.

---

### Post by Dellfan on 2007-10-23
One further note... creating a file 99-network-manager.sh in /etc/acpi/resume.d with the following:

> 
#!/bin/sh
/etc/dbus-1/event.d/25NetworkManager restart


seems to resolve the issue with the latest Network Manager sometimes getting confused and thinking that it was reconnected when it was not, after a resume.

---

### Post by fredronn on 2007-10-24
Update. Confirmed Working!

Machine: Dell Inspiron 1520 (Nvidia 8600M GT)

Suspend is working for me! I'll describe the process:

Full reinstall (deleted everything, including home directory)

Installed linux-backports-modules-generic, rebooted, Sound works!

Ran X using the nv driver for a while. Machine suspended, but would not turn on backlight on resume.

Installed nvidia-glx-new, ran nvidia-glx-config enable, rebooted. Nvidia driver worked, X loaded fine.

Suspend? Works! Resume? Works!

---

### Post by Passenger on 2007-10-24
> **greg.hagen said:**
> GOT IT!

I have Gutsy working with fglrx 8.40, accelerated video and suspend to ram! I added the feisty main restricted repositories and installed the 2.6.20-15-generic kernel and modules, removed the repository, edited /boot/grub/menu.lst to run the older kernel, rebooted, compiled and installed the fglrx kernel module from ati's website using the wiki guide and rebooted.

A kernel downgrade is a really bad way to fix this problem but it WORKS! :D

If anyone is interested I can make a guide.

I've also tried this method on my Dell Inspiron 6400 (ATI x1400) and it works like a charm!

---

### Post by djRob on 2007-10-24
If you have ATI graphic card, complain to ATI about their crappy driver, here is the link
[http://support.ati.com/ics/survey/survey.asp?deptID=894&surveyID=508&type=web](http://support.ati.com/ics/survey/survey.asp?deptID=894&surveyID=508&type=web)

---

### Post by paulten on 2007-10-24
Dell m1330.
Suspend and hibernate works.

After a resume, I get no sound from the speakers.. Everything looks normal, no error messages in the log.
Any hints on this problem?

```

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

```


Paul

---

### Post by kevin79 on 2007-10-24
Dell Latitue D820 with nVidia Quardro card.

I did an upgrade from 7.04 (64bit Kubuntu) to 7.10 (same) and suspend/hibernate did not work. In 7.04 suspend worked but hibernate did not.

I just finished doing a clean install and both suspend and hibernate work now. I'm using whatever video driver came with the distro.

---

### Post by shift1186 on 2007-10-24
Dell XPS M170 - Suspend/Hybernate does NOT work.

The power lights does the normal dimming to show it is in Standby mode, but when i open the laptop up and press Power, it acts like it is comming up.  Screen flickers for a moment, but never comes on.  I tried manually going to screens F1 through F7 with no luck.

This is a fresh 7.10 Live CD Install.

Currently working on installing the latest Nvidia drives but habing many problems.  Will post back if they fix the problem.

---

### Post by mushroomcloudwarrior on 2007-10-24
Dell Vostro 1500

Ubuntu Gutsy 7.10 fresh install.

Computer incapable of Hypernating or standby

---

### Post by prismatic7 on 2007-10-24
Dell XPS m1210, Nvidia GFGo7400 - suspend worked just fine in Feisty but fails in Gutsy. The laptop does not suspend or hibernate at all - display fades and blanks correctly, but fans and hdd are still running, and the power light remains steady (rather than flashing)

On opening the lid, nothing happens. The only way out is to hit and hold the power button until the laptop powers off.

I've tried the uswsup tip [here](http://ubuntuforums.org/showthread.php?t=471855&highlight=nvidia+suspend),  the acpi tweaks [here](https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend) and the fix marked for the Latitude D820 [here](http://koon.fr/wiki/suspend_to_ram_on_the_dell_d820_proprietary_nvidia_drivers_under_ubuntu_gutsy) with no success.

This is a clean install of Gutsy with no other customizations than the Nvidia binary driver (although suspend/hibernate fail with the nv driver as well).

---

### Post by evilmigit14 on 2007-10-24
dell inspiron e1405, intel 950 video accelerator

fresh install

when hibernating, the machine appears to shut down, then comes back up with text filling the screen, unlock screen appears
suspend works, but there are network issues upon resume.

---

### Post by Dellfan on 2007-10-25
Try adding a file to /etc/acpi/resume.d

99-network-manager.sh:

> #!/bin/sh
/etc/dbus-1/event.d/25NetworkManager restart


with the following ownership/permissions:

-rwxr-xr-x 1 root root 55 2007-10-23 20:58 99-network-manager.sh

This will restart the Network Manager on resume, which should resolve your network issues.

---

### Post by kevin79 on 2007-10-25
Update:

I installed the latest nVidia driver using Envy and now Suspend and Hibernate are both broken. When I suspend, it shuts down fine but when I turn it back on, my video doesn't come back up. I'll keep playing with it and see if I can't get it working again.

Update again:

I have at least suspend working again. I used the links provided by primatic7. I'm not using Compiz yet, but I'll be trying that later this week.

---

### Post by alchemistz06 on 2007-10-25
M1210 with Geforce 7400 Hiberanate and Suspend don't work with Compiz Fusion and Latest Nvidia driver installed with Envy.  It works when i deactivate Compiz Fusion. This sucks. I hope they fix it. I can't live without suspend. Everything worked great in Fiesty.

---

### Post by jkoyle on 2007-10-25
Dell 820 using nvidia-new - Suspend/Hibernate both work

Modify /etc/default/acpi-support:
    SAVE_VBE_STATE=false
    POST_VIDEO=false

Append to /etc/modprobe.d/blacklist:
    blacklist intel_agp
    blacklist agpgart

Modify xorg.conf Device Section to include:
    Option "NvAGP" "1"

Here's the relevant section from my xorg.conf:
Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    Option "NvAGP" "1"
    Option "XAANoOffscreenPixmaps" "true"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro NVS 110M"
EndSection


That's it.  I can validate that it was not working prior to the above changes.

John

---

### Post by seanhvw on 2007-10-25
IBM T43
Laptop freezes booting up at the Ubuntu scroll bar. All patches installed running Beta with most recent updates.

---

### Post by RangerDanger on 2007-10-26
Vostro 1700 fresh Gutsy install.  Suspend and Hiberbate work great, nothing needed to be done at all.

---

### Post by dacg on 2007-10-26
Dell C400
Clean install.

 Returning from suspend sometimes gives me a blank screen and sometimes gives me a correct looking desktop but as soon as an item is clicked on the machine freezes up.

---

### Post by joker2of5 on 2007-10-26
I have a Dell Inspiron 1420 that came pre-loaded with Fiesty 7.04.

The first time I tried to Hibernate the system it resumed with no sound working.

I ran alsamixer from the terminal and found that all my sound channels were muted except the main channel.  When I unmuted these the sound worked fine.  After that the hybernate and the suspend both  seemed to work fine but took a long time to resume.

A few days ago I upgraded to Gutsy 7.10 and I had some problems with my monitor which are now resloved.

The hybernate and suspend functions actually seem to be working better now than before, when I use the power down menu.

When I close the lid, though, I get the error message:

Action forbidden policy timeout is not valid.

this happens for any action I specify in the power management for closing the lid.

---

### Post by alexander.forster on 2007-10-26
brand new inspiron 1521
hibernate/suspend doesnt work, everything else seems to 

fresh install of 7.10

---

### Post by Odium on 2007-10-26
Dell XPS M1710
Ubuntu 7.10 [Clean Install]
Problem getting out of Standby

---

### Post by GoodPanos on 2007-10-27
Hallelujah! :guitar: 

Thank you **prismatic7**!  I got Suspend to work from one of your [links]("https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend").  Hibernate does not work though, but that's okay.  I am happy with just Suspend working.

---

### Post by black_magician on 2007-10-27
Dell Inspiron6000
Suspend: no
Hibernate: no

---

### Post by CycleGeek on 2007-10-27
> **moschops said:**
> As an update I switched to the i810 driver and loaded the 915resolution package to tweak my display resolution too 1280x800 as I had with my old Feisty install.  I have also turned on desktop effects (sweet) and as best I can tell both hibernate and suspend/resume are working fine now - at least no abherent behavior in the first day of use.

There was documentation that the 915resolution tweak is not necessary with the latest i810 driver and or Xorg server - instead you're supposed to be able to just put a "ForceBIOS" option in the xorg.conf file to redefine the 1024x768 video mode to 1280x800 (or whatever else applies for your system).  See: [http://www.geocities.com/stomljen/](http://www.geocities.com/stomljen/) - but I wasn't able to get it to work - however at least the 915resolution tweak did work okay in Gutsy.

I wish everyone else good luck with their issues.

I've got the exact same system but going to the i810 driver (via System --> Administration --> Screens and Graphics) screws me when I try to reload.  Only way to fix it is to roll back xorg.conf from the backup.

---

### Post by moschops on 2007-10-27
> **CycleGeek said:**
> I've got the exact same system but going to the i810 driver (via System --> Administration --> Screens and Graphics) screws me when I try to reload.  Only way to fix it is to roll back xorg.conf from the backup.

Ditto here, although it looks real nice I quickly found that the configuration dialog is really unreliable for me.  If your driver works as is out of the box I expect you may have some luck using the configurator to change monitor settings and the like.

Anyway what I recommend is using 

```
sudo dpkg-reconfigure xserver-xorg
```

either from the command line or by botting in recovery mode if your graphics are already screwed up.  For the 700m have it auto detect your adapter and pick the i810 driver instead of the defaul Intel.  That should be enough to get you booted in 1024x768 mode.

To get the right video resolution you need to 

```
sudo apt-get install 915resolution
```

then edit /etc/default/915resolution to contain:

```

MODE=auto
XRESO=1280
YRESO=800
```

and reboot... all should be well.

In case you still have problems with the xorg.conf I have attached my current working xorg.conf as xorg.conf.txt.

---

### Post by jellystones on 2007-10-27
Laptop Model: Dell 640m (E1405)

Brand new fresh install of Gutsy Gibbon.

The ability to wake-up from suspend works only half the time. All the other times, I get a blank screen and I have to manually power the machine off.

---

### Post by rozen on 2007-10-27
Dell XPS 410, Navidia 7300, Dell 2707WFP monitor and nvidia-new.

I made the changes suggested by jkpoyle:

Modify /etc/default/acpi-support:
SAVE_VBE_STATE=false
POST_VIDEO=false

Append to /etc/modprobe.d/blacklist:
blacklist intel_agp
blacklist agpgart

Modify xorg.conf Device Section to include:
Option "NvAGP" "1"

Unfortunately, suspend did not work reliably. It would work a few times and then it would show a black screen with a dead keyboard although the mouse would work.  

I found a link suggesting that one should downgrade from nvidia-new.  I tried doing that using synaptic but had problems doing that.

I would appreciate any suggestions.

Thanks in advance.

Don

---

### Post by prismatic7 on 2007-10-28
> **GoodPanos said:**
> Hallelujah! :guitar: 

Thank you **prismatic7**!  I got Suspend to work from one of your [links]("https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend").  Hibernate does not work though, but that's okay.  I am happy with just Suspend working.

Damn! How come everyone else gets their suspend to work with those links and it doesn't work for me?!

---

### Post by Ergogirl on 2007-10-28
Dell Dimension 4400
Upgrade from Feisty.

Luckily I get no crashes or black screen of death; it simply ignores me when I click on the Suspend or Hibernate actions.

I guess I can live with it as the upgrade fixed a LOT of annoying issues I was having with Feisty.  Always a tradeoff, eh?


Edited to add: weirdly enough, the Suspend and Hibernate functions DO work perfectly if I select them from my desktop while logged in, but they don't work if I am NOT logged in and select them on the main login screen.

---

### Post by Nesmontu on 2007-10-28
Dell Vostro 1000 with ATI Radeon XPress 1150 - using the fglrx driver from the restricted drivers manager.
Both suspend & hibernate worked in Ubuntu Feisty (64bit), and both are now broken in Gutsy :(

---

### Post by bluedragon436 on 2007-10-28
I also had everything working fine with 7.04, but since completely installing 7.10 and setting everything up my hibernate/standby doesn't work.  It did work with 7.04  I have a Dell D610

---

### Post by alchemistz06 on 2007-10-28
> **rozen said:**
> Dell XPS 410, Navidia 7300, Dell 2707WFP monitor and nvidia-new.

I made the changes suggested by jkpoyle:

Modify /etc/default/acpi-support:
SAVE_VBE_STATE=false
POST_VIDEO=false

Append to /etc/modprobe.d/blacklist:
blacklist intel_agp
blacklist agpgart

Modify xorg.conf Device Section to include:
Option "NvAGP" "1"

Unfortunately, suspend did not work reliably. It would work a few times and then it would show a black screen with a dead keyboard although the mouse would work.  

I found a link suggesting that one should downgrade from nvidia-new.  I tried doing that using synaptic but had problems doing that.

I would appreciate any suggestions.

Thanks in advance.

Don

This has made my suspend work so far. On the last three tries so far. I'm pretty stoked. My system M1210, Envy, Nvidia Ver. 100.14.19. Also running Compiz-Fusion.

---

### Post by adohall on 2007-10-28
Dell 8600; 1900x1200 resolution;  nvidia card

Wake from suspend produces blank unresponsive screen in Ubuntu 7.10. The same thing happened with 7.04. Both were fresh installs.

I've never tried any workarounds or kernel tweaks to get this working.

I might try the initial suggestion in another thread, suing uswsusp.

---

### Post by DarqueWing on 2007-10-29
I have a Dell Inspiron 700m laptop, with an upgrade from Feisty to Gutsy.  It's gone through stages of problems with Standby mode - I'm not sure about Hibernate, as I don't use it.

First, it simply refused to go into Standby - both the hotkey combination (Fn+Esc) and the menu command were non-functional.  That lasted a few days.

Then it would go through a nearly-complete shutdown, but then it would hang on a black screen with the power still on - holding down the power key was the only thing that would finally shut it down.

For the last several days now, it has gone into Standby successfully.  When coming out of Standby, however, I have the usual password screen, and then after inputting the password, I get either a normal mouse icon on a completely black screen, or a screen full of graphical artifacts (red background with black and white static once, for example).  It appears that it's only the display that isn't working - programs are still running, windows are still functional, and commands still run - I can still start Rhythmbox because I know exactly where the button is, for example.

I haven't done anything at all yet to alter the Standby characteristics or to try to fix the problem, so it's worth noting that it's gone through these stages without any input from me.  It may or may not have anything to do with the updates that have been performed - I haven't kept notes.  The only real fix I've had to do was the resolution trick discussed previously in this thread for another 700m.

Also, it does occasionally go into and out of Standby properly, although of the last five times I've put it into Standby, it's manifested the black screen, so maybe it's finally stabilized on that one problem.

This weekend, I will likely try a fresh install of Gutsy to see if that might help, although judging from this thread, I'm not so sure anymore.

---

### Post by ewinslow on 2007-10-30
Dell Inspiron 6000  ATI Mobility Radeon X300

Clean install of 7.10

Hibernate and Suspend do not function. Blank screen action needing a hard shutdown with the power button.

Bummer.

---

### Post by bluedragon436 on 2007-10-30
I have the same issue as ewinslow.....  it is rather annoying to have to hard shutdown as I know it isn't good for the hardware

---

### Post by Ricket on 2007-10-30
Dell Inspiron E1705
Clean install of 7.10

Haven't tried hibernate, don't plan to ever use it.

Standby usually works, but I have seen two problems. One was the network issue, where, upon wakeup, the network manager thinks it's still connected and won't be convinced otherwise, resulting in no internet connection without restarting the computer; I applied the fix mentioned earlier in the thread (adding 99-network-manager.sh to resume.d) and it seems to work, but I'll report back if I see the problem again.

But my second issue is weird. It happened for the first time on 7.10 this morning, and it used to happen with 7.04 pretty frequently. I've resumed from standby probably 10-15 times since 7.10 so as you can tell, this is infrequent. Basically, I open the lid and the computer wakes up as it's supposed to, but instead of resuming to the lock screen (where I then type my password and use the computer), it boots as if from a cold boot; the BIOS loads, and then Ubuntu boots, as if it weren't in standby at all. Naturally all running programs and data is lost too.

I'm pretty new to Ubuntu. I don't know what kind of logs to look in or whatever, but someone please let me know how I can log this weird behavior and figure out the cause of it.

Otherwise, standby has worked great, which I'm really happy about because I could never get 7.04 to wake from standby to anything usable (it would always wake to a black screen with a mouse and about a 50x50 px square of jumbled mess around the mouse, the mouse would not move, nothing would work, and I would have to cut power).

Oh, and I'm using the drivers from the restricted drivers manager; I think they are nvidia-glx-new or something like that. And I have desktop effects enabled (yay desktop cube!).

So, please let me know how to log the standby and resume so that I can find out the source of this weird cold boot behavior!
~Ricky

---

### Post by TheSe7enthSin on 2007-10-30
Model: XPS M140
Standby/Hibernate: Both Don't Work
Clean or Upgrade?: Clean Installation

---

### Post by petay on 2007-10-30
I have a dell latitude D500 pentium m 1.3Mhz - 1.2gb ram - intel Gcard

I tried a fresh install of 7.10 and had no suspend (didnit try hibernate) and it wouldn't even shut down!!!

Restored my backup of 7.04 and tried the update via tinternet. Suspend worked, but I had the network problem (just added 99-network-manager.sh which should fix it :D ).

Either theres newer files available via the online update, or theres still files left over from 7.04 that are fixing the problems???

:edit:
Just been forced to standby due to a flat battery and I could not get back :( I got a little box of 'static' and a mouse pointer. tried ctrl+alt+backspace which restarted x, but on logging in, the graphics go's screwey and it all locks up. Try going through the F keys to get a terminal to try and investigate, and it locks up after log in. :'(

---

### Post by atlascomplete on 2007-10-30
HP Pavillion Laptop.

Can enter Hibernate/Suspend, but cannot exit. Computer turns back on, but screen turns blank.

---

### Post by herbster on 2007-10-30
7.10 on P4 EE 3.4ghz, 1.2gb ram, 2 x 320gb sata, m-audio 7.1 card, nvidia 7600 GS

Hibernate/Suspend issue has not changed at all, it's mainly the sound. Everything restores just fine, but the sound is dead. The moment I turn it back on from hibernate there's a lot of hissing from my speakers, then it stops when I get into my session.

It's *almost* there...

---

### Post by dacap06 on 2007-10-30
Dell Inspiron 5100 running Kubuntu 7.10.  When I hibernate, it stops successfully, it starts successfully, but the network connection is hammered.  To get my networking restarted, I have to (as root):

a) issue an /etc/init.d/networking stop

b) issue ps -aef | grep wpa to find the PID of the WPA supplicant.

c) issue a kill -9 <WPA Suppicant PID> to kill the supplicant.

d) start the supplicant again using /sbin/wpa_supplicant -B -iath0 -c/etc/wpa_supplicant.conf

e) issue an /etc/init.d/networking start to start the network.

And even then I usually have to reissue my default route (I used fixed IP addresses on my home LAN -- DHCP won't even register after the restart from hibernation).

---

### Post by donallen on 2007-11-01
Thinkpad Z60

Same issue as many others have reported. Suspend was working with 7.04, upgraded to 7.10, and now attempts to suspend result in what appears to be the machine hung trying to suspend, and recovery is impossible -- must reboot to unwedge the machine. Pretty disappointing.

/Don Allen

---

### Post by Paladin Michael on 2007-11-02
> **Dellfan said:**
> This is doable... 

Unfortunately I did not document what I tweaked for the lid... definitely was in /etc/acpi... I think events/default. Google is your friend. 

Also need to tweak /etc/default/acpi-support:

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=false

With the tweaks my 1505 with an nvidia card both suspends and hibernates, from the Fn F1/F2 keys and shuts down the display when I close the lid. Come back rorm suspend and hibernate every time.

I'm using a Dell Latitude D820 Laptop with a nVidia G72M [Quadro NVS 110M/GeForce Go 7300] as shown in 
KInfoCenter, running Kubuntu 7.10 Gutsy,  (edit) - I forgot to mention, I'm using the restricted drivers so my GL screensavers work.  I'm a graphics whore :)

I can confirm the modification to the /etc/default/acpi-support file in setting POST_VIDEO to false has allowed suspend to function properly for me.  I didn't have to tweak for closing the lid, just used settings in the power manager which was installed by default from the live DVD. (edit) - I lied, it worked before, but now lid isn't causing the configured action.  Oh well, I'll fix it later.

Also, though hibernate previously did not work for me, I looked around a little and found an implication that the swap partition may be where the memory contents are stored during hibernation and noticed that my swap partition was about half the size of my total physical memory.  After modifying my system so that my swap partition was over 1.5 times the size of my memory (tried for double but flubbed my calculations) hibernate now works.  

Note that it is **very** difficult to re-size the swap partition if you are using a logical partition within an extended partition which doesn't have any free space left inside of it.  I couldn't figure out a way to do it using QTParted  I ended up backing up my home folder and reinstalling rather than spend a large amount of time on the idea.

---

### Post by knowledge_is_power on 2007-11-02
Using Dell Inspiron 1501 neither hibernate or suspend work.  Also, wireless will not connect at school which is both wierd and annoying.

---

### Post by netlogic on 2007-11-02
The suspend doesn't work, but hibernate works for me. It used to work on Feisty Fawn.

Toshiba A135-S4656
Graphics 	Intel® Graphics Media Accelerator 950
Wireless Networking 	Built-in Atheros high-speed wireless LAN

---

### Post by vaxius on 2007-11-03
If any of you are using ATI (maybe it works for nVidia too?) I have a howto over at my blog showing how to recompile the kernel with SLAB, which seems to be the only fix until ATI/nVidia learns to play nice with SLUB.

[http://blog.vaxius.net/?p=19](http://blog.vaxius.net/?p=19)

---

### Post by bluedragon436 on 2007-11-03
Yeah I imagine as a complete fresh install you are missing some files that you would have that may fix some of these issues if you had just upgraded from 7.04...I didn't try it after I had updated, and now I have done the fresh install so I don't have 7.04 on there to try it again.  I have been searching and still can't find a fix for the no hibernate/standby issue...and it is kind of annoying...I just shut the computer down instead of allowing it to go into standby since when it does finally go into standby (leaving it sit for 20mins or so) it won't come back out of it I have to completely kill power to it and undo the battery and restart it...but by trying to get it to either hibernate or standy it won't do it...

---

### Post by viking777 on 2007-11-03
Evesham Voyager c530rd with a fresh install of Gutsy Gibbon Tribe 2 continually updated since then, although the version of Ubuntu doesn't really make any difference because it is the same on every version of Linux I have ever tried.
ATI Radeon Mobility X1600

Shutdown - doesn't, you have to use the power button.

Hibernate - never recovers.

Standby - never recovers.

Ctl/Alt/Backspace - does not restart the graphical interface, just hangs.

In fact the only thing it does do is to reboot. I suppose I should be grateful for small mercies!!

---

### Post by carolinamagi on 2007-11-03
IBM Thinkpad T42

Using the "out of the box" graphics driver I can go into hibernation but when I attempt to log in my keyboard doesn't work. Because I am unable to type my password in I cannot log in.

I have not tried suspend yet.

When I downloaded the new ATI drivers, or used XGL, hibernate nor suspend worked properly.

Hope this helps.

---

### Post by stara on 2007-11-03
* First *
sudo gedit /etc/initramfs-tools/modules
add the following

vga16fb
fbcon
vesafb

sudo gedit /etc/modprobe.d/blacklist-framebuffer
comment out the following (add prefix #) so it would look like:

# blacklist vesafb
# blacklist vga16fb

last but not least, run the following in a terminal

sudo update-initramfs -u

* Second *
sudo gedit /etc/default/acpi-support
change 
MODULES_WHITELIST="" to MODULES_WHITELIST="vga16fb vesafb"
ENABLE_LAPTOP_MODE=false to ENABLE_LAPTOP_MODE=true

Nothing else, it's work for me FS A1630 with ATI Mobile 9700

---

### Post by osiris2258 on 2007-11-03
I am also having this issue.

Trying to suspend turns the screen off for a few seconds and then it pops right back up to the password prompt, as if everything had worked fine.

Trying to hibernate causes a lockup, and the computer has to be hard-rebooted (usually also cause drive issues, need to run fix afterward). 

Neither of these worked in Feisty, I was hoping the fresh install of Gusty would fix the problem, but no such luck.

Custom system:
32 bit Gusty, dualbooting with Windows XP
AMD Athalon 64 X2 Dual 2.41 GHz
2GB Ram
NVidia GeForce 7600 GT
EPoX EP-MF570SLI motherboard (BIOS up-to-date)

---

### Post by adam0509 on 2007-11-04
in fact, I didn't undertood the difference between

 Lock Screen, blank screen and Hibernate.


Now everything works, cool...


..execpt the PC can't hibernate when lockscreen/blank screen is active...

---

### Post by climatewarrior on 2007-11-04
Dell latitude X300

fresh intall and upgrade

worked on feisty, works in gutsy with compiz fusion diabled

---

### Post by carac on 2007-11-04
> **climatewarrior said:**
> Dell latitude X300

fresh intall and upgrade

worked on feisty, works in gutsy with compiz fusion diabled


I am surprised - what wireless do you have ? (Dell Truemobile 1400 certainly does not work with bcm43xx !!! I am using ndiswrapper and with that it works ... with one problem ...).

Can you suspend and then resume by closing the lid and opening it again ?

In my case CompizFusion works perfect and suspend/resume works perfect from software or suspend hotkey, but NOT from the lid, which will always hang the computer :(

---

### Post by climatewarrior on 2007-11-07
I use the fwcutter driver (bcm43xx). I used to use ndiswrapper but bc43xx has gotten good enough for me. It used to be really bad. Closing the lid ALWAYS gets my system unresponsive( nothin will bring it back I have to turn it off). This didint happen in Feisty. I have heard that switching to the i810 video dirver fixes this but graphics wont look as good. I tired that but it didint work for me.

I really hope they fix all of this for Hardy Heron. I really dont mind this kinds of issues but some people panic and go back to windows. Nontheless ubuntu is getting better and better really quickly.

---

### Post by bwood720 on 2007-11-08
Computer: Inspiron 1300

Suspend works just fine (even though occasionally I get a message saying it had trouble suspending). 

Hibernation doesn't work at all. It acts like it's going to hibernate; it even shows a screen of "dos-like" code and then after a few screen flickers the login screen appears. When I log back in, typically there's a message in the top right of the screen saying that ubuntu didn't properly hibernate or something and to check the help files.


Also, I have had wireless network problems and have tried to add the file as mentioned several pages earlier (in the resume.d directory, creating the 99-...sh. file). However, for some reason it tells me that I am not the owner of the directory and therefore can't make any changes or add anything.

Thanks.

---

### Post by Dr. Feltersnatch on 2007-11-08
Inspiron 8200
Upgrade from 7.04

System will attempt to load up after Suspend or Hibernate and then will lock up. Powering off is the only way to restart.

```
product: Inspiron 8200
product: Intel(R) Pentium(R) 4 Mobile CPU 1.80GHz
product: 82845 845 [Brookdale] Chipset Host Bridge
product: 82845 845 [Brookdale] Chipset AGP Bridge
product: NV17 [GeForce4 440 Go]
product: 82801CA/CAM USB Controller #1
product: 82801CA/CAM USB Controller #3
product: 82801 Mobile PCI Bridge
product: 3c905C-TX/TX-M [Tornado]
product: PCI4451 PC card Cardbus Controller
product: PCI4451 PC card Cardbus Controller
product: PCI4451 IEEE-1394 Controller
product: PRO/Wireless 2915ABG Network Connection
product: 82801CAM ISA Bridge (LPC)
product: 82801CAM IDE U100 Controller
product: HTS726060M9AT00
product: CD-W216E
product: 82801CA/CAM AC'97 Audio Controller
product: 82801CA/CAM AC'97 Modem Controller
product: CGR-B/858
```


***UPDATE***
Did a fresh install of 7.10 and hibernate works (did not try suspend). Hibernate fails to work when restricted nvidia driver enabled. With the restricted nvidia driver enabled and I go to hibernate I cannot resume from hibernate.

---

### Post by Qwacko on 2007-11-09
Dell 6400 (e1505 equivalent i think)
Clean install (including latest updates)
suspend works, i have done the 99-network-manager thing so hopefully that will fix that small problem. Another problem is that when i resume sometimes the keyboard and mouse on the laptop dont work, if i plug in a usb mouse it works but keyboard still doesn't. So i am stuck at login screen, and put it into standby again (using keyboard, seems to work for this oddly) and when i bring it back again it normally works properly.

Havent tested hibernate, suspend is much more useful to me.

James

---

### Post by Nxion on 2007-11-09
Dell XPS m1210
Clean install
 
Suspend and hibernate do not work at all no matter what I do. Also I have noticed NetworkManager issues. Lost connect eventhought I am right next to the router as well as speed issues.

---

### Post by black_magician on 2007-11-09
clean install on a Inspiron 6000.  I've never been able to get hibernate to work.  suspend to RAM works sometimes, rarely though.

---

### Post by repawn on 2007-11-09
Dell Inspiron 1420 - Clean install of Ubuntu 7.10 - Nvidia 8400 GS - WXGA+ (1440x900) screen - Suspend works well - though I have intermittent problems with wireless returning - when using hard wired network everything works perfectly. Hibernate also works - though there doesn't seem to be much advantage because it takes nearly as long to come up as it does from being turned off. I am impressed with how well it has done with suspend though - the little light in front even pulses when it is in suspend mode. To be fair - the wireless works really well - but if I turn it off and then later try to turn it on I have some difficulty connecting - this problem seems to be similar to the problem with wireless connecting after coming out of suspend. side note - the webcam works flawlessly and I am happy I chose to purchase the Vista version with the better video card, bluetooth and the webcam - I never booted into Vista - stuck the install disk in and went for full install of Ubuntu.

---

### Post by GSBoomer on 2007-11-10
I have a fresh install of Gutsy on an e1505 with the 945GM graphics chip. After installation I did run the update manager.

Suspend works and it wakes with a press of the power key. Wireless network does not bounce back. Going into the Network Settings, clicking properties for the wireless network, and switching the password type to a different setting then back causes the network to reconfigure, which brings back the wireless.

BTW, xserver-xorg-video-intel was installed by default. I've made no other changes to the setup. I did activate xscreensaver and I was asked for my password on waking. Also, the screen was blank after waking but touching the touchpad brightened the screen.

Hope this helps someone.

UPDATE: Using the information at [http://ubuntuforums.org/showthread.php?t=461294](http://ubuntuforums.org/showthread.php?t=461294) and following harty83's instructions for 99-fixwifi.sh, suspend now works flawlessly!

UPDATE 2: Hibernate also works flawlessly. The screen comes back and the network is up.

---

### Post by keyboardphd on 2007-11-10
> **dahen said:**
> Dell Inspiron 6000
ATI Mobility X300 (M300)
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON X300
OpenGL version string: 2.0.6473 (8.37.6)

Gutsy through stepwise upgrading from Feisty.
Stanby/HIbernate was working in Feisty.
In Gutsy the screen gets black when going to Standby (Suspend to RAM) but computer doesn't go to sleep. It gets stuck on the black screen and there is no way of getting it to unlock. I have to hold down the powerbutton to turn the computer off and then start it normally again.

DELL INSPIRN 710M

i have the same problem. Is this tread only for complain about the issue or some one has find a effective way to fix it?! i really  need to fix it... i don't want to go back to windows... PLEAAAASE! SOME ONE!!

---

### Post by divdude on 2007-11-11
It WORKS for once!!!!
Ok this is what I did.
1. commented
# Should we attempt to warm-boot the video hardware on resume?
#POST_VIDEO=true
from /etc/default/acpi-support

2. Suspended, it worked.
3. To resume pressed power button and alt+ctrl+F1 ( I dont know if
this is required but works for me), shows a password dialog and i am back in.

Nvidia 6200
AMD 3200

---

### Post by MarilenCorciovei on 2007-11-11
Thanks a lot for all the info on this thread. Finally [suspend works for m]("http://www.len.ro/work/tools/ubuntu-gutsy-on-a-dell-latitude-d820/install-gutsy/view")e on a Dell D820 with Gutsy.

---

### Post by frankmulder on 2007-11-12
I managed to fix hibernate on my Kubuntu desktop with Nvidia graphics by applying the following fixes:
[LIST]
[*]Add Option "NvAGP" "1" to the Device section of xorg.conf
[*]Append "blacklist via_agp" and "blacklist agpgart" to /etc/modprobe.d/blacklist
[*]Set "SAVE_VBE_STATE=false", "SAVE_VBE_STATE=false", "POST_VIDEO=false" and "HIBERNATE_MODE=platform" in /etc/default/acpi-support
[*]Fix swap partition by using the procedure at [http://ubuntuforums.org/showthread.php?p=1683612](http://ubuntuforums.org/showthread.php?p=1683612).
[/LIST]

I'm not sure if all of these were needed; at least Hibernate works now (I haven't tried Suspend, as there is no Suspend option in my KDE logout dialog).

---

### Post by xurizaemon on 2007-11-12
Dell Dimension 4800. Gutsy. Two issues:

1) As per above, comes back from Hibernate with blank screen.

2) Despite installing grub to /dev/hda, the Dell BIOS insists on booting to WinXP @ /dev/hdb UNLESS I hit F12 and choose "Utility Partition". (OT, but I'd LOVE a fix for this.)

---

### Post by cangrejojeringa on 2007-11-12
wherer can i get drivers for a ATI Technologies Inc Rage 128 Pro Ultra TF?

g

---

### Post by Tristam Green on 2007-11-13
Dell 1501, GNOME Desktop, x86 version.  Compiz-enabled, video adapter listed in signature.

*edit*Gutsy 7.10, clean install.*edit*

Dual-boots with Vista Basic just fine.

Upon Hibernate or Suspend, screen locks entirely, and cannot recover unless I poweroff/poweron.

I do not have screensavers running, and all power settings are set to "do nothing".  After about 15 minutes of idle, however, screen blanks.  If I don't move the touchpad in about...3 or 5 minutes, screen is non-recoverable.

Any ideas?  I'd really love to be able to hibernate/suspend.

---

### Post by Dan_N on 2007-11-14
My samba mount points does not work after resume from standby. 

I mount several samba shares to my nas (D-Link DNS-323) by using entries i fstab. Example entry is:
//192.168.1.32/MEDIA /mnt/Media smbfs credentials=/root/dansmbcredentials,lfs,iocharset=utf8,codepage=cp850,uid=dan,gid=users,fmask=550,dmask=550 0 0

Regards, Dan

---

### Post by staticsage on 2007-11-14
I fixed Suspend and Hibernate on my Dell Precision M60 by making the following changes:

Changing "POST_VIDEO=false" in /etc/default/acpi-support and adding Option "NvAGP" "1" to my xorg.conf in the devices section.

Now here is the weird part. I didn't have to blacklist any modules to have this work. In my log files it explicitly says that the Nvidia driver won't use NvAGP because agp modules are loaded. However, if I remove the NvAGP option from my xorg, suspend and hibernate no longer work.

I thought that was very strange...

(I came across this because I misspelled agpgart when I tried to blacklist it. Suspend and Hibernate still worked without having it blacklisted so I removed all my blacklist rules that I had listed for Suspend and Hibernate to work. It still worked after removing the modules from the blacklist so I narrowed it down to the two settings: NvAGP and POST_VIDEO=false.)

---

### Post by loso on 2007-11-14
Dell inspiron 1501
gutsy upgraded from fiesty
Hibernate and Sleep don't work

---

### Post by slanbarn on 2007-11-14
Hello there everyone!

I dont have a Dell laptop.

My laptop is a Advent 7105(made by ECS)
OS: ubuntu 7.10
wireless: marvell libertas (ndiswrapper)
graphics: ati radeon Xpress 200M, restricted driver.

my suspend/hibernate doesnt work...

When I use the software("shutdown menu") and choose hibernate, then X shuts down, and I get a black screen, with a blinking cursor in the top right corner... ctrl+alt+fX works, and there are startup messages left on tty1(I dont use splash at boot, it doesnt show anyway :p)

what could be wrong.. I have tried some of the tips in this thread, like trying some different settings in /etc/default/acpi-default...

one strange this thou is that /proc/acpi/button/lid/state says CLOSED when the lid is open... so i guess something with the acpi-system isnt working right....

---

### Post by Student Driver on 2007-11-15
I am still going through this thread, but I have suspend to RAM and suspend to disk working OK on my Dell Latitude D610.  It didn't work with the proprietary driver, but then again neither did Compiz.  I used the open driver and got more graphic functionality and suspend to RAM, but the graphics would be corrupted upon resume and suspend to disk still didn't work.

I eventually traced a lot of the issues down to using 3D accelerated features.  It seems that suspend and hibernate works fine with the open driver if I don't have any kind of 3D screensaver in use.  I am going to work this a bit more, but so far so good.  At first, it wouldn't even try to resume from hibernate status.  Once I went to the open driver it got further, but just got a cursor flashing.  At this point, it's working fine.  I will give it a few weeks and then start using fancy screensavers (I only use the blackout right now) and see what works and what breaks.

---

### Post by geeree on 2007-11-15
I have an Inspiron 640m and I upgraded to Gutsy soon after it was released. Both suspend and hibernate are working fine here,

Girish.

---

### Post by slanbarn on 2007-11-15
Okey, where can I find the open driver for my ATI card: here is what lspci says about it:
01:05.0 VGA compatible controller: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]

This is with the restricted driver loaded(if that may alter what lspci says, i dont know...)

---

### Post by slanbarn on 2007-11-15
Okey, nevermind!

I used the "radeon" xorg driver(uninstalled the restricted), and hibernation works fine :)

thanks everyone who contributed to this thread!

it spits out some errors regarding usb, but it shuts off, and starts from image just fine, and network working after resume from hibernation image :)

---

### Post by slanbarn on 2007-11-15
Hello there again! :)

Have a peculiar problem, relating to hibernation. My /proc/acpi/button/lid/LID0 says "State: closed" when the lid is open, so if I set that "when on battery - if lid is closed, hibernate", this results in that the computer goes into hibernation if I yank the AC-cord :)

this is not a big problem, hibernation can be activated via the menu, but is kinda peculiar.

Anyone has any idea, why the state of the lid isnt working?

---

### Post by jimmy the saint on 2007-11-15
Check out my very newbie friendly guide to enabling suspend.  Hibernate still doesn't work.  It works for my thinkpad t61, hopefully it will for Dell as well.  

[http://ubuntuforums.org/showthread.php?t=614106]("http://ubuntuforums.org/showthread.php?t=614106")

---

### Post by fuzzy_umbra on 2007-11-16
I'll throw my config. into the mix:
Machine: Dell 8100
Video Card: Radeon 9600 XT

---

### Post by Surgeon General on 2007-11-16
Dell 1520

laptop fan just spins continuously. laptop don't resume.

---

### Post by alvenegas on 2007-11-17
I have a Dell Inspirion 8100 with nVidia GeForce 2 Go and after a fresh 7.10 install Suspend nor Hibernate worked.  I went to some notes
I found when I dealt with this problem when I installed Dapper on the same machine some years ago.  As soon as I did the fix on the machine it went back to work. Here is what I did:

On /etc/X11/xorg.conf file go to the "Device" Section and add an 
"Option" of "NvAGP"   "1"

On file /etc/default/acpi-support change to "false" the entry
POST VIDEO=true

Doing only these two things made Suspend work.  Hope someone
finds it useful.

---

### Post by staticsage on 2007-11-17
> **alvenegas said:**
> I have a Dell Inspirion 8100 with nVidia GeForce 2 Go and after a fresh 7.10 install Suspend nor Hibernate worked.  I went to some notes
I found when I dealt with this problem when I installed Dapper on the same machine some years ago.  As soon as I did the fix on the machine it went back to work. Here is what I did:

On /etc/X11/xorg.conf file go to the "Device" Section and add an 
"Option" of "NvAGP"   "1"

On file /etc/default/acpi-support change to "false" the entry
POST VIDEO=true

Doing only these two things made Suspend work.  Hope someone
finds it useful.

Did you have to blacklist any modules? If not, do you see any errors in your messages or kern logs: "NVRM: not using NVAGP, an AGPGART backend is loaded!"?

I had to do the same two things, but the error basically says that the NvAGP option isn't doing anything. I thought it was just me, but it seems like this may also be your situation.

---

### Post by 61811 on 2007-11-18
Two out of three desktops upgraded (not a fresh install) from Feisty to Gutsy - both cannot Resume from Suspend. Upgrade was clean without errors.

System #1
Dell Dimension 4700
Pentium 4 2.8GHz
82915G Integrated Graphics Controller
- Suspends fine.
- Resumes - however, after entering the password, screen goes blank with lots of USB messages, and then computer powers off. Have to restart (cold boot).
- If Power Management is disabled, then Resume works fine after manually Suspending the machine.
- Feisty worked flawless for auto Suspend/Resume.

System #2
ECS Mobo AMD690GM-M2
AMD Athalon 64 X2 4600+
AMD 690G Northbridge (no add-on video card)
SB600 Southbridge
- Suspends fine
- Cannot Resume at all. Have to power cycle (cold boot).
- Cannot Resume from manual Suspend either.
- Feisty worked flawlessly - system would Resume after manual or auto Suspend.

Questions:
- Has a fix been found for the Power Management bug in Gutsy? If so, please point me to it.
- If not, how do I revert back to Feisty?

Thank you.

---

### Post by terklotron on 2007-11-18
Dell Inspiron 6000
Did a clean install with Ubuntu 7.10 a few weeks ago.
Both suspend and hibernation worked smoothly untill a few days ago.
Might have been around the time I got Compiz fusions 3d thing to work with my ati mobility readon x300 card, using xgl.

Hope we get a fix soon. Pretty anoying, but I still love Ubuntu:guitar:

Peace

---

### Post by Paul S on 2007-11-18
> **AaronMT said:**
> Hello,

I think it would be a wise idea to create an *official* thread containing all  the collective data received concerning this issue with Ubuntu 7.10 (Gutsy) rather than have an array of topics and threads posted many times pertaining to duplicate data.

I suppose one collective thread would be better.


I think this thread has grown too large and is now too difficult to find useful information.  It's apparent that the type of video card is critical to whether suspend / hibernate work on gutsy.  Also, with all the non-dell posters, they add unuseful reading.  Next time, I think it would be better to have a separate thread for each laptop and video card combination.  It sure would save time for those of us searching for tips.

regards,

---

### Post by lowlymarine on 2007-11-20
Dell Inspiron 9300:
-Pentium M Dothan
-915PM Chipset
-Intel PRO/Wireless 2200BG
-256MB nVidia GeForce Go6800

Suspend to RAM does not work with Gutsy, though it worked fine with Edgy (the last time I used Ubuntu on this machine).  It suspends successfully, and tries to resume - I can briefly see the terminal resume - but it eventually ends up stuck at a black screen and nothing works, even Ctrl+Alt+F1 and Ctrl+Alt+Backspace.  I haven't tried hibernate yet.  This is all with Compiz enabled; I'll try again with it disabled and see how that goes.

Update: Disabling Compiz didn't help, as I'd suspected.

Update 2: Hibernate, much to my great surprise, works without a hitch (a first ever in my experiences with Linux).  Not that it goes any faster than actually shutting down and restarting the computer, however, and there's no visual feedback on progress.

---

### Post by yfarjoun on 2007-11-20
Dell Inspiron 8100 Nvidia GeForce2 Go  with  a 1600X1200 LCD.

Upgraded from 7.04 and suspend (to RAM) stopped working. Hibernate never worked, and I don't care much for it either.

Suspend would fail in two different ways depending on the setup. Either it would not resume properly and a hard reset was needed, or it would resume  and give me a screensaver that I could not get out of (moving the mouse would show a cursor, but I never got my desktop back). In this case, I could switch to a terminal and kill the screen-saver, and this would give me my desktop back.
(Or I could use the three-finger salute and kill X, which also worked)

Yesterday I was playing around trying to get suspend to work again. FInally I managed.
I don't know if a subset of the actions I did will also work...perhaps somebody will care to try.

1. I removed APM, (probably not needed)
2. I  installed nv and removed nvidia for the graphics driver, and
3. I killed gnome-screensaver as I logged in.

now I'm happy...I don't need a screensaver anyhow.....

I tried to uninstall gnome-screensaver, but that didn't work properly for some reason.....

I hope this will help pinpoint the problem.....

Cheers.

---

### Post by lowlymarine on 2007-11-20
The issue lies in the proprietary drivers.  By switching to the open source nv driver, it allowed suspend to work properly.  However, you probably lost a lot of 3D horsepower, and does Compiz still work?

I might try nvidia-glx instead of nvidia-glx-new, unless someone else can comment on that.

---

### Post by theproc64 on 2007-11-20
I have a Dell latitude D620.  suspend works most of the time but sometimes when it comes out of suspend the computers frozen, keyboard, and mouse don't work and I can't even turn the num lock on and off.

---

### Post by DarqueWing on 2007-11-21
I've tried upgrading to Gutsy, and I've tried fresh installs.  I've tried every applicable fix suggested in this thread and elsewhere - some producing even more awful problems.  I've devoted too much time to doing fresh installs, doing a fix that makes it look like it will work for a while, getting all my stuff reinstalled, and then having it start doing the same thing over again.

This little standby problem is officially a fatal flaw in Gutsy for me.  I just lost half of an important meeting because I was trying to get my laptop to turn on instead of taking notes like everyone else.  After a hard boot, it chose the worst possible time to require a disk scan.  The guy using the Apple next to me had some choice words for how poor Ubuntu is.  Hard to argue with him when I can't even get the thing out of standby without major problems.  (It's sad when the guy on the Apple actually suggests that Windows would be an improvement.)

So I'll see you back at Feisty Fawn.  While a lot of Gutsy's features are cool, and it would probably be a non-issue on a desktop computer, standby mode is necessary for a laptop that's used for work.  It's a deal-breaker, and embarrassing considering how I've been telling everyone since I discovered Feisty how stable and superior Ubuntu is.

Hopefully this will be sorted out by the next release.  I like Ubuntu too much to bear watching it cause this many problems.

---

### Post by Dellfan on 2007-11-21
A summary of tweaks to improve suspend/hibernate/resume on Gutsy - this works flawlessly on a 1505, with Nvidia graphics, Intel 3945 wireless, a current kernel (2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux) running Gnome, for both suspend and hibernate

In /etc/acpi/suspend.d

create 20-i8042-input.sh:
#!/bin/sh
# Added to deal with keyboard freeze/lockup after suspend
# Unbind the AT keyboard interface.
if [ -f /sys/bus/platform/drivers/i8042/unbind ]; then
  echo -n "i8042" > /sys/bus/platform/drivers/i8042/unbind
fi

in /etc/acpi/resume.d

create 40-i8042-input.sh:
#!/bin/sh
# Added to deal with keyboard lockup/freeze after resume
# Rebind the AT keyboard interface.
if [ -f /sys/bus/platform/drivers/i8042/bind ]; then
  echo -n "i8042" > /sys/bus/platform/drivers/i8042/bind
fi

create 99-network-manager.sh:
#!/bin/sh
# Added to deal with NetworkManager getting confused on resume
/etc/dbus-1/event.d/25NetworkManager restart

if having issues with sound on resume create 99-restore-volume.sh:
#!/bin/sh
amixer sget Master | grep "Mono:" | while read m p v j
do
        amixer sset Master 0
        amixer sset Master $v
done

in /etc/default/acpi-support ensure that:
POST_VIDEO=false

in /etc/X11/xorg.conf, in the Section "Device" add the option:
Option          "NvAGP"

Note: All files in suspend/resume directories, need to be owned by root and executable (ie sudo su, chown root filename, chgrp root filename,chmod 755 filename)

With this, I do not have to blacklist any modules.

---

### Post by luco.vico on 2007-11-22
I have a DELL Inspiron 1501. Upgraded from 7.04. Hibernate/Susepnd/Black Screen all go into some trance and never come back.

There are a few other issues that occured after the upgrade, but those are probably not applicable to this issue.

Hope we can find a solutions!

Victor

---

### Post by Aure on 2007-11-22
Dell m1210
Clean install

doesn't sleep when closing lid, unresponsive after resuming from suspend when I click on suspend.

---

### Post by cheechdurden on 2007-11-22
Dell D800
Clean install

Will suspend from shutdown/suspend/logout menu, but is unresponsive when powered back on.

---

### Post by shbae on 2007-11-22
Dell Latitide D520
RAM 2G
Intel Core2 Duo 2.0
Dual boot with windows XP,
Clear Install of 7.10
Actually, Kubuntu
Problem with Suspand/Hibernate

---

### Post by hal69000 on 2007-11-22
Dell Inspiron 5150
512MB RAM
Pentium 4
Clean Install

Can't suspend, hibernate, closing the lid does nothing. It also freezes up completely on occasion, requiring a restart.

---

### Post by tombeharrell on 2007-11-23
Dell Inspiron XPS Gen 2, 2GB RAM, 100GB, Nvidia 6800 256MB

Upgraded from 7.04 through development versions of 7.10. A few kernels ago standby and hibernate both worked, but the last couple of updates (last month or so of betas) broke standby.

Hibernate works fine though, with or without Compiz running.

---

### Post by richardh on 2007-11-24
Dell Lattitude D810.
Hibernate worked with Eft.
I first upgraded to Feisty at an RC stage, and hibernate worked. Then at some point (viz., during one of the updates) it broke (dont have the details any more). 
Got hibernate/suspend working with uswsusp on Feisty.
Hibernate is broken again on upgrade to Gutsy. Got it working once, but then an update broke it again. Havent been able to get suspend or hibernate working again any which way, even with uswsusp. Given up for the time being.

After the massive PR surrounding Dell and Ubuntu, I am amazed that what is truly an important feature for a laptop (hibernate/suspend) user should NOT work out of the box on an upgrade that occured after the hype.

Question: does hibernate / suspend work on Dell laptops preloaded with Ubuntu?

If so, how have the Dell engineers got it working?

---

### Post by julep on 2007-11-24
Dell Inspiron 1100 with a remanufactured motherboard. It calls itself an Inpiron 5100 and tells me it has an ATI Radeon 7500...I have no idea where the motherboard came from, but it was free. 

It's running Gusty upgraded from Feisty.

It suspends and resumes OK but I loose the wireless (and probably dhcp). It also doesn't turn off the screen when the lid closes. It behaved the same on Feisty, so there's really no change here.

---

### Post by serhito on 2007-11-25
Inspiron 710m with 7.10 version, clean install.

No Hibernate, No Suspend working.
Sometimes, it will also give me a black screen and freeze while shutting down.

---

### Post by Dellfan on 2007-11-26
> **richardh said:**
> Dell Lattitude D810.
Question: does hibernate / suspend work on Dell laptops preloaded with Ubuntu?

If so, how have the Dell engineers got it working?

It seems to on the 1505. Also worked after I upgraded to Gutsy. Tweaks I have made were to deal with NetworkManager sometimes getting confused after a resume and ending up in a weird state, and the keyboard sometimes locking up, which started happening after I added the fix to restart NetworkManager. Rock solid suspend/hibernate and resume out of the box.

The Ubuntu release seems slightly more stable than the Kubuntu version. I suspect this has more to do with Canonical being primarily a Gnome shop than anything else. For example the media and Fn keys worked out of the box on Ubuntu. Some folks are reporting issues under KDE.

---

### Post by dolphin_oracle on 2007-11-26
So you know, suspend/hibernate is also broken on my old Sony Vaio PCG-FXA32 running Gutsy.  Worked under Feisty and Edgy.  mine locks up whenever you choose either option.

---

### Post by Tristam Green on 2007-11-26
> **Dellfan said:**
> 
The Ubuntu release seems slightly more stable than the Kubuntu version. I suspect this has more to do with Canonical being primarily a Gnome shop than anything else. For example the media and Fn keys worked out of the box on Ubuntu. Some folks are reporting issues under KDE.

The only function keys that work out of box on mine are the volume control.  Brightness and others do not.  Any fixes for this aspect, since it's not power management features?

---

### Post by dregin on 2007-11-27
> **prismatic7 said:**
> Dell XPS m1210, Nvidia GFGo7400 - suspend worked just fine in Feisty but fails in Gutsy. The laptop does not suspend or hibernate at all - display fades and blanks correctly, but fans and hdd are still running, and the power light remains steady (rather than flashing)

On opening the lid, nothing happens. The only way out is to hit and hold the power button until the laptop powers off.

I've tried the uswsup tip [here](http://ubuntuforums.org/showthread.php?t=471855&highlight=nvidia+suspend),  the acpi tweaks [here](https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend) and the fix marked for the Latitude D820 [here](http://koon.fr/wiki/suspend_to_ram_on_the_dell_d820_proprietary_nvidia_drivers_under_ubuntu_gutsy) with no success.

This is a clean install of Gutsy with no other customizations than the Nvidia binary driver (although suspend/hibernate fail with the nv driver as well).

Was having this problem with the exact same setup.

sudo nano /etc/default/acpi-support

Change POST_VIDEO=true to POST_VIDEO=false.
That sorted it for me. Got it from this thread:
[http://ubuntuforums.org/archive/index.php/t-350265.html](http://ubuntuforums.org/archive/index.php/t-350265.html)

---

### Post by mauron on 2007-11-27
Acer Aspire 1360
Clean install

Suspend and hibernate don't work, didn't work in previous versions either.

---

### Post by prismatic7 on 2007-11-27
> **dregin said:**
> Was having this problem with the exact same setup.

sudo nano /etc/default/acpi-support

Change POST_VIDEO=true to POST_VIDEO=false.
That sorted it for me. Got it from this thread:
[http://ubuntuforums.org/archive/index.php/t-350265.html](http://ubuntuforums.org/archive/index.php/t-350265.html)

Tried it, didn't work...

---

### Post by prismatic7 on 2007-11-27
> **prismatic7 said:**
> Tried it, didn't work...

Sorry... I should expand on that - my problem is not that the machine does not *wake* from sleep, but that it doesn't *go* to sleep in the first place. I can't see where to increase logging options so that I can see what's holding it up.

---

### Post by Ron F. on 2007-11-28
Dell Latitude D500 laptop (Pentium M - 1300 MHz,) 512M RAM, 855GM Intel Integrated graphics.

Ubuntu Gutsy - fresh install.

Hibernate causes an immediate crash and a frozen display - no recovery possible other than a power cycle.

Suspend goes to a black screen - no recovery other than a power cycle.

Shutdown does not work either - no recovery other than a power cycle.

In effect - I cannot shutdown my laptop at all - I can only crash it. 

I have tried a lot of things mentioned in many online discussions about the shutdown failure - nothing has helped.

-Ron

---

### Post by trippinnik on 2007-11-29
I finally got sleep working using Linux Mint (it's faster going in and out now too) but the sound doesn't work when I resume. It's not the volume as I checked alsamixer and all the other sound panels.  This used to happen back in fedora 6 or 5.  Is there some command to redetect the soundcard on resume? Anyone have some other ideas?

---

### Post by serhito on 2007-11-29
i have a dell 710m and the only way that standby/hibernate will work, is by applying the lowest setting for the effects. In other words "NO EFFECTS".
Does anybody knows if it would be possible to enable them at startup, and disable them before shut down. All that automatically with a script.

---

### Post by road2elysium on 2007-11-29
> **serhito said:**
> Inspiron 710m with 7.10 version, clean install.

No Hibernate, No Suspend working.
Sometimes, it will also give me a black screen and freeze while shutting down.

Same here on an i700m.

---

### Post by Makoshark on 2007-11-30
Hi have the same Suspend/Hibernation problems of the other Acer owners...My laptop is  Acer aspire 1694...I hope Ubuntu Community will fix all this bugs....thank you very much for your work!

---

### Post by jlavezzo on 2007-11-30
Dell Precision M90 (all 4 kg of it)
4gb ram
NVIDIA Quadro FX 3500 512MB
(no this is not [Michael Dell]("http://www.dell.com/content/topics/global.aspx/corp/biographies/en/msd_computers?c=us&l=en&s=corp"))
Intel Pro/Wireless 3945 Network Driver
NVIDIA accelerated graphics driver

I did a clean install of 7.10 on Tuesday. Yesterday I tested Suspend AND Hibernate. Both worked perfectly, even when shutting the laptop lid. TODAY neither works. Basically when I click Suspend or Hibernate, Ubuntu acts as if I hit the "lock screen" button, though I occasionally get a "Sleep Problem" error message in my system tray. The only system changes I made today was that I installed Virtual Box. Uninstalling it did not correct the problem.

The fact that this WORKED then stopped indicates to me that it's a very fixable bug. I hope I hear about it when it is fixed.  In the mean time, I'd rather have Compiz than hibernate, so I'm not going to disable the restricted driver.

As an aside, has anyone else experienced a 'screen flicker' where the screen blinks black for a moment?  I'll search the forums for it separately as well.

---

### Post by ictiosapiens on 2007-12-01
Dell latitude D800
Pentium m 1.6
1.5 GB ram
Nvidia geforce 4200 64mb

Ubuntu 7.10 clean install
No shutdown problems, but unable to resume from hibernate or stand by.
The machine does actually go into the chosen state, but when resuming I just get a black screen.

---

### Post by zasq on 2007-12-01
Hi,
Inspiron 1501
updated from feisty to gutsy
suspend and hibernate do not work (not closing the lid, not using the fn-Esc or fn-F1 nor over the menu. It won't with or without compiz-fusion installed
ATI-driver Radeon XPress, open gl version string: 2.0.6473 (8.37.6)
Has anyone tried the new propietary ATI-Driver with installer released yesterday?
Hope the problem will be solved as well as the not functioning fn-keys!
All the best

---

### Post by bomanizer on 2007-12-02
What's the biggest difference regarding suspend/hibernate between kernels/kernel configurations. I mean, where to look FIRST if suspend/hibernate works on one kernel and not on the other?

-Cheers

---

### Post by chanas on 2007-12-02
ACER 1640 with Intel graphics card. Laptop suspends but never wakes up. Only power down saves the day.In 7.04 all was fine.

---

### Post by dimbulb1024 on 2007-12-02
Dell Inspiron 6000
Pentium M 1.7
2 GB RAM
Integrated Intel Media Accelerator 900 Graphics (mobile 915)
Broadcom Corporation BCM4401-B0 100Base-TX

Never used Hibernate
Suspend works 75% of the time. The other 25% when I resume from Suspend NetworkManager hits 100% CPU and I can no longer connect. At this point I have to reboot.

Update: I've tried Hibernate but I set my Swap, I didn't realize Hibernate used it, so who knows it if works or not. :)

---

### Post by macbuff on 2007-12-02
DELL Latitude D610
Ubuntu 7.10

Suspend/Resume works OK

Hibernate seems to work, but when I try and bring the system back it just does a normal system boot - except that the swap partition fails to mount after which I have to do a mkswap and edit /etc/fstab with the new swap UUID.

Also this may be unrelated, but the system will not do a shutdown/hibernate/sleep when the battery level becomes critical - this worked fine under 7.04.

John

---

### Post by OlyPerson on 2007-12-02
I have a Dell Dimension 2400 with a clean install, not sure about my graphics card and stuff.

So is there a solution to this problem?  It's really pretty annoying because I like to use suspend often.

---

### Post by antid0te on 2007-12-04
i did post this 2 weeks ago here :```
http://ubuntuforums.org/showthread.php?t=591229
```

Still no update from Ubuntu :(

I migrate to Mint 4.0 yesterday which based on Gutsy too, and when i tried to shutdown, restart, hibernate, and standby it's not working at all.

Still..no further action :(

---

### Post by exquest on 2007-12-04
HI.  I can't hybernate or suspend my laptop without it hanging and causing my to do a complete reboot of the system.  I have a Dell Inspiron 5150 and did a clean install of ubuntu 7.10 and LOVE IT besides the pesky little not suspend or hybernate thing.  I would love a fix for this.

---

### Post by ckilger12 on 2007-12-05
Dell Inspiron 6000 I believe i have an ATi card....but Suspend/Hibernate will not come back awake...reboot needed.....I am ubuntu noob

---

### Post by TrinitronX on 2007-12-05
Dell XPS M1710 
nVidia GeForce Go 7900 GS - Using Gutsy's restricted drivers
Ubuntu 7.10 [Clean Install]
**With clean install I get:**
Black screen on resume from standby 

**With following modifications I get:**
1st Suspend/Resume cycle [color=green]successful[/color], 2nd Resume [color=red]fails[/color] with black screen.
 
Added into /etc/X11/xorg.conf in "Device" section: 
```
Option          "NvAGP"         "1"
```And in /etc/default/acpi-support :
```
SAVE_VBE_STATE=false
POST_VIDEO=false

```After these changes the laptop will resume ONLY ONCE from standby.  Any subsequent attempts to resume from standby again still result in a blank screen

Looked into /var/log/messages and found where it failed, the last kernel messages were:
```
Dec  4 03:24:27 sirius gnome-power-manager: (trinitronx) Suspending computer because the lid has been closed on battery power
Dec  4 03:24:28 sirius dhcdbd: Unrequested down ?:3
Dec  4 03:24:28 sirius kernel: [  170.636000] ACPI: PCI interrupt for device 0000:09:00.0 disabled
Dec  4 03:24:28 sirius kernel: [  170.824000] ACPI: PCI interrupt for device 0000:0c:00.0 disabled

```Attached is a messages.log file with 2 suspend/resume cycles.  I've marked places in the file with lines starting "####### NOTE:"  .
This is repeatable upon reboot, first suspend/resume cycle  is successful, second fails.

---

### Post by al_sharpe on 2007-12-05
Ubuntu 7.10
Acer Travelmate 290
Intel 955GM

Using Vesa drivers suspend and hibernate work perfectly.

Change to Intel (i810) driver and suspend and hibernate screw up video totally.
With firefox the mouse movement only moves the top 20% and bottom 20% 
of browser, middle of browser is frozen, strange result from suspend.
I can tell all is not well when coming out of suspend right away because the
network config icon on top of screen has a black background.
Time to reboot.

As long as I do not go to suspend or hibernate all is well.

Al Sharpe

---

### Post by YuriBCN on 2007-12-05
**Dell Inspiron 1501 AMD 2x64-bit**

After upgrading to 7.10 (64-bit) from 7.04 (64-bit), tried a clean install to sort hibernation problem, to no avail.

Real hastle as I have to boot up every time.

---

### Post by svguy on 2007-12-05
Dell d600 with gresh gutsy 7.10

Suspend=yes
hibernate=yes
shutdown=yes

The only problem i have is that if the laptop is asleep or in hibernation for longer than just a few minutes the network card isn't around when it comes back.
I checked /var/log/messages yesterday when it did it and came up with
> Dec  4 20:05:58 wabbit kernel: [ 4030.264000] ipw2200: Intel(R) PRO/Wireless 220
0/2915 Network Driver, 1.2.0kmprq
Dec  4 20:05:58 wabbit kernel: [ 4030.264000] ipw2200: Copyright(c) 2003-2006 In
tel Corporation
Dec  4 20:05:58 wabbit kernel: [ 4030.268000] ACPI: PCI Interrupt 0000:02:03.0[A
] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
Dec  4 20:05:58 wabbit kernel: [ 4030.268000] ipw2200: Detected Intel PRO/Wirele
ss 2200BG Network Connection
Dec  4 20:05:58 wabbit kernel: [ 4030.480000] ACPI: PCI interrupt for device 000
0:02:03.0 disabled
Dec  4 20:05:58 wabbit kernel: [ 4030.480000] ipw2200: probe of 0000:02:03.0 fai
led with error -5

I have the 99-fixwifi.sh script that seems to do its job unless the computer has been asleep for any long period of time, then running that script doesn't help.

I'm a linux noob and just can't figure this out.

*UPDATE*
i put the laptop to sleep when i went to lunch today. I came back 30 minutes later, opened it up to a black screen with two flashing lights next to the power button.  One if the caps lock light, the other one is a lock with a down arrow on it.  Had to hold the power button down to turn it off.

---

### Post by metalheart on 2007-12-05
Inspiron 6400 with ATI X1400. Everything works with radeonhd version 0.4 drivers.

---

### Post by peedeeramone on 2007-12-05
I've got a Sager NP5580-C.
Intel Centrino Duo
Integrated Intel Video (i forget exactly which one)
Intel Pro/Set Wireless (3945 i think) A/B/G
1GB ram
2 GB swap
Ubuntu Gusty 7.10 with most updated kernel

Gusty: Suspends down fine the first time, resumes allright with a few listed errors saying that it did not suspend properly, but otherwise is fine. the second time you try to suspend kills it. Sometimes it will halfway suspend, but never turns off, other times it kills x, shows some stuff about usb devices, and stays there untill you manually power off.
Hibernate: works sometimes, but not others. I dont use hibernate very often.


It has basically done this since I first installed Dapper.

I have no idea why it will only suspend once, and I don't really know how to resolve it.

---

### Post by edochan3 on 2007-12-05
Dell Inspiron E1405.  Clean Gutsy install.  Neither standby nor hibernate work.

---

### Post by tribbleva on 2007-12-05
Another Dell Latitude D610, latest BIOS, latest Gutsy, everything up-to-date. This machine has the ATI video set, the wireless, the bluetooth adapter, and 1GB RAM.

This was a clean wipe, format, and install of Gutsy from CD.

Neither suspend nor hibernate works. They fail in the "going into" part of the process; that is, the power light never dims/cycles, it just stays on solid. The screen does go black, but from that point nothing but a hard reset will bring it back. Entering hibernate does not flush much of anything to disk; HD light flickers briefly, but no substantial state saving occurs.

I've had this failure both with the open source driver and the proprietary ATI driver. The ATI driver performs much better, so I'd like to stick with it.

---

### Post by Orion2000za on 2007-12-06
When I had Inspiron 6400 w ATI card I got suspend/hibernate to work this way: 

Sinclair
----------------------------------------------------
getting suspend to work
root edit /etc/default/acpi-support

Code 
# Comment the next line to disable ACPI suspend to RAM
ACPI_SLEEP=true

# Comment the next line to disable suspend to disk
ACPI_HIBERNATE=true

# Change the following to "standby" to use ACPI S1 sleep, rather than S3.
# This will save less power, but may work on more machines
ACPI_SLEEP_MODE=mem

# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded 
# unless they're listed in MODULES_WHITELIST
MODULES=""

# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST="fglrx"

# Should we save and restore state using the VESA BIOS Extensions?
SAVE_VBE_STATE=false

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=false

# Save and restore video state?
# SAVE_VIDEO_PCI_STATE=true

# Should we switch the screen off with DPMS on suspend?
USE_DPMS=true

# Use Radeontool to switch the screen off? Seems to be needed on some machines
# RADEON_LIGHT=true

# Uncomment the next line to switch away from X and back again after resume.
# This is needed for some hardware, but should be unnecessary on most.
DOUBLE_CONSOLE_SWITCH=true

# Set the following to "platform" if you want to use ACPI to shut down
# your machine on hibernation
HIBERNATE_MODE=shutdown

# Comment this out to disable screen locking on resume
LOCK_SCREEN=true

# Uncomment this line to have DMA disabled before suspend and reenabled
# afterwards
# DISABLE_DMA=true

# Uncomment this line to attempt to reset the drive on resume. This seems
# to be needed for some Sonys
# RESET_DRIVE=true

# Add services to this list to stop them before suspend and restart them in 
# the resume process.
STOP_SERVICES="mysql "

# Restart Infra Red services on resume - off by default as it crashes some
# machines
RESTART_IRDA=false

# Switch to laptop-mode on battery power - off by default as it causes odd
# hangs on some machines
ENABLE_LAPTOP_MODE=false

---

### Post by pfeels on 2007-12-09
Dell XPS 410

Clean Install

Hibernate takes me back to boot to recover ...

Suspend, in order to recover I have to hit the computers power button, hit any key or the mouse does not work ...

If thats the least of my problems I'm fine, Ubuntu is an awesome piece of software

---

### Post by dex Otaku on 2007-12-10
Dell inspiron 6000 with clean 7.10 install.

Restricted ATI driver is installed and compiz is working [well, except for the fact that you have to choose between compiz and basic apps, or no compiz and working opengl and video playback, heh].  

I usually have compiz disabled altogether because I frequently use the notebook for watching videos with Miro.  The suspend/hibernate behavior is the same whether compiz is running or not.

Suspend is hit+miss, it appear to always get there, but usually [maybe 9/10 times] it won't wake up.  The rare times when it does wake up, the touchpad acts as though it's on crack.

Hibernate doesn't work at all; trying to enter hibernation begins with X closing, resulting in a text-mode screen with blinking cursor at top-left - it doesn't get any further than that.  Cold boot is required at that point.

Suspend and Hibernate both worked under Feisty, albeit without the restricted ATI driver installed.

I have not tried switching back to the OSS ATI driver and checking the system's behavior yet, but will be doing so.

---

### Post by Plotor on 2007-12-11
Dell Latitude D400... 

Clean Install of "Gutsy" 
- Initially had problems with Suspend/Hibernate /Shutdown 
- Initially WLAN did not work
- Keyboard would stop responding sporadically... 

Steps to resolve...
[LIST]
[*]Installed Broadcom firmware (3rd party)
[*]added to kernel in menu.lst - **acpi=force noapm pci=irqmask=0x0e98**
[*]edited /etc/x11/xorg.conf - replace "Intel Corporation 82852/855GM Integrated Graphics Device" with **i810** driver spec.
[/LIST]

Now Suspend Hibernate and Shutdown works without issues, Keyboard has not locked up since, and wireless is also working... 

Finally a *stable* linux distro with full functionality for a Latitude D400...

---

### Post by Lucasco on 2007-12-12
Dell Latitude D 505..

Clean Install of "Gutsy"
- Initially had problems with Suspend/Hibernate/Shutdown/Restart
- black screen, nothing works only hard restart (pushing power off button)

Please advice

Thanks 

Lucasco

---

### Post by OlyPerson on 2007-12-12
I've already posted my stats.

I was wondering if there is an "official" fix for this yet?  Why can't there just be an update or something?

---

### Post by MacHaddock on 2007-12-13
Dell Inspiron 2600 - Uppgraded from fiesty fawn - suspend f**ks up grafics somehow. Haven't tried hybernation yet.

---

### Post by Starman on 2007-12-13
After weeks of frustration because suspend won't work I finally decided to give a try to other distributions. I tried PClinuxOS 2007 and found that suspend did work but subsequently discovered that it runs a much older kernel (2.6.18 I think). Then I tried OpenSuse 10.3 and found that suspend on it also worked AND it is running the same kernel as gutsy. This raises questions...

If they can do it why can't gutsy?

Why has this problem with suspend been allowed to continue?

very frustrating.....

---

### Post by bluedragon436 on 2007-12-14
> **Starman said:**
> After weeks of frustration because suspend won't work I finally decided to give a try to other distributions. I tried PClinuxOS 2007 and found that suspend did work but subsequently discovered that it runs a much older kernel (2.6.18 I think). Then I tried OpenSuse 10.3 and found that suspend on it also worked AND it is running the same kernel as gutsy. This raises questions...

If they can do it why can't gutsy?

Why has this problem with suspend been allowed to continue?

very frustrating.....


Honestly I know that it seems a bit discouraging and pretty odd that they have gotten it to work correctly and that Gutsy still doesn't, but all in time....  I have run OpenSuse 10.3 and I with the exception of the hibernate/suspend issue...I would much rather choose to run Ubuntu...as I have already deleted OpenSuse off of my computer completely and stuck with my initial install of Gutsy....but that is just me...I can be patient and find a fix, for my computer...

---

### Post by jpkotta on 2007-12-14
Dell Latitude D610 with ATI graphics.

Before upgrade, suspend worked.  I'm not sure about hibernate because I never use it, but the last time I know it worked was in Hoary.

Upgraded using the alternative install CD.

After upgrading, neither suspend nor hibernate worked.  As others with D610 have posted, it gets stuck some where during suspend and needs a hard reset.  After unloading ATI fglrx driver with
```
sudo /etc/init.d/gdm stop
sudo modprobe -r fglrx
```
(execute from Linux console, not xterm) suspend works perfectly (didn't test hibernate).

I installed the latest ATI driver and suspend works perfectly, however the 3D acceleration is broken (DRI can't initialize).  This is with fglrx 8.433 from 2007-11.

ATI wiki says it's caused by the new SLUB allocator.  Apparently the only solution is to not use SLUB, by using a different kernel, or recompiling with SLAB, or etc.  Even the latest driver is broken with SLUB, so if I get 3D accel working, the suspend will probably break again.

---

### Post by therrmann on 2007-12-14
I have an older Dell Latitude CPx.  I upgraded to Gutsy it would not boot -- got kernel panic.  Booting from an earlier kernel, GDM would not work.  I took the plunge and did a clean install (wiping my Windows partition, but what the heck).  Now it boots fine, but will not shut down, suspend, or hibernate.  I cannot even log off or go to a Vterm.  If I try, the screen goes blank and whiteness slowly spreads over the screen.  I have to shut power off and restart.

---

### Post by fragpe on 2007-12-15
> **exquest said:**
> HI.  I can't hybernate or suspend my laptop without it hanging and causing my to do a complete reboot of the system.  I have a Dell Inspiron 5150 and did a clean install of ubuntu 7.10 and LOVE IT besides the pesky little not suspend or hybernate thing.  I would love a fix for this.

 Hi! I did a clean install and hibernate/suspend were not working.
I pull the information together after reading other forums. I changed the following. I am using the nvidia drivers BTW.
for suspend to work
[INDENT]edit /etc/default/acpi-support
# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=false[/INDENT]

for hibernate
[INDENT]edit /etc/X11/xorg.conf
find ther nvidia driver option
Option "NvAGP" "True"[/INDENT]
[INDENT]
/etc/modprobe.d/blacklist
# adding failure to suspend DELL 5150 ?? agpart
blacklist intel_agp
#prob blacklist this one too: blacklist agpart[/INDENT]

Make sure to test this with compiz disabled first. I hope this helps.

---

### Post by iprat on 2007-12-15
Here I'm running:

Dell Dimension 8400.
PCIx ATI Radeon X300

Suspend / Hibernate does not work.

Now with OSS ATI drivers and compiz disabled as hangs easily.

I'll play around with acpi settings and tell more if I found anything interesting... this is the only important issue I have with Ubuntu.

The other issue (not very important now) is that I cannot record anything from micro in the Audigy2 sound card.

---

### Post by El Lance-O on 2007-12-19
I have a Dell E1505n that was preloaded with Feisty, I upgraded to Gutsy, problems happened, and I had to do a fresh install.

I have a Nvidia 7300 Go card, and suspend works, but only if I turn compiz off. It used to never work, but I did the "POST_VIDEO=false" edit which seemed to somewhat fix it. It still acts pretty screwy when it does it's thing.

Hibernate doesn't work at all. It will shutdown, and come back with a scrambled graphic behind the mouse. I have to restart X to continue at that point. And this is the feature that I want the most, as my battery likes to die after an hour and a half for some reason. :confused:

---

### Post by OlyPerson on 2007-12-19
> **Dellfan said:**
> Try adding a file to /etc/acpi/resume.d

99-network-manager.sh:
```
#!/bin/sh
/etc/dbus-1/event.d/25NetworkManager restart
```


with the following ownership/permissions:

-rwxr-xr-x 1 root root 55 2007-10-23 20:58 99-network-manager.sh

This will restart the Network Manager on resume, which should resolve your network issues.

How do I add that in there?  Do I just type in what is in the code?

---

### Post by jw5801 on 2007-12-19
Use ```
gksu gedit /etc/acpi/resume.d/99-network-manager.sh
```Then copy and paste the code above, then run in a terminal: ```
sudo chmod 755 /etc/acpi/resume.d/99-network-manager.sh
```

---

### Post by bigboyman2 on 2007-12-19
Dell inspiron 1500 laptop, running gutsy 7.10

suspend/works, and wireless automatically comes up. But only after I unsuspend

Okay, wireless works before I suspend the laptop (closing the lid), and automatically connects after I unsuspend. But is there a way for the wireless to stay on during suspension? Or is there a way for me closing the lid, for the screen to lock, not to suspend or hibernate? I only have those two options, or to blank screen, or do noting. I want to be able to have my applications running and connected to the internet, but still have a lock on the screen when I open my laptop lid.

I mean, I could chose it to blank screen on lid close, and manually lock it, but if there's a way to set lid close as lock screen, that'd be nice

---

### Post by ayu on 2007-12-22
* Vostro 1400, core2, 8400gs, dell wireless, upgraded from feisty (suspend/hibernate didnt work on feisty), using compiz
* standby works as far as i can tell (sound and wireless resume when i start it back up).
* hibernate crashes the system, must kill it via the power switch.
* using nvidia driver from restricted drivers, ran the commands on [http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/8400M_Suspend_Hibernate-Failure](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/8400M_Suspend_Hibernate-Failure)

Hopefully somebody can let me know how to get hibernation to work, seeing that standby works at least the couple times I've tested so far

---

### Post by noodles12 on 2007-12-26
> **Plotor said:**
> Dell Latitude D400... 

Clean Install of "Gutsy" 
- Initially had problems with Suspend/Hibernate /Shutdown 
- Initially WLAN did not work
- Keyboard would stop responding sporadically... 

Steps to resolve...
[LIST]
[*]Installed Broadcom firmware (3rd party)
[*]added to kernel in menu.lst - **acpi=force noapm pci=irqmask=0x0e98**
[*]edited /etc/x11/xorg.conf - replace "Intel Corporation 82852/855GM Integrated Graphics Device" with **i810** driver spec.
[/LIST]

Now Suspend Hibernate and Shutdown works without issues, Keyboard has not locked up since, and wireless is also working... 

Finally a *stable* linux distro with full functionality for a Latitude D400...

dell 700m integrated graphics gutsy clean install. 

this combined with the Post_video=FALSE got my suspend working perfetly!!! thanks. 

Hibernate doesn't work and just locks the screen and i can just sign back in, but i don't really use hibernate. 

I'm not even sure if the Post_video is needed but i had it changed to that from previous tries. Will test out soon.

---

### Post by MrSootentai on 2007-12-26
[COLOR="Red"]Dell 1420[/COLOR] (not 1420N)
Suspend works, Hibernate has errors.

Clean Install.
Suspend is working prefectly with no error, but hibernating goes to blank screen and returns to 'enter password' prompt.

***NOTE: I think it may be a problem with my Intel Mobile GM965/GL960 Integrated Graphics Controller video card, but I've never been able to confirm it.**

This is pretty much the major thing that seperates my major usage from ubuntu and my vista partition.

---

### Post by ayu on 2007-12-27
Has anybody tried a clean install from the Dell 7.10 dvd (for the inspiron 1420n)?  Does hibernate work with that?  If not, then I can give up on fixing hibernate until the next release.

---

### Post by jacobssmithy on 2007-12-28
> **Plotor said:**
> Dell Latitude D400... 

Clean Install of "Gutsy" 
- Initially had problems with Suspend/Hibernate /Shutdown 
- Initially WLAN did not work
- Keyboard would stop responding sporadically... 

Steps to resolve...
[LIST]
[*]Installed Broadcom firmware (3rd party)
[*]added to kernel in menu.lst - **acpi=force noapm pci=irqmask=0x0e98**
[*]edited /etc/x11/xorg.conf - replace "Intel Corporation 82852/855GM Integrated Graphics Device" with **i810** driver spec.
[/LIST]

Now Suspend Hibernate and Shutdown works without issues, Keyboard has not locked up since, and wireless is also working... 

Finally a *stable* linux distro with full functionality for a Latitude D400...

PLOTOR,

I'm glad to see that somebody else has a d400 and has full functionality.  Could you explain in more detail how to "add to kernel in menu.lst?"  I'm am not sure how to do this.  Where you able to get your touchpad to work properly?

Any help would be greatly appreciated,
Jacob

---

### Post by GSBoomer on 2007-12-28
I just did a clean install on a new hard drive with the 7.10 CD and, after 149 upgrades, suspend works flawlessly every time, including the wireless network, on my e1505.

I haven't tried hibernation yet.

---

### Post by dimaoo7 on 2007-12-29
Dell E1505 with ATI x1400. Clean install
Standby and hibrenate do not work. Tried the solutions from the wiki entry :
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide")
Still no luck.:(

---

### Post by neptho on 2007-12-30
Dell Vostro 1400 w/ onboard Intel video.
 
 Clean Install of "Gutsy" 
 - Keyboard would stop responding sporadically after resume from Standby.

Steps to resolve (workaround):

Create these files:

**/etc/acpi/resume.d/45-i8042-input.sh**:
```
#!/bin/sh

# Rebind the AT keyboard interface.
if [ -f /sys/bus/platform/drivers/i8042/bind ]; then
  echo -n "i8042" > /sys/bus/platform/drivers/i8042/bind
fi
```

**/etc/acpi/suspend.d/20-i8042-input.sh**:
```
#!/bin/sh

# Unbind the AT keyboard interface.
if [ -f /sys/bus/platform/drivers/i8042/unbind ]; then
  echo -n "i8042" > /sys/bus/platform/drivers/i8042/unbind
fi
```

Make sure they have proper permissions:

```
sudo chmod 755 /etc/acpi/suspend.d/20-i8042-input.sh
sudo chmod 755 /etc/acpi/resume.d/45-i8042-input.sh
sudo chown root.root /etc/acpi/suspend.d/20-i8042-input.sh
sudo chown root.root /etc/acpi/resume.d/45-i8042-input.sh
```

Now, the next time you suspend (and resume), from here-on, your mouse and keyboard will work.

---

### Post by biohzrd on 2007-12-31
> **neptho said:**
> Dell Vostro 1400 w/ onboard Intel video.
 
 Clean Install of "Gutsy" 
 - Keyboard would stop responding sporadically after resume from Standby.

Steps to resolve (workaround):

Create these files:

**/etc/acpi/resume.d/45-i8042-input.sh**:
```
#!/bin/sh

# Rebind the AT keyboard interface.
if [ -f /sys/bus/platform/drivers/i8042/bind ]; then
  echo -n "i8042" > /sys/bus/platform/drivers/i8042/bind
fi
```

**/etc/acpi/suspend.d/20-i8042-input.sh**:
```
#!/bin/sh

# Unbind the AT keyboard interface.
if [ -f /sys/bus/platform/drivers/i8042/unbind ]; then
  echo -n "i8042" > /sys/bus/platform/drivers/i8042/unbind
fi
```

Make sure they have proper permissions:

```
sudo chmod 755 /etc/acpi/suspend.d/20-i8042-input.sh
sudo chmod 755 /etc/acpi/resume.d/45-i8042-input.sh
sudo chown root.root /etc/acpi/suspend.d/20-i8042-input.sh
sudo chown root.root /etc/acpi/resume.d/45-i8042-input.sh
```

Now, the next time you suspend (and resume), from here-on, your mouse and keyboard will work.

I tried what you posted here because I am having similar problems on resume from suspend on my Vostro 1400. Essentially after I enter my password at the prompt with a black screen, my keyboard input is not recognized, my mouse clicks are not recognized, but SOMEHOW I can move the pointer and use my Fn keys to increase my brightness and put the laptop back to sleep. I tried your method and it did not fix my problem. Maybe we are having different issues or does this sound similar?

---

### Post by mrund on 2008-01-01
I'm running Gutsy on a Dell Inspiron 6000 laptop. Clean upgrade from Feisty,

The problem I have is with suspend. After suspension, when I wake the machine, it goes into operational mode, says something about the suspension not having been successful, and then drops into hibernation!? Then, when I press the power switch, it starts nicely.

---

### Post by GSBoomer on 2008-01-01
This is my third time posting to this thread when I *think* I have all the suspend/hibernation stuff worked out. I may be wrong, but I think this will be the last time.

I did a completely clean gutsy install on a new hard drive in my Dell e1505 and both hibernation and suspend worked ... at first. After a few days, suspend began to fail. Either the keyboard would not respond, or the screen would stay black.

After applying the scripts in neptho's post (#214), suspend and hibernation seem to be working finally.

---

### Post by neptho on 2008-01-02
> **biohzrd said:**
> I tried what you posted here because I am having similar problems on resume from suspend on my Vostro 1400. Essentially after I enter my password at the prompt with a black screen, my keyboard input is not recognized, my mouse clicks are not recognized, but SOMEHOW I can move the pointer and use my Fn keys to increase my brightness and put the laptop back to sleep. I tried your method and it did not fix my problem. Maybe we are having different issues or does this sound similar?

Your problem seems different than mine; my keyboard and mouse entirely fail to registered at all; so I made this to tell it to 'forget 'em', then 'reset 'em'.

This is mostly working for me, but I've still got an obnoxious 'keyboard stuck repeating characters' bug that's still driving me nuts.

---

### Post by cotcot on 2008-01-02
GA-m55plus S3G motherboard with AMD Athlon 64x2 3800+ processor.
Suspend and hibernate do not work.
I get a error "your computer fails to go in sleep mode" (or soimething like that). After a while i get a login screen to enter the password. Entering the password gives the desktop back. Power was not of in both cases (suspend and hibernate).

---

### Post by nmehta6 on 2008-01-02
Dell Inspiron 1501

Installed Gutsy Final from scratch. Any fixes for this to work again?

---

### Post by eskimojoe85 on 2008-01-02
> **mrund said:**
> I'm running Gutsy on a Dell Inspiron 6000 laptop. Clean upgrade from Feisty,

The problem I have is with suspend. After suspension, when I wake the machine, it goes into operational mode, says something about the suspension not having been successful, and then drops into hibernation!? Then, when I press the power switch, it starts nicely.

Dell Inspiron 6000. Clean install of Gutsy from live CD.

My laptop is doing the same thing as mrund.

---

### Post by Paul S on 2008-01-02
> **dimaoo7 said:**
> Dell E1505 with ATI x1400. Clean install
Standby and hibrenate do not work. Tried the solutions from the wiki entry :
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide")
Still no luck.:(

OK, I think I have the same hardware and just now seem to have it working.  You followed the wrong guide.  The fix from ATI is in fglrx version 7.12, from [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide).    Make sure you follow the one for gutsy not edgy! The Guide works ok, but forgot to say that you have to edit  /etc/defaults/acpi-support.  Thanks to someone earlier in this post, these changes seem to work:

MODULES_WHITELIST="fglrx"
MODULES="usbhid,uhci_hcd"
SAVE_VBE_STATE=false
POST_VIDEO=false
DOUBLE_CONSOLE_SWITCH=true

The usbhid and uhci_hcd are useful if you have a usb keyboard, printer or camera, but not necessary if you don't.  No harm to include them though, in case you get one later.

This still does not work with Desktop Effects (compiz), but seems good without compiz.

I also tried the radeonhd driver (also recommended earlier in this thread) and had 100% success with it.  But radeonhd does not yet support TV-out or 3D acceleration or compiz.

HTH,

---

### Post by dimaoo7 on 2008-01-03
> **Paul S said:**
> OK, I think I have the same hardware and just now seem to have it working.  You followed the wrong guide.  The fix from ATI is in fglrx version 7.12, from [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide).    Make sure you follow the one for gutsy not edgy! The Guide works ok, but forgot to say that you have to edit  /etc/defaults/acpi-support.  Thanks to someone earlier in this post, these changes seem to work:

MODULES_WHITELIST="fglrx"
MODULES="usbhid,uhci_hcd"
SAVE_VBE_STATE=false
POST_VIDEO=false
DOUBLE_CONSOLE_SWITCH=true

The usbhid and uhci_hcd are useful if you have a usb keyboard, printer or camera, but not necessary if you don't.  No harm to include them though, in case you get one later.

This still does not work with Desktop Effects (compiz), but seems good without compiz.

I also tried the radeonhd driver (also recommended earlier in this thread) and had 100% success with it.  But radeonhd does not yet support TV-out or 3D acceleration or compiz.

HTH,
Thank you for your response,
I tried to change the settings as recommended and disabled desktop effects but still no luck.
But is it safe to assume that right now I can't have both the compiz effecst and standby working?

---

### Post by crazyfish666 on 2008-01-03
> **AaronMT said:**
> Hello,
On to the problem.


Dell Inspiron 6400

I have never been able to get it out of hibernate, I thought I was just an idiot and wasn't doing the right thing.

---

### Post by Paul S on 2008-01-03
> **dimaoo7 said:**
> Thank you for your response,
I tried to change the settings as recommended and disabled desktop effects but still no luck.

Make sure you reboot after making those changes.

Also, open a terminal and enter the command
```
grep fglrx /var/log/messages*
```
and look for a line like this:

/var/log/kern.log.0:Jan  2 20:22:31 localhost kernel: [   28.704000] [fglrx] module loaded - fglrx 8.44.3 [Dec 19 2007] on minor 0


The important part is "module loaded - fglrx 8.44.3" (the version number 8.44.3).  If you don't have this same version, then you need to try again to follow the installation procedure.

> 
But is it safe to assume that right now I can't have both the compiz effecst and standby working?

Yes, that's correct.  And if you can't get the fglrx working, then the radeonhd driver at [http://wiki.x.org/wiki/radeonhd](http://wiki.x.org/wiki/radeonhd) will be a good alternative.

HTH

---

### Post by deatom on 2008-01-05
Hi all,
Dell Inspiron 6400 with ATI Mobility Radeon x1400 - upgraded from feisty

With ATI's Catalist 7-12 (aka fglrx 8.443) the system hibernates and suspends well. I have problems with resume from suspend:

For the first look, the laptop resumes normally. About 30 secs after resume i get **enormous disk activity**, so the system does not respond, hard reset is needed.

Framebuffer is disabled, it seemms not to be related to network-manager, compiz and AIGLX nor XGL.
Before the Catalyst 7-12, suspend/resume worked in Gutsy with the 2.6.20 Feisty kernel, but a custom compiled, SLAB-enabled 2.6.22 kernel gave the above symptoms with the disk activity.

Any hints?

---

### Post by BrewBelly on 2008-01-06
Dell Inspiron 1300

Finally got Suspend (both GUI and closing lid) to work.

Still no hibernate.

I edited /etc/default/acpi-support

# Should we attempt to warm-boot the video hardware on resume?
from POST_VIDEO=true to FALSE

as described several times in this massive thread.

I guess this is as good as it's going to get for now.

---

### Post by dustman on 2008-01-10
I have a Toshiba Satellite A100-529. Fresh Gutsy installation, but suspend and hibernate do not work (they haven't worked neither in feisty, edgy or dapper)....tried a lot of solutions from this thread, none did the job. When i try to hibernate, i get a black screen with a white cursor blinking in the upper left corner...when i try to suspend, i get only the blck screen without the cursor...perhaps someone with someone with a little more experience is needed to solve this :|



Cheers!

Radu

---

### Post by kvonb on 2008-01-10
-

---

### Post by ellaguno on 2008-01-10
It's not stupid question is an unsolved problem how each laptop works with Suspend/hibernate, in theory:
- Suspend freezes everything leaving just enough power to memory so when you come back you restart almost inmediatly where you left things. When it works you just have to put your password and get back where you were.
- Hibernate: sends an image of the memory to the HardDisk so when you boot up it loads the state where you were back (it takes longer).

The problem is fine configuration and in my case when I update something sometimes it crash again. For instance, when you use compiz you should configure sme issues to let Suspend work.

:guitar:

---

### Post by kvonb on 2008-01-10
-

---

### Post by achortleaday on 2008-01-10
Inspiron 1501, Install to 7.10.
Suspend shuts of screen, but does not start flashing the power light. Will not respond to any buttons, so hence won't wake up.
Hibernate sends laptop to blank black screen, but never shuts off and again doesn't respond to buttons.
Whenever I try either I just have to manually restart.

---

### Post by ghettosamson on 2008-01-10
I had the same issue on my dell inspiron 1501 and For anyone who cares, this fixed my problems. I disabled the restricted ATI graphics card driver in 7.10, rebooted the pc and hibernate works again!

Too bad to have to choose between using the (better) restricted graphics driver or the hibernate function, though.

Anyway, try it on your machine, it might work for you too...

---

### Post by deniz_erdem on 2008-01-18
dell latitude d505 
clean installation of 7.10 
dual booting with xp

i can't shut down, hipernate, or even log off. i get a non responsive black screen.

---

### Post by kcoombs on 2008-01-18
It looks like the latest ATI Catalyst driver is supposed to fix the issue... any ideas when it will show up in the official update channel?

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_81_linux.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_81_linux.html)

Resolved Issues:

Suspending to RAM or DISK on kernel version 2.6.23 or later no longer fails

---

### Post by Chimera76 on 2008-01-18
Inspiron 6400...have had no issues with Hibernate or Stand-by yet on a fresh install. 

If I had any complaint at all it would be that during the reload from Hibernate it put a wierd block of lit pixels on my screen (kinda looked like static on an old tv) about the size of a quarter. they were there for about 30 seconds then it booted fine the rest of the way.

---

### Post by poscaman on 2008-01-19
Hasee w225r.

suspend/hibernate didn't work.i fix it using the new drivers as described above.now,everything works fine.

---

### Post by ghettosamson on 2008-01-19
so i was reading the release info on the new ati catalyst. says it supports ati radeon x1100 which is the one i have installed on my laptop. but i cant find it on the list to download the driver. is it safe for me to download the x1300 one?

---

### Post by rozen on 2008-01-23
XPS 410, 
4GB ram,
Gutsy,
Nvidia  GeForce 7300 LE, proprietary nvidia driver,
usb keyboard

Applied the modifications from: [http://koon.fr/wiki/suspend_to_ram_on_the_dell_d820_proprietary_nvidia_drivers_under_ubuntu_gutsy](http://koon.fr/wiki/suspend_to_ram_on_the_dell_d820_proprietary_nvidia_drivers_under_ubuntu_gutsy)

Then the system would resume after suspend but without a functioning keyboard, while the usb mouse would work. (At least I could reboot.)  Then applied the change 

MODULES="usbhid,uhci_hcd"

to /etc/default/acpi-support as suggested in a couple of posts. It seemed to have no effect.

I am about ready to give up on Gutsy and revert to Feisty where I have no problem with suspend/resume. I am willing to try almost any suggestion.

I hope that somebody will fix in the next release what they broke in Gutsy.  With the whole world going green, it is too bad that the Linux folks don't give this function as much priority as eye candy.

---

### Post by mikaelsnavy on 2008-01-24
> **fragpe said:**
> Hi! I did a clean install and hibernate/suspend were not working.
I pull the information together after reading other forums. I changed the following. I am using the nvidia drivers BTW.
for suspend to work
[INDENT]edit /etc/default/acpi-support
# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=false[/INDENT]

for hibernate
[INDENT]edit /etc/X11/xorg.conf
find ther nvidia driver option
Option "NvAGP" "True"[/INDENT]
[INDENT]
/etc/modprobe.d/blacklist
# adding failure to suspend DELL 5150 ?? agpart
blacklist intel_agp
#prob blacklist this one too: blacklist agpart[/INDENT]

Make sure to test this with compiz disabled first. I hope this helps.

I have a Dell 1505 with the Nvidia 7300 and hibernate and standby didn't work by default.. I did the above AND EVERYTHING WORKS!!! THANKS!!!

---

### Post by blastfm on 2008-01-31
My desktop can come in and out of hibernate without problems. Well, not exactly. 

When I click on the "Quit" button and choose "Standby" or "Hibernate" the system just goes to Standby mode (HDD and fans are still running) and I cant bring it back up except via a hard reset. 
But when I press the sleep button on the keyboard (button with the crescent moon and "Zzzzz") the desktop goes to hibernate (no video activity, no HDD activity, temp monitor LCD dies, no fans running, only a blinking power LED), and I can bring it back up by pressing the power button.

My problem is, when I bring it up and there happens to be a CD/DVD on the drive, the system crashes (no keyboard response, cant eject CD/DVD via right click or eject button, then screen gets this distorted whatever) and cant even do a CTRL+ALT+Backspace. The only way is to re-start the system before it crashes (only via mouse control) or a hard reset.

Any idea why the CD/DVD is causing this?

---

### Post by YannBuntu on 2008-01-31
> **deniz_erdem said:**
> dell latitude d505 
clean installation of 7.10 
dual booting with xp

i can't shut down, hipernate, or even log off. i get a non responsive black screen.

Deniz_erdem, I have the same configuration and same problem. Did you manage to fix it?

Links for your information:
[http://ubuntuforums.org/showthread.php?p=4190287]("http://ubuntuforums.org/showthread.php?p=4190287")
[http://ubuntuforums.org/showthread.php?t=590875]("http://ubuntuforums.org/showthread.php?t=590875")

---

### Post by noisygecko on 2008-02-01
Here is my setup:
[INDENT]dell inspiron 710m
clean installation of 7.10
dual booting with xp
[/INDENT]
Has anyone figured out how to fix the shutdown problems?  When I shutdown it almost never actually shuts down. The screen goes blank but the power light never goes off.  I have to hold the power button for 5 seconds to stop it and then restart.  This seems to happen with shutdown, restart and the other modes as well.

I have never gotten suspend or hibernate to work, either.

-Sim

---

### Post by Sugz on 2008-02-02
Shutdown, suspend and Hibernate work fine, but my Touchpad does not work after Suspend. Once restarted it is fine though

---

### Post by dahlheim on 2008-02-02
> **alchemistz06 said:**
> This has made my suspend work so far. On the last three tries so far. I'm pretty stoked. My system M1210, Envy, Nvidia Ver. 100.14.19. Also running Compiz-Fusion.

same here, these changes fixed my issue.  this was, with m1210, fresh gutsy install (using /home/.* from feisty, but i assume that probably doesn't matter much), where suspend (to RAM, all i ever use) worked fine in feisty, with gutsy it would suspend to S3 on lid closure, then reboot system on opening lid.

Modify /etc/default/acpi-support:

SAVE_VBE_STATE=false

POST_VIDEO=false



Append to /etc/modprobe.d/blacklist:

blacklist intel_agp

blacklist agpgart



Modify xorg.conf Device Section to include:

Option "NvAGP" "1"


----
THANKS!  :guitar:

---

### Post by Sugz on 2008-02-02
By the ways is there a solution to my above post? about the touchpad not working after Suspend?

---

### Post by thedaylights on 2008-02-02
Lenovo X60 laptop
Fresh install of Gutsy

When returning from a hibernate command, laptop boots through bios then Grub to boot Linux. It looks like a full reboot to me. Also gives message of possible data loss due to improper shutdown of external drive.

---

### Post by SonicJMC on 2008-02-03
I've got a custom built machine.

Motherboard: MSI K9A Platinum
Video: ATi Radeon 9800 (only works properly with proprietary drivers)
Processor: AMD Anthlon X2


Ubuntu Breezy, Feisty, and Gutsy, both 32-bit and 64-bit versions, all had the same problem. Sleep and hibernate fail to resume, and nothing I do seems to fix it.
Sleep and Hibernate both work perfectly in Windows.

I haven't yet seen a machine properly sleep in Ubuntu.

---

### Post by Michl on 2008-02-03
no problem with hibernate and suspend in Feisty on a
Dell CS610 laptop.  But the lid function never works.
Stays on in Feisty and goes black and stays black
in Heron.  Have to reboot.

Upgrades in all cases.

---

### Post by bisbebri on 2008-02-05
Insprion 1501 Clean Install   Downgraded bios 1.7

---

### Post by hetti012 on 2008-02-07
I'm having problems when resuming from hibernate on a Dell Dimension 2400. I run Ubuntu 7.10 (full installation - dual boot with XP) and have an nvida videocard with restricted drivers with full desktop effects turned on.

---

### Post by daw3rd on 2008-02-08
IBM thinkpad t41p.
Install 7.10 today.  
Standby using Fn->F4 or dialog box leaves moon light flashing, but nothing seems to resume it.  Tried all keys, ctl-alt-del, and power key only reboots.  Help.

---

### Post by daw3rd on 2008-02-08
A previous post specifying the following fixed the problem on my t41p laptop...

Modify /etc/default/acpi-support:

SAVE_VBE_STATE=false

POST_VIDEO=false



Append to /etc/modprobe.d/blacklist:

blacklist intel_agp

blacklist agpgart



Modify /etc/X11/xorg.conf Device Section to include:

Option "NvAGP" "1"

---

### Post by PsychedelicReaction on 2008-02-11
XPS 1440 (Vista preinstalled)

Standby: seems to work
Hibernate: get this error "uvcvideo: failed to query (135) UVC control 1 (unit 0)

:(

---

### Post by RichTJ99 on 2008-02-11
> **daw3rd said:**
> A previous post specifying the following fixed the problem on my t41p laptop...

Modify /etc/default/acpi-support:

SAVE_VBE_STATE=false

POST_VIDEO=false



Append to /etc/modprobe.d/blacklist:

blacklist intel_agp

blacklist agpgart



Modify /etc/X11/xorg.conf Device Section to include:

Option "NvAGP" "1"

This fixed the issue on my Dell XPS M1210 laptop with Nvidia 7400 video card.

---

### Post by jw5801 on 2008-02-11
You need to open it as root:
```
gksu gedit /etc/default/acpi-support
```

---

### Post by Keyper7 on 2008-02-11
Vostro 1400 with NVIDIA GeForce 8400M GS and intel wireless.
Fresh install of Gutsy amd64.

After installing the nvidia proprietary drivers and enabling vesafb, both suspend and hibernate seem to work fine. However, it failed to resume from hibernate ONCE, it hung on "suspending console". I've hibernated other times after that and never happened again.

I have no idea what caused that single failure.

---

### Post by leftyfb on 2008-02-11
Got mine fixed!

Dell Inspiron 9300
Nvidia Go 6800
Fresh install of Gutsy
Suspend would log me out of my session when resuming. Tried the posted changes to xorg.conf and acpi-support, but that only caused the black screen on resume problem. 


The solution which was suggested to me, the latest Nvidia driver from their site: 169.09 as of this post. 

I still have the following changes left in .. everything is working so i'm not going to "fix" it right now :)

Modify /etc/default/acpi-support:

SAVE_VBE_STATE=false
POST_VIDEO=false

Modify /etc/X11/xorg.conf Device Section to include:

Option "NvAGP" "1"

---

### Post by rozen on 2008-02-12
A question for Keyper7:

You mention enabling vesafb as part of getting suspend and hibernate to work.   How does one go about enabling vesafb?

I notice that I the vesafb driver is in the system but there is no /dev/fb0. 

Many Thanks in Advance,
Don

---

### Post by Keyper7 on 2008-02-12
Hi rozen,

Here are the steps to enable vesafb:

1) edit /etc/initramfs-tools/modules and add the lines
fbcon
vesafb

2) edit /etc/modprobe.d/blacklist-framebuffer and
comment out the line "blacklist vesafb"

3) sudo update-initramfs -u

4) install hwinfo (sudo apt-get install hwinfo) and run
sudo hwinfo --framebuffer
You should see a list of resolutions and their hexadecimal
codes. Remember the code of the resolution you want
(for example, mine is 0x0365)

5) finally, add vga=<code you chose in step 4> to the
kernel parameters you use to boot (edit /boot/grub/menu.lst)

Reboot and, if everything works, you should now have a
gorgeous high-resolution console. :)

---

### Post by pvravi on 2008-02-13
A separate thread did not create any responses. Hoping this thread is the right forum for this Q: 

I installed gOS Rocket on a Dell Latitude L400 (P3 Coppermine), and have been having some powersave mode problems.

Initially gOS did NOT install acpid and laptop_mode during the OS install. I installed both later (with apt-get). However, lid state always shows "closed".

If I run acpitool -s to suspend from the command line and then bring it back up, the lid state is good, but I think the fan stays off - which might cause problems in the long run.

In any case, although the lid state is good (open for open and closed when closed) after acpitool -s, closing the lid still does not suspend the machine -just the screen goes off, which I think is hardwired to the lid-button anyway (so acpi or Linux isn't doing anything there).

How do I get the machine to suspend when the lid is closed, and the machine to turn on correctly (with the fan on) when I bring it out of suspend?

I had Ubuntu Gutsy on the same laptop just before my gOS misadventure, and it was perfectly OK on the suspend. Just wanted to indicate that there are no Hardware problems.

Someone please help.

---

### Post by Acapulco on 2008-02-13
Dell Inspiron 1420
     Core 2 Duo T7500 2.2
     4GB RAM

Ubuntu 7.10 x86 clean install 

Dual boot with Vista Business (only option at purchase time unfortunately)

---

### Post by pressed on 2008-02-16
i also had a problem with standby recently... by default by dell inspiron 6000 was able to boot and standby/resume no problem, but yesterday I put it on Sleep while no processes were running (to the best of my knowledge) and on resume I got a "kernel panic"

there was no response to alt+SysRq and i had to do a hard reboot. I got a gdm error and had to boot into recovery mode... after a manual fsck i was able to reinstall gdm from synaptic and now everything seems fine. (thank god i didnt need to download any files)

---

### Post by Brad811 on 2008-02-16
I put my Dell Inspiron B130 laptop into hibernating, and it wouldn't restart. I had to hold down the power button. Now when I turn it on, it gets all the way to the Ubuntu logo with the orange load bar. The orange load bar baaarely gets any orange in it, maybe this much: [], and then stops, and eventually goes to a completely blank screen with an underscore "__" in the top left. I can do nothing from this screen. I have tried starting in recovery mode, nothing. I tried setting the kernel boot option to "noresume", same thing.

I need to do anything I can to fix this. If someone can tell me how to get permission to access files from a live CD that would be fine too. I just really need to fix this ASAP.

---

### Post by dahlheim on 2008-02-16
> **Brad811 said:**
> I put my Dell Inspiron B130 laptop into hibernating, and it wouldn't restart. I had to hold down the power button. Now when I turn it on, it gets all the way to the Ubuntu logo with the orange load bar. The orange load bar baaarely gets any orange in it, maybe this much: [], and then stops, and eventually goes to a completely blank screen with an underscore "__" in the top left. I can do nothing from this screen. I have tried starting in recovery mode, nothing. I tried setting the kernel boot option to "noresume", same thing.

I need to do anything I can to fix this. If someone can tell me how to get permission to access files from a live CD that would be fine too. I just really need to fix this ASAP.

for me, it would be important to next see where the thing is hanging up on boot.  the first step i usually employ is to boot without the splash logo.  if i remember, when grub starts, you press "e" (for edit), then remove the "splash" parameter from the boot string that appears, then "b" to continue booting.  the system will then boot showing textual progress rather than the boot screen, and you can see where it's hanging up.

---

### Post by dahlheim on 2008-02-16
> **Brad811 said:**
> I put my Dell Inspiron B130 laptop into hibernating, and it wouldn't restart. I had to hold down the power button. Now when I turn it on, it gets all the way to the Ubuntu logo with the orange load bar. The orange load bar baaarely gets any orange in it, maybe this much: [], and then stops, and eventually goes to a completely blank screen with an underscore "__" in the top left. I can do nothing from this screen. I have tried starting in recovery mode, nothing. I tried setting the kernel boot option to "noresume", same thing.

I need to do anything I can to fix this. If someone can tell me how to get permission to access files from a live CD that would be fine too. I just really need to fix this ASAP.

if you need to quickly access the files on your hard drive using the live cd, that shouldn't be very hard either.  you open a terminal, type "df" to show the partitions you have, then make a new directory "mkdir" to temporarily mount the desired partition on, then mount it ("sudo mount -t ext3 /dev/{partition} {newdirectoryname}"), or something similar.

---

### Post by Brad811 on 2008-02-16
> **dahlheim said:**
> for me, it would be important to next see where the thing is hanging up on boot.  the first step i usually employ is to boot without the splash logo.  if i remember, when grub starts, you press "e" (for edit), then remove the "splash" parameter from the boot string that appears, then "b" to continue booting.  the system will then boot showing textual progress rather than the boot screen, and you can see where it's hanging up.

Ok, I am yet to try your suggestion for moving my files, but I did change the splash option, and here is what I got:

Starting up ...
Loading, please wait...
kinit: name_to_dev_t(/dev/disk/by-uuid/[long hex value]) = sda5(8,5)
kinit: trying to resume from /dev/disk/by-uuid/[same long hex value]
kinit: No resume image, doing normal boot...

...and that is where it stops. I then get the blinking underscore, and am able to type. edit: I am able to type for a few minutes, then I can do nothing. The keyboard is totally unresponsive, except for the fact that I can brighten and darken the screen... Other than that, absolutely nothing.

Know what I need to do?

Thanks for your help.

---

### Post by dahlheim on 2008-02-16
> **Brad811 said:**
> Ok, I am yet to try your suggestion for moving my files, but I did change the splash option, and here is what I got:

Starting up ...
Loading, please wait...
kinit: name_to_dev_t(/dev/disk/by-uuid/[long hex value]) = sda5(8,5)
kinit: trying to resume from /dev/disk/by-uuid/[same long hex value]
kinit: No resume image, doing normal boot...

...and that is where it stops. I then get the blinking underscore, and am able to type. edit: I am able to type for a few minutes, then I can do nothing. The keyboard is totally unresponsive, except for the fact that I can brighten and darken the screen... Other than that, absolutely nothing.

Know what I need to do?

Thanks for your help.

two questions:
1) does anything happen if you control-alt-backspace?
2) can you get a prompt from that point?  either (a) by just pressing enter, or (b) by control-alt-F1?

if #1 didn't work, then if #2 did, then try this:
[http://cinnamonpirate.com/blog/497/](http://cinnamonpirate.com/blog/497/)

---

### Post by Brad811 on 2008-02-16
> **dahlheim said:**
> two questions:
1) does anything happen if you control-alt-backspace?
2) can you get a prompt from that point?  either (a) by just pressing enter, or (b) by control-alt-F1?

if #1 didn't work, then if #2 did, then try this:
[http://cinnamonpirate.com/blog/497/](http://cinnamonpirate.com/blog/497/)

1. From the underscore, pressing ctrl-alt-backspace just puts out "^[^H"

2. No, when I press enter it just goes down to the next line, and nothing happens when I press ctrl-alt-F1

I'm really worried having to hard-reset my computer this many times, I may just have to copy my partition like you said.

BTW my fan is still running while it's sitting there doing nothing, and my processor is still somewhat hot, so it must be doing something.

---

### Post by dahlheim on 2008-02-16
> **Brad811 said:**
> 1. From the underscore, pressing ctrl-alt-backspace just puts out "^[^H"

2. No, when I press enter it just goes down to the next line, and nothing happens when I press ctrl-alt-F1

I'm really worried having to hard-reset my computer this many times, I may just have to copy my partition like you said.

BTW my fan is still running while it's sitting there doing nothing, and my processor is still somewhat hot, so it must be doing something.

i doubt all those hard resets will hurt anything for the moment.

can you boot into recovery mode in order to reestablish your swap partition as described in the link provided?

---

### Post by Brad811 on 2008-02-17
> **dahlheim said:**
> i doubt all those hard resets will hurt anything for the moment.

can you boot into recovery mode in order to reestablish your swap partition as described in the link provided?

no, won't reboot in recovery mode either.

it tries to resume again, then says:

kinit: trying to resume from /dev/disk/by-uuid/[hex]
[4.052000]Attempting manual resume
kinit: No resume image, doing normal boot...
Done.

[4.068000]EXT3-fs: INFO: recovery required on readonly filesystem.
[4.068000]EXT3-fs: write access will be enabled during recovery
[4.100000]kjournald starting. Commit interval 5 secconds
[4.100000]EXT3-fs: sda1: orphan cleanup on readonly fs

---

### Post by jw5801 on 2008-02-17
Try booting from a LiveCD and running fsck on your Ubuntu hard drive.

---

### Post by chadeldridge on 2008-02-17
> **MarilenCorciovei said:**
> Thanks a lot for all the info on this thread. Finally [suspend works for m]("http://www.len.ro/work/tools/ubuntu-gutsy-on-a-dell-latitude-d820/install-gutsy/view")e on a Dell D820 with Gutsy.


Thank you a ton this worked perfectly on the Dell XPS M1710.  Finally suspend is working.

---

### Post by bluedragon436 on 2008-02-17
Tried this...and it didn't work for my Dell D610

---

### Post by Brad811 on 2008-02-17
> **dahlheim said:**
> if you need to quickly access the files on your hard drive using the live cd, that shouldn't be very hard either.  you open a terminal, type "df" to show the partitions you have, then make a new directory "mkdir" to temporarily mount the desired partition on, then mount it ("sudo mount -t ext3 /dev/{partition} {newdirectoryname}"), or something similar.

Alright, I am trying to do this, but having some difficulty.

I run "df" and get this:

Filesystem           1K-blocks      Used Available Use% Mounted on
tmpfs                   253796     15444    238352   7% /lib/modules/2.6.22-14-generic/volatile
tmpfs                   253796     15444    238352   7% /lib/modules/2.6.22-14-generic/volatile
varrun                  253796        92    253704   1% /var/run
varlock                 253796         0    253796   0% /var/lock
udev                    253796        92    253704   1% /dev
devshm                  253796         0    253796   0% /dev/shm
tmpfs                   253796        20    253776   1% /tmp
/dev/sdb5            156242112 102154112  54088000  66% /media/disk

The last line there (/dev/sdb5) is where i will be moving all my files.
So,

sudo mount -t ext3 /{**what do i put here?**} /media/disk/restore

I've tried putting a few of those in, but it says "so and so is not a block device"

---

### Post by chadeldridge on 2008-02-17
> **chadeldridge said:**
> Thank you a ton this worked perfectly on the Dell XPS M1710.  Finally suspend is working.

Spoke too damn soon ... works to suspend and resume, but after about 2 seconds I have no keyboard.  Anyone have a similar issue or the fix?

EDIT:  Keyboard fix in previous posts did resolve the issue.  Thanks everyone.

---

### Post by Brad811 on 2008-02-17
> **Brad811 said:**
> Alright, I am trying to do this, but having some difficulty.

I run "df" and get this:

Filesystem           1K-blocks      Used Available Use% Mounted on
tmpfs                   253796     15444    238352   7% /lib/modules/2.6.22-14-generic/volatile
tmpfs                   253796     15444    238352   7% /lib/modules/2.6.22-14-generic/volatile
varrun                  253796        92    253704   1% /var/run
varlock                 253796         0    253796   0% /var/lock
udev                    253796        92    253704   1% /dev
devshm                  253796         0    253796   0% /dev/shm
tmpfs                   253796        20    253776   1% /tmp
/dev/sdb5            156242112 102154112  54088000  66% /media/disk

The last line there (/dev/sdb5) is where i will be moving all my files.
So,

sudo mount -t ext3 /{**what do i put here?**} /media/disk/restore

I've tried putting a few of those in, but it says "so and so is not a block device"

I have also gotten this error:

mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       (aren't you trying to mount an extended partition,
       instead of some logical partition inside?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

This is a lot of trouble for hibernating my computer...

I can see my hard drive in "Computer" but it won't seem to mount or open

---

### Post by Brad811 on 2008-02-18
Well, nevermind. My computer will no longer even boot from the live CD.

---

### Post by vahnx on 2008-02-19
Booting from the live CD (DVD) on my Dell Inspiron 1501 AMD Sempron 3500+ 1.8ghz ATI Radeon X1150 1.5GB RAM and Suspend works! Boot onto the partition (/dev/sda4) and screen goes black, and I tried billions of combo's. I know on the live dvd 'fglrxinfo' says it's not installed and desktoip effects don't work. That probably has something to do with it.

---

### Post by Xavier_To on 2008-02-20
Just a question like that... Is it just a Ubuntu-family issue or do other Debian-based and Gentoo-based, etc distros suffer from the same issue ? If Ubuntu is not alone in this issue, maybe some other distro's forum has the answer...

---

### Post by sofamensch on 2008-02-22
I don't wan't to open another thread, but i do not own a Dell :-)

I use a MSI Mainboard (G31 Chipset with onboard Intel GMA 3100). The Bios is set to StandbyMode S3 (i prefer that one) and additionally i told it to "Repost VGA on Resume" but still getting no picture after restarting from Standby.

---

### Post by unxplained on 2008-02-23
I've got a Dell Vostro 1000.

Did a clean install of 7.10 (dual boot with xp), enabled restricted driver for radeon xpress 1150 (Desktop effects not working though). Both suspend to RAM and hibernate are NOT working.

---

### Post by tobydeemer on 2008-02-25
Gateway mx6428 laptop, 7.10 clean install dual boot with XP, suspend and hybernate both broken.

---

### Post by sadeghi on 2008-02-26
Hi

Dell Inspiron 640m
ubuntu 7.10
Standby works fine.
Hibernate fails, just logout and displays the password screen. I tried many solutions but I could not enalbe Hibernation.

Thanks

---

### Post by veniatregnum on 2008-02-26
An old Dell Inspiron 5100 running Xubuntu 7.10

Suspend works great,
Hibernate initiates fine - but won't resume - starts new session with my swap removed which I then need to manually reinstate.

---

### Post by pormogo on 2008-02-27
Dell M1330n - When returning from suspend the Network Manager is taking up 100% CPU utilization and is not responding to my requests. It seems that the ipw3945 module is locked up or something like that. Loading the iwl3945 module is worse as it won't even detect wireless networks when returning from a hibernate or standby. with the ipw3945 module restoring from hibernate seems to work fine. So it looks like suspend is just off limits for me right now (unless before suspending I turn the wireless card off via swtich on the computer). Kinda lame seeing as cannocial says *Intel® 3945 802.11a/g Mini-card* is among the supported peripherals for this particular hardware.

---

### Post by hazelnutz18 on 2008-02-27
I switched over to Ubuntu from Windows in October of 07 and was able to fix all issues quickly except for suspend - I tried a bunch of different things that were suggested and nothing worked. My computer would go on suspend no problem but when it would resume I would get a totally blank screen. I just got it to work and I hope it helps you guys out.

This is where I found it - it has a lot of other useful tips as well.
[http://wiki.eeeuser.com/ubuntu](http://wiki.eeeuser.com/ubuntu)      - about 80% of the way down...

You need to edit the following file as super user:
/etc/default/acpi-support

Change the following line from true to false:
# Should we save and restore state using the VESA BIOS Extensions?
SAVE_VBE_STATE=false

Thats all I did and suspend works perfectly for me!

HP L2000
AMD Turion64 ML-37
1GB RAM
ATI Radeon Xpress 200M

---

### Post by Frankly Francois on 2008-02-28
Hey, that's great you got it to work, hazelnutz18.

Unfortunately, the same didn't work me. I still get the same black screen with blinking underscore. Everything seems to come on, just not the screen.

Would it make a difference if I didn't restart after editing that file? Also, I'm using an old desktop~ Compaq D510.

---

### Post by hazelnutz18 on 2008-03-01
You shouldn't need to restart...

Are you having problems performing the suspend or does your computer suspend no problem and have issues on the resume?

Whats your graphics card and processor?

---

### Post by selda on 2008-03-02
> **hazelnutz18 said:**
> 
This is where I found it - it has a lot of other useful tips as well.
[http://wiki.eeeuser.com/ubuntu](http://wiki.eeeuser.com/ubuntu)      - about 80% of the way down...

You need to edit the following file as super user:
/etc/default/acpi-support

Change the following line from true to false:
# Should we save and restore state using the VESA BIOS Extensions?
SAVE_VBE_STATE=false

Thats all I did and suspend works perfectly for me!


There's some extra help for nvida cards - [https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend](https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend)

These few steps solved mine probles (Dell XPS 1210)

---

### Post by selda on 2008-03-02
> **pormogo said:**
> Dell M1330n - When returning from suspend the Network Manager is taking up 100% CPU utilization and is not responding to my requests. It seems that the ipw3945 module is locked up or something like that. Loading the iwl3945 module is worse as it won't even detect wireless networks when returning from a hibernate or standby. with the ipw3945 module restoring from hibernate seems to work fine. So it looks like suspend is just off limits for me right now (unless before suspending I turn the wireless card off via swtich on the computer). Kinda lame seeing as cannocial says *Intel® 3945 802.11a/g Mini-card* is among the supported peripherals for this particular hardware.

I had similar problems with Network Manager. I have replaced it with wicd ([http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)) and all the issues were solved. It may help you too, since my dell xps 1210 has the same wireless card.

---

### Post by Frankly Francois on 2008-03-02
> **hazelnutz18 said:**
> You shouldn't need to restart...

Are you having problems performing the suspend or does your computer suspend no problem and have issues on the resume?

Whats your graphics card and processor?
Right now I'm using nVidia GeForce2 MX200, PCI 64MB card and Pentium 4 2.4 ghz. 

Would I have better luck if I upgraded the graphics card? I do have an ATI 9550 card, but I'd have to upgrade my PSU before I used it.

Yes, the system has no problems going into suspend or hibernate. The problem is when I try to resume it. As far as I can tell, everything but the display comes back to life. I always get that black screen with the blinking underscore. So I'm forced to just unplug the computer. It's a bummer because I like to use suspend.

---

### Post by hendrikdegraaf on 2008-03-07
Hi,
Does anyone know if it is possible to get a Dell XPS M1330 laptop to hibernate?

Suspend works fine, but the system doen't want to to wake up after hybernate.

Thanks,
Hendrik

---

### Post by pormogo on 2008-03-07
My m1330n hibernates about 80% of the time however the other 20% of the time it crashes to a blank screen and I have to reboot with the power button.

---

### Post by newagelink on 2008-03-07
[COLOR="Indigo"]I have a Gateway laptop; the model is linked in my signature.

I upgraded from 7.04 to 7.10 via the Update Manager. Now when I try to hibernate it acts like it's going into it, then I get a black screen with grayscale text reporting USB error messages, and then it shuts off (or I get frustrated and hold down the power button until it shuts off.)[/COLOR]

---

### Post by hendrikdegraaf on 2008-03-08
> **pormogo said:**
> My m1330n hibernates about 80% of the time however the other 20% of the time it crashes to a blank screen and I have to reboot with the power button.

Mine is always doing that: the only thing that helps is a hard reboot. Is there anything that can be done, apart from waiting for the new kernel version that hopefully fixes this issue?

Any tips would be highly appreciated!

Kind regards,

Hendrik

---

### Post by milky2313 on 2008-03-11
Dell Latitude D610 Pentium M with ATI Mobility Radeon X300.

With a fresh install of Gutsy, everything is stable (including standby) under the open source ati drivers provided by linux.

Tried installing fglrx with the restricted drivers manager and the video card worked fine but X Server will not load, so there are no desktop effects.  

I uninstalled the driver and tried again using Envy.  Now X server and desktop effects work fine.  There are a few glitches with the video playback, and the computer consistenly crashes when going into standby. I'm still trying to decide if i want to keep fglrx or just go back to the linux open source ati drivers for more stability.

---

### Post by ekkof on 2008-03-11
I work on a HP6720s on gutsy (7.10).

Every things worked... exept for the suspend & hibernate... I can't get it to work.
With both the hibernate and suspend the laptop freezes on a black screen :(

---

### Post by selda on 2008-03-11
> **ekkof said:**
> I work on a HP6720s on gutsy (7.10).

Every things worked... exept for the suspend & hibernate... I can't get it to work.
With both the hibernate and suspend the laptop freezes on a black screen :(

If you have nvdia card in your laptop, try this guide - [https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend](https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend)

---

### Post by 42Wired on 2008-03-11
Toshiba Satelite R15-S829 (laptop)
I closed the lid to put it into standby, and when I came back to it, I opened it, and it went through GRUB fine. I thought the screen was blank, but it turns out that the backlight for my screen wasn't on, and wouldn't turn on no matter what I tried. It was fine after a restart.

---

### Post by cabez0n on 2008-03-11
I have an Acer Travelmate 5510 and Hibernate works almost perfect. 
The only problem is that the wifi interface doesnt work after coming back from hibernation (ndiswrapper and the windows firmware), so I need to ifdown wlan0; ifup wlan0
I was wondering if there is a mechanism to call some script when coming back from hibernation ?

thanks

---

### Post by 42Wired on 2008-03-11
Toshiba Satellite R15-S829

What happens with my computer in hibernate mode is inconsistent; I just tried to bring it out of hibernate mode, and after GRUB, the screen remained black, except for the mouse cursor.
I left Firefox open when I went into hibernate, and when it tried to come back, the mouse cursor changed when I hovered over text or a link, still.

Would 915resolution fix these problems? I'm reluctant to install it because other than standby and hibernate, I have only one or two occasional graphics problems, both of which are quite bearable.

---

### Post by hendrikdegraaf on 2008-03-12
> **selda said:**
> If you have nvdia card in your laptop, try this guide - [https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend](https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend)

Is there also a guide for hybernate settings? My suspend works fine!

---

### Post by rhyguy on 2008-03-12
I have a dell pc with a new mobo,

should i choose s1 sleep, s3 sleep or s1&s3 sleep?

---

### Post by kevin79 on 2008-03-12
I just upgrade to Hardy Alpha 6 X64 bit. Suspend and Hibernate worked before the upgrade but now it just reboots when I try to use it. This is on a Latitude D820 with a nVidia Quadro card using driver 169.12

---

### Post by djbon2112 on 2008-03-12
I figure I'll add to this too.

Dell Vostro 1700, in either sleep or hibernate
Clean install of 7.10.

---

### Post by john5 on 2008-03-12
Dell D400.  Clean install of Gutsy.

After installing pm-utils, suspend works, either by pm-suspend or the gui option.  Hibernate dosn't turn the computer off, and it just return.

---

### Post by JohnHood on 2008-03-13
I have a Dell Dimension (Intel) with ATI Radeon 1300 graphics card running "Gutsy Gibbon". Like others I can't get the machine to suspend/hibernate. Please ask if you want more details of the hardware.

---

### Post by Canux08 on 2008-03-13
Update:

Dell D610, Standby now works. I reinstalled the ATI video card drivers for my X300 Radeon mobility card. As part of the reinstall, the restricted FGLRX driver is installed, but not in use. 

I'm still trying to get hibernate to work, but I suspect that issue is related to a problem I'm having with my swap partition.

---

### Post by cos4 on 2008-03-13
Dell Latitude D531, clean install(Kubuntu), can't recover from hibernate or suspend(like a system freeze).

---

### Post by raywjohnson on 2008-03-13
> **selda said:**
> If you have nvdia card in your laptop, try this guide - [https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend](https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend)

> **hendrikdegraaf said:**
> Is there also a guide for hybernate settings? My suspend works fine!

Thank you both! I have a system that I put together and installed Gutsy 7.10. The suspend and/or hibernate function would turn off the monitor and nothing (mouse, keyboard, yelling) would restore it (accept turning the computer off and on). 

I made the changes recommended (from the link you provided: found via hendrikdegraaf quoting selda ) and now it works as expected. (I did not make the "compiz" change).

I previously change to the nVidia drivers via: apt-get install nvidia-glx nvidia-kernel-source

And changed my xorg.conf according to this info: [http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8174/README/32bit_html/chapter-03-section-02.html](http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8174/README/32bit_html/chapter-03-section-02.html)

For ref my system is:
AMD Athlon(tm) 64 X2 Dual Core Processor 5200+
DELL E228WFP (flat panel monitor, using digital input) @ 1680x1050
nVidia GeForce 6150 
Note: this is NOT a laptop!


--RayJ :mrgreen: :biggrin:

---

### Post by DavidFourer on 2008-03-15
Login problem.  If I make a password typo at login after suspend, it hangs and I have to reboot.  Alt-Ctrl-Backspace does not help.  Maybe there is a simple fix.  I don't need the login security--can I disable it?

Otherwise, suspend to ram works.  Dell inspiron 6000 with intell 9000 graphics, Broadband 1370 wireless.   Once in a while Firefox browser hangs on resume, but I can restart Gnome without reboot.  Not sure if it's firefox or the system that's crashing.

---

### Post by 4rk3typ3 on 2008-03-15
Latitude 630
Occassionally comes out of standby or hibernate with the help of wishful thinking and baby tears. For the most part, however, it doesn't seem to do very well with either. I just turn off the display now to conserve powe, but luckily this system doesn't seem to be much of a power hog (can run a solid 3+ hours no problem).

---

### Post by sdennie on 2008-03-15
On a Dell XPS m1330 (nvidia 8400M GS model), suspend/resume works just fine on 7.10 with the following changes:

A script from Dell that modifies /etc/default/acpi-support:
[http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/8400M_Suspend_Hibernate-Failure](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/8400M_Suspend_Hibernate-Failure)

Using iwl3945 driver instead of ipw3945.  The first link is from Dell that tells how to switch to the driver, the second is from Ubuntu that talks about making the driver work properly with suspend/resume.
[http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/ipw3945_Wireless_Network_Module_Issues](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/ipw3945_Wireless_Network_Module_Issues)
[https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/130457/comments/3](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/130457/comments/3)

With those two changes, I've had no problems with suspend/resume and I use the functionality several times a day.  Actually, that's not completely true.  Sometimes the machine comes back from suspend and all I see is the error message from the webcam driver when it gets reloaded.  I'm not sure what causes it to stick on that screen but, a simple Ctl-Alt-F1 and then Ctl-Alt-F7 brings me back to the screensaver login prompt.

---

### Post by napzilla on 2008-03-17
Dell Inspiron 6400
Radeon Mobility X1400

Suspend/Hibernate didn't work with a clean install of Edgy, an upgrade to Fiesty, a clean install of Fiesty or an upgrade to Gutsy.

I gave up on it a while ago, but it's getting on my nerves again.

I installed the latest X1400 drivers from ATI to fix a different video issue. This didn't do a thing to resolve the suspend/hibernate problem.

---

### Post by balayyoub on 2008-03-18
Hi everybody 
I used to have a problem with hibernate and suspend options most of the time.
It kept like that for maybe 2 weeks, I thought the problem was with the wireless network driver, so I changed using ndiswrapper, Its been 2 days and every thing is going so smoothly, and i used to have a problem with wireless that it always drops down, but no more of that.
Dell Inspiron E1405

---

### Post by Strelock on 2008-03-20
> **Canux08 said:**
> Update:

Dell D610, Standby now works. I reinstalled the ATI video card drivers for my X300 Radeon mobility card. As part of the reinstall, the restricted FGLRX driver is installed, but not in use. 
.

I also have the latest drivers but it doesn't suspend. Have you done anything special?

Could you please, post the /etc/default/acpi-support?

---

### Post by gcraenen on 2008-03-23
JKoyle, Thanks for putting this together. It helped me with my "blank screen" problems after standy on my Dell Latitude D820. Very important to me that it works, so thanks again.

Dell 820 using nvidia-new - Suspend/Hibernate both work

Modify /etc/default/acpi-support:
SAVE_VBE_STATE=false
POST_VIDEO=false

Append to /etc/modprobe.d/blacklist:
blacklist intel_agp
blacklist agpgart

Modify xorg.conf Device Section to include:
Option "NvAGP" "1"

Here's the relevant section from my xorg.conf:
Section "Device"
Identifier "Videocard0"
Driver "nvidia"
Option "NvAGP" "1"
Option "XAANoOffscreenPixmaps" "true"
VendorName "NVIDIA Corporation"
BoardName "Quadro NVS 110M"
EndSection


That's it. I can validate that it was not working prior to the above changes.

John

---

### Post by charliehubuntu on 2008-03-24
Vostro 1700 Nvidia Gutsy

Hibernates but won't come out of hibernation.

I pretty much don't count on hibernation working on any machine under any operating system.

---

### Post by Drittponken on 2008-03-24
Well my doens't work to either hibernate or suspent. Gotta check into this.


HP compaq nc6000 laptop.
ATI Mobile Radeon 9600


Clean install

---

### Post by 42Wired on 2008-04-04
After coming back from Hibernate, no wireless networks will be detected. I haven't tried fixing it, but restarting the computer solves the problem.

HP dv2700
Intel Core 2 Duo 2.5 Ghz (T9300)
4.0 GB RAM
Ubuntu 7.10 (64-bit)

OK, it only does it sometimes, now.

---

### Post by Redrazor39 on 2008-04-04
I own a Sony VAIO computer; however, I can still post my problems.

VAIO VGN-SZ430N

Will not fully enter suspend mode, hibernate does not restore session

---

### Post by ghstzr0 on 2008-04-06
Dell Inspiron 1420n (Ubuntu Version) w/ Intel X3100.

Suspend and hibernate work, however 50% of the time, the keyboard and touchpad are completely unresponsive when resuming.  If I plug in a USB keyboard or mouse, I can resume use of my notebook (obviously this is not practical).  I have read about others with this problem, but never found a solution.

BTW, even upgrading to the latest Hardy Beta doesn't eliminate this problem!  That's so irritating!

---

### Post by cos4 on 2008-04-08
Has anybody got a ATI card and a working hibernate/suspend mode? The solutions I found are for Nvidia(yeah I know its better). I've got a Dell Latitude D531 with the ATI card and the notebook won't awake from suspend or hibernate. If anyone knows a way how to fix this plz let me know.

---

### Post by L. Cranston on 2008-04-08
IBM Thinkpad T-40
most current Gutsy install with all packages.
Seemed to have the hibernate issue as well
unresponsive keyboard from hibernate (intermittent at first)
but resolved to be a hardware issue (keyboard short).

seem to now have the network detection issue as well.
glad to see the issue is known however....

---

### Post by feveryear on 2008-04-08
I'm not sure who all knows of this, but I found a link to an Ubuntu Wiki that shows the Suspend workaround. I haven't tried the Hibernate yet, but apparently it fixes both. 

[https://wiki.ubuntu.com/InstallingUbuntuOnADellXPSM1530](https://wiki.ubuntu.com/InstallingUbuntuOnADellXPSM1530)

If you scroll down that page, it shows plenty of issues that can be fixed. Down towards the bottom is a Suspend Fix. Basically, you use Envy for nVidia cards (at least I know this works with nVidia, because that is what I have) and then run the fix commands in the terminal. Once you restart, it should work. It works for me just fine. One little thing, so you don't get upset right away, for about 5 or 6 seconds after you hear the hard drive and fan cut out, the power LED and HD activity LED are still flashing. They will eventually go off and the Power LED will fade in and out like normal. I'm still trying to find a work around to the touchpad going nuts when coming out of Suspend, but I thought this may be valuable.

Credit goes to whoever put up that site. I'm just the messenger!

EDIT: For what it may be worth, I am running Ubuntu with the newest nVidia card drivers, but I have NO desktop effects activated. I'm not sure if that would make a difference or not, but just an FYI.

---

### Post by dmk0210 on 2008-04-10
Dell Inspiron E1505 w/ ATI Radeon X1300. Had Vista initially, now wiped clean and Ubuntu Gutsy installed.  Has latest fglrx driver (catalyst 8.3), downloaded from ATI and compiled. Desktop effects mostly work and I don't have the Firefox scroll bug, but Compiz flickers video in a window, so I disabled desktop effects.

 Hibernate and suspend do not work. However, I haven't "gotten under the hood" and seriously atemped any fixes for it yet.

---

### Post by aidave on 2008-04-10
Dell 1420n preinstalled with Ubuntu 7.10.

What a joke.  Suspend/resume didnt even work out of the box.  Dell is selling broken systems! 

Had to upgrade to Hardy Beta, install Envy, then finally get a working suspend/resume (although only if you type your password on a white screen).  Wireless/USB does not always recover and not all hardware features work right with Hardy yet.  This is totally unacceptable.  How is a new user supposed to figure this out?

For a company like Dell, they should not be selling faulty laptops.  If it is Ubuntus fault, or Nvidias fault, or whoevers fault, who cares!!!  Dell has the leverage to get a fix in, dont they?  Just demand Nvidia/Ubuntu fix it or something.  What a joke.

Anyways that is my experience: frustration.

---

### Post by jellystones on 2008-04-13
Hi,

I have a dell that 20% of the time refuses to resume from standby mode.

But today I think I found a temporary solution:

If you try to resume from sleep mode, and you get a blank screen, try playing with your screen brightness. For me I press Fn+Up or Down.

This seems to work as all of a sudden, my computer comes to life!

---

### Post by TheFuzz4 on 2008-04-13
Try Hardy it fixed all of my suspend/resume issues.

---

### Post by littlebattler on 2008-04-16
According to [http://linux.dell.com/wiki/index.php/Ubuntu_7.10](http://linux.dell.com/wiki/index.php/Ubuntu_7.10) 1525 with the new bios will not wake up from suspend:
15	Resume from Suspend Broken with newer BIOS 	1525n

i just bought one and it hasn't arrived yet.. but i am guessing it will probably come with the latest bios. is there a workaround to getting suspend to work? any way to downgrade the bios version?

---

### Post by AaronMT on 2008-04-16
Hi all,


I am the original thread starter. I haven't used Ubuntu in a few months but returned today to test out Hardy Heron Beta and to my surprise, suspend is functional. I am still using the Dell Inspiron 1501 and everything is functional. I suggest those using 7.10, try out Hardy beta.

Cheers :)

- AaronMT

---

### Post by lynchman on 2008-04-18
> **ghstzr0 said:**
> 
Suspend and hibernate work, however 50% of the time, the keyboard and touchpad are completely unresponsive when resuming.  If I plug in a USB keyboard or mouse, I can resume use of my notebook (obviously this is not practical).  I have read about others with this problem, but never found a solution.


Same here.  I think for me it works more that 50% of the time.  I almost always use a wireless mouse, so the mouse is usually alive, but I won't have any keyboard input and will need to reboot.

I think I'll try Hardy this weekend, but it sounds like that doesn't help too much either.

Anyone with a solution?

---

### Post by Pitabread112 on 2008-04-18
> **AaronMT said:**
> Hi all,


I am the original thread starter. I haven't used Ubuntu in a few months but returned today to test out Hardy Heron Beta and to my surprise, suspend is functional. I am still using the Dell Inspiron 1501 and everything is functional. I suggest those using 7.10, try out Hardy beta.

Cheers :)

- AaronMT

It's working for you? It worked for me in the beginning, but after an update or two ago, it has not worked. The screen says black when I open the lid back up on my Hp Pavilion dv6000 special edition. I'd try and press the suspend key but there is none! Ive tried pressing the power button since its supposed to initiate things of that sort. No luck. my screen is stuck black and I have to force a restart. >.<  This last time I could see my cursor, but that is all. Still the black screen. Uber frustrating. Anyone have any help?

Hp Pavilion DV6000 Special Edition
Core 2 duo, nvidia graphics
Hardy Heron with Compiz-fusion.

---

### Post by trippinnik on 2008-04-19
Still not working for me either.  I have yet to get suspend to work on my IBM Thinkpad X22.  it used to work in Fiesty, but since Gutsy has been broken unless I set the graphics driver to vesa which means I can't watch video.  I had been running Debian 4.0 but just tried Hardy again today.

---

### Post by alphacrux on 2008-04-23
hey guys after crawling around on the launchpad bug site I figured out that the reason hibernate/suspend is better on hardy is that they are using a whole different program for it. Starting in hardy they'll be using the pm-hibernate and pm-suspend commands. If you want to get the same functionality just download pm-utils from aptitude or synaptic. Then just issue a "sudo pm-hibernate". If you want to setup the hibernate button to use this utility you will have to edit: /usr/lib/hal/scripts/linux/hal-system-power-hibernate-linux. However if you look at this code segment in that file: > #Other distros just need to have *any* tools installed
else
        if [ -x "/usr/sbin/pm-hibernate" ] ; then
                /usr/sbin/pm-hibernate $QUIRKS
                RET=$?
        elif [ -x "/usr/bin/powersave" ] ; then
                $POWERSAVED_SUSPEND2DISK
                RET=$?
        elif [ -x "/etc/acpi/hibernate.sh" ] ; then
                # acpi-support installed
                /etc/acpi/hibernate.sh force
                RET=$?
        elif [ -x "/usr/sbin/s2disk" ] ; then
                # uswsusp tools installed
                /usr/sbin/s2disk
                RET=$?
        elif [ -x "/usr/sbin/pmi" ] ; then
                /usr/sbin/pmi action hibernate force
                RET=$? it seems that if pm-utils is merely installed that it will use it before any of the other hibernating utilities. Doing this prevented my network from going down everytime I hibernate and also prevented my screen from locking from hibernate as well. Hope this helps yall out :)

---

### Post by trippinnik on 2008-04-23
to bad i still have the same problem with Hardy.  I'm running OpenSuse 11 and that's working though.

---

### Post by bucketoftruth on 2008-04-29
Dell XPS M1210 started at 7.04, then upgraded to 7.10, now at 8.04.  Hibernate and Suspend both resume fine EXCEPT now I have no display.  The screen is completely black, but I can see that there is IO activity.  I'm using the 915resolution package.  The pertinent parts of lspci:

```
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
```

Is there anything else I can provide that might help fix this?

---

### Post by RichTJ99 on 2008-04-29
> **bucketoftruth said:**
> Is there anything else I can provide that might help fix this?

Hi,

I have a XPS M1210 (with 7.10) and this fixed the issue in 7.10 for me (I didnt make the upgrade yet).  Please try this & report back.

This code was posted from someone else in this thread (credit doesnt go to me):

```
Modify /etc/default/acpi-support:

SAVE_VBE_STATE=false

POST_VIDEO=false



Append to /etc/modprobe.d/blacklist:

blacklist intel_agp

blacklist agpgart



Modify /etc/X11/xorg.conf Device Section to include:

Option "NvAGP" "1"
```

---

### Post by bucketoftruth on 2008-04-30
I made the changes you described above and it worked.  Now my desktop effects ala compiz are gone and I can't re-enable it.  I removed the changes and suspend/hibernate still work but still no compiz.

EDIT: Ok, after a few more reboots everything is back to as it was before the changes.  Is there a way to make these changes and reap the benefits of suspend/hibernate without loosing my desktop effects?

---

### Post by tombeharrell on 2008-05-01
Machine: Dell XPS Gen2, 2GB RAM, 100GB disk, Nvidia GeForce Go 6800 Ultra 256MB 

Suspend and Hibernate work perfectly in 8.04 for me, EXCEPT that since installing the last few updates, hibernate doesn't actually turn the machine off. After waiting a few seconds I have to hold down the power button.

Apart from that it's perfect, and I can close and open the lid to suspend and resume, no problems with wi-fi, sound or USB devices.

---

### Post by paour on 2008-05-02
> **noodles12 said:**
> dell 700m integrated graphics gutsy clean install. 

this combined with the Post_video=FALSE got my suspend working perfectly!!! thanks. 

Hibernate doesn't work and just locks the screen and i can just sign back in, but i don't really use hibernate. 

I'm not even sure if the Post_video is needed but i had it changed to that from previous tries. Will test out soon.

In Hardy Heron, the post_video change seems to be enough, I can now suspend and hibernate without any problem on a Latitude D400.

In /etc/default/acpi-support, set POST_VIDEO=FALSE.

Edit: even though the above change seemed to be enough at first, the laptop would sometimes lock up when hibernating or going to standby, until I applied the other change suggested in the thread:

In /boot/grub/menu.lst, add "acpi=force noapm pci=irqmask=0x0e98" to the line starting with "# kopt=", then run "sudo update-grub".

---

### Post by jdeslip on 2008-05-04
> **aidave said:**
> Dell 1420n preinstalled with Ubuntu 7.10.

What a joke.  Suspend/resume didnt even work out of the box.  Dell is selling broken systems! 

Had to upgrade to Hardy Beta, install Envy, then finally get a working suspend/resume (although only if you type your password on a white screen).  Wireless/USB does not always recover and not all hardware features work right with Hardy yet.  This is totally unacceptable.  How is a new user supposed to figure this out?

For a company like Dell, they should not be selling faulty laptops.  If it is Ubuntus fault, or Nvidias fault, or whoevers fault, who cares!!!  Dell has the leverage to get a fix in, dont they?  Just demand Nvidia/Ubuntu fix it or something.  What a joke.

Anyways that is my experience: frustration.

Hi aidave,

I have a 1420 with nvidia that I just upgraded to hardy.  Suspend seems to work ok except for the white screen at which you have to type your password.  Did you ever find a fix for this?  I am using the hardy 169.12 nvidia driver, does 173.08 fix it by any chance?

---

### Post by ubunthu on 2008-05-09
> **neptho said:**
> This machine is a bear, I'm afraid.  The fix is to add "fglrx" (and ipw3945 if you have an intel wireless controller) to MODULES_WHITELIST in /etc/acpi/acpi-support.

I was looking to solve the network restart problem after resume from hibernate on an amd64 / ati x1250 system / x/ubuntu 8.04. It worked for me on both desktops. Thank you.

---

### Post by TracyO on 2008-05-12
> **littlebattler said:**
> According to [http://linux.dell.com/wiki/index.php/Ubuntu_7.10](http://linux.dell.com/wiki/index.php/Ubuntu_7.10) 1525 with the new bios will not wake up from suspend:
15	Resume from Suspend Broken with newer BIOS 	1525n

i just bought one and it hasn't arrived yet.. but i am guessing it will probably come with the latest bios. is there a workaround to getting suspend to work? any way to downgrade the bios version?

 I've had my 1525n for about a week.  I'm waiting to update to Hardy until Firefox 3 comes out, and everything has worked well with my Dell/Ubuntu out of the box, but it does not suspend or hibernate at all.  It sounds like it might work when I go to Hardy?  Otherwise, has anyone found a way around this? Thanks.

---

### Post by noisygecko on 2008-05-13
> **paour said:**
> In Hardy Heron, the post_video change seems to be enough, I can now suspend and hibernate without any problem on a Latitude D400.

In /etc/default/acpi-support, set POST_VIDEO=FALSE.

Edit: even though the above change seemed to be enough at first, the laptop would sometimes lock up when hibernating or going to standby, until I applied the other change suggested in the thread:

In /boot/grub/menu.lst, add "acpi=force noapm pci=irqmask=0x0e98" to the line starting with "# kopt=", then run "sudo update-grub".

I just applied both of these changes to my 8.04 Hardy install on a Dell Inspiron 710m and finally the hibernate function works.

But it doesn't seem to have fixed a problem where my system never shuts off sporadically.  Does anyone know what is up with that?

-Sim

---

### Post by sistoviejo on 2008-05-15
Is this only for Dell laptops? 
I own an HP tx1215nr. 
Suspend and hibernate also doesn't work on my laptop. 
Where should I post my concerns?

> **AaronMT said:**
> 
**Problem**

You own a Dell Desktop or Laptop. In my case I own a Dell Inspiron 1501. You installed Ubuntu 7.10 recently, today or last week on a clean install or an upgrade and now your machine is incapable of entering or returning from standby/hibernate.

If so, please post the following information.

**Dell Model (Laptop/Hibernate?)**
**Upgrade or Clean Install**

Please vote in Ubuntu Brainstorm to promote this idea:
[[IMG]http://brainstorm.ubuntu.com/idea/94/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/94/)

---

### Post by noisygecko on 2008-05-15
> **sistoviejo said:**
> Is this only for Dell laptops? 
I own an HP tx1215nr. 
Suspend and hibernate also doesn't work on my laptop. 
Where should I post my concerns?


I would probably try the things mentioned here. They don't actually have anything to do with Dell -- no Dell specific drivers or anything.

Also, just want to mention that I made sure that CPU scaling is still running, as I wasn't sure that was affected by the ACPI setting changes. My system goes to 600Mhz when idle, and 1800Mhz when pegged.

---

### Post by sistoviejo on 2008-05-16
> **noisygecko said:**
> I would probably try the things mentioned here. They don't actually have anything to do with Dell -- no Dell specific drivers or anything.


Is there a list of things to try or should I read through all 35 pages?
:confused:

---

### Post by noisygecko on 2008-05-16
I guess I was thinking in terms of applying just the things that I did (noisygecko).  I just did these 2 things and everything seems to be working for me:

> **paour said:**
> In Hardy Heron, the post_video change seems to be enough, I can now suspend and hibernate without any problem on a Latitude D400.

In /etc/default/acpi-support, set POST_VIDEO=FALSE.

Edit: even though the above change seemed to be enough at first, the laptop would sometimes lock up when hibernating or going to standby, until I applied the other change suggested in the thread:

In /boot/grub/menu.lst, add "acpi=force noapm pci=irqmask=0x0e98" to the line starting with "# kopt=", then run "sudo update-grub".

---

### Post by aidave on 2008-05-25
> **jdeslip said:**
> Hi aidave,

I have a 1420 with nvidia that I just upgraded to hardy.  Suspend seems to work ok except for the white screen at which you have to type your password.  Did you ever find a fix for this?  I am using the hardy 169.12 nvidia driver, does 173.08 fix it by any chance?

Hi, there is no fix that I am aware of, although I am not currently using 173.08.  I was using the latest NVIDIA earlier though, until I reinstalled my OS.  A white screen is silly, but at least it still works.

---

### Post by DavidFourer on 2008-05-25
> **sistoviejo said:**
> Is this only for Dell laptops? 
Where should I post my concerns?


Is this now the thread for Dell or laptop suspend problems?
I want to get back into the active thread, now that I have 8.04 Hardy.

Dell inspiron 6000, intel graphics. Sleep yes but resume works only sometimes. Hibernate has not worked since about 6.10. Sometimes no display and sometimes I get resume but message says "you computer failed to suspend", even though it seemed OK.  I'm using older kernel for now.

---

### Post by stevieP on 2008-06-07
> please Post The Following Information.

Dell Model (laptop/hibernate?)
Upgrade Or Clean Install

I have a Dell XPS M1530. 
Running Ubuntu 7.10 - Gutsy Gibbon
Clean install. 

My computer will not enter hibernation when I close it. And when I manually enter hibernnation through System->Quit->Hibernate, itt will not come out of hibernation. 

What I've tried:

Following the advice on this page
[https://wiki.ubuntu.com/InstallingUbuntuOnADellXPSM1530#head-ba49c7c103bc45b5d01af3cd620368924e1a87cf](https://wiki.ubuntu.com/InstallingUbuntuOnADellXPSM1530#head-ba49c7c103bc45b5d01af3cd620368924e1a87cf)
I've downloaded Envy to install the latest closed source Nvidia drivers. This is because thhe workaround does not apparently work with the native open-source 2D 'nv' driver, as described here:
[http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/8400M_Suspend_Hibernate-Failure](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/8400M_Suspend_Hibernate-Failure)

After downloading and running envy, I could not see anythinng inn the windows or xterminals onn my computer! I had to use envy to uninstall the new nVidia graphics driver, annd I was back to square one. 

I should also mentionn that the keyboard on my new Dell has several sticky keys that has me backspaccing every few words to correct double-typed letters.

---

### Post by edunam on 2008-06-11
Dell XPS M1530
Clean Install

---

