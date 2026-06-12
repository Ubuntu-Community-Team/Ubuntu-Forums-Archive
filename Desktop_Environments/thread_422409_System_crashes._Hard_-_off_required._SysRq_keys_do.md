---
title: "System crashes. Hard - off required. SysRq keys do not work"
date: 2007-04-25
forum: Desktop Environments
---

### Post by YetAnotherNoob on 2007-04-25
I decided to log a bug report because this is becoming unbearable.

The system crashes and fails to respond. On occasion caps-lock and scroll lock flash. But more recently nothing happens. Key strokes Alt+SysReq-S Alt+SysReq-U Alt+SysReq-B fail to have any affect.

This was a fresh install of Feisty 7.04, but is dual boot with Vista NTFS. (Vista has worked fine for several months).
I have a Dell Inspiron 9400
nVidia 7800 GO
I have disabled: bluetooth/wireless, usb wake on lan, memory card reader and firewire via the bios. But the problem still occurs.


Bug: [https://bugs.launchpad.net/ubuntu/+bug/109877]("https://bugs.launchpad.net/ubuntu/+bug/109877")
The problem happens frequently perhaps every 30-40 minutes sometimes more often sometimes an hour passes. The problem has become very frustrating because I do not see anything any problems in /var/logs/

I am not using desktop affects and I only use applications/addons available through the Add/Remove Programs Application.
I can provide more information.

---

### Post by gmc on 2007-04-25
Hi,

A couple of thoughts occur to me regarding your lockup problems. Originally I thought maybe bad memory, the obvious solution is to run the memory test offered when booting the cd/dvd. Now I'm sure this has been suggested before and it wouldn't hurt to try it and be sure that's not causing the problem.

However, you meantioned that lights on your keyboard sometimes flash by themselves, and that would indicate that there maybe a problem with your keyboard. I'm not sure if you are aware, but there is a microcontroller (8051 microcontroller). This controller is used in timing between the PC and the keyboard. Now if there is a problem with this controller, it can cause your PC to act erratically. I'd suggest replacing your keyboard and see if that helps any.

Regards
Gord

---

### Post by YetAnotherNoob on 2007-04-25
Thank you for your reply.  I have tried using the memory tests and they passed OK.  (In past I have used have also another memory test supplied by Dell which gave also gave the all clear).

On the flashing:
the capslock light does not happen everytime, maybe twice.  Ubuntu has crashed maybe 20 times all up.  And the lights only flashed after everything else had stopped. does not help

That probably but more information is better.

---

### Post by gmc on 2007-04-25
> **YetAnotherNoob said:**
> Thank you for your reply.  I have tried using the memory tests and they passed OK.  (In past I have used have also another memory test supplied by Dell which gave also gave the all clear).

On the flashing:
the capslock light does not happen everytime, maybe twice.  Ubuntu has crashed maybe 20 times all up.  And the lights only flashed after everything else had stopped. does not help

That probably but more information is better.

Aha! Ok now I understand. The flashing keyboard lights are after the crash. It's been a long time since I had a linux crash like that, I seem to recall that linux it's flashing them to report a kernel crash.

I'm intrigued with this problem.  Do these lockup's occur if you are using the live version, and I'm not sure if you said or not? Did you have these problems with 6.10 (installed and/or live)?

Regards
Gord

---

### Post by YetAnotherNoob on 2007-04-25
I have not installed 6.10 but maybe it is worth a try.  I have used the live version for a couple of hours without lockup. What would be different between the two?  Drivers?  I am only using the default vesa driver (was using nvidia drivers) butstill crashes.  I am kind of desperate so after searching the forums I have tried noacpi boot option:

[http://ubuntuforums.org/showthread.php?t=340390&highlight=noacpi+9400]("http://ubuntuforums.org/showthread.php?t=340390&highlight=noacpi+9400")

Now waiting to see if it crashes...

---

### Post by YetAnotherNoob on 2007-04-26
ACPI off but crashed again.  At first OK but once after some use 45mins...BOOM.  I have used 4 memory testing programs now.  None found any problems, which is supported by windows running OK (even under load).

I wonder if there are other ubuntu FF 7.04 users with **[COLOR="Red"]Dell Inspiron 9400[/COLOR]**?

Any tips or things you did to get things working?

Help would be much appreciated.

---

### Post by gmc on 2007-04-26
> **YetAnotherNoob said:**
> I have not installed 6.10 but maybe it is worth a try.  I have used the live version for a couple of hours without lockup. What would be different between the two?  Drivers?  I am only using the default vesa driver (was using nvidia drivers) butstill crashes.  I am kind of desperate so after searching the forums I have tried noacpi boot option:

[http://ubuntuforums.org/showthread.php?t=340390&highlight=noacpi+9400](http://ubuntuforums.org/showthread.php?t=340390&highlight=noacpi+9400)

Now waiting to see if it crashes...

The shortest distance to a solution is to work with known tools, so I'm just trying to eliminate options.  Diagnosing random lockups can be a real pain in the *ss.

So you have had the 7.04 live version lockup too then. If adding noacpi doesn't help, I'd recommend trying live 6.10 or even 6.06 (if you have either) and see if the problems persist. 

Regards
Gord

---

### Post by secret_squirrel on 2007-04-26
I'm seeing a similar problem on my IBM Thinkpad R50e laptop.

I've been running 6.10 for a few months without any problems - completely stable, even with Beryl running.

I upgraded to 7.04 last week with the online update and ever since I've been getting these hard crashes where the screen goes whacky, none of the keys work and nothing gets written to the error logs.  It seems to run for between 10 mins and an hour before crashing.

I've tried disabling Beryl and even booting from the old 6.10 kernel but same result (which is very curious in itself).

I'll run through the hardware checks, but the timing seems like too much of a coincidence.

---

### Post by gmc on 2007-04-26
Hi S.S.!

  So your system was upgraded from 6.10 rather than a fresh install. Have you tried some of the kernels from 6.10 (if they are still installed) to see if the problem is the feisty kernel? Also are you seeing flashing keyboard lights too?

Gord

---

### Post by skubisnack on 2007-04-26
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/109877](https://bugs.launchpad.net/ubuntu/+bug/109877) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I had a similar crash a little while ago.  I have a fresh install of Feisty (first ever install of Ubuntu), dual boot, wireless enabled on a Gateway 7320gz (m520) laptop.  

I got the flashing caps lock light, my mouse stopped working, no keyboard, and had to do a hard reboot.  I was playing Same Gnome with Firefox and Thunderbird open at the time of the crash.  My wireless was a little squirrelly on reboot, but is working fine now.  This is the only time this has happened.  I have had Feisty installed for a few days, but just got wireless working yesterday, and have had the comp on ever since until it just crashed.  This has not been a persistent issue...this has only happened once.  I've had lots of crashes in Windows, but never flashing lights, so I decided to search the forums.

I did get an error log message:

E [26/Apr/2007:18:31:33 -0400] Creating missing directory "/var/run/cups/certs"

Being a complete noob to Ubuntu/linux, I have absolutely no idea what that means.  I tried to give as much info about what I was doing at the time to help out with the problem solving.  Let me know if you have any other questions.

---

### Post by gmc on 2007-04-27
> **YetAnotherNoob said:**
> I am kind of desperate so after searching the forums I have tried noacpi boot option:

[http://ubuntuforums.org/showthread.php?t=340390&highlight=noacpi+9400](http://ubuntuforums.org/showthread.php?t=340390&highlight=noacpi+9400)

Now waiting to see if it crashes...

How are things going with 'noacpi' ? 

Gord

---

### Post by secret_squirrel on 2007-04-27
Happily for Ubuntu and less happily for my wallet, I've confirmed that the crashing I've been seeing is definitely a hardware problem with my laptop; just coincidence that it started going wrong about the time I upgraded to feisty.

---

### Post by YetAnotherNoob on 2007-04-27
I really appreciate your help.  The noacpi option did not work (or I did not set it up properly).  The crash happened again.  It seems to crash most often using GIMP and firefox.  However, logically I use these two apps the most...so stands to reason.

Unfortunately I have bandwidth issues and cannot download the 6.10 distro at the moment.  

I was running out of ideas but tonight I had two hours spare.  I have reinstalled ubuntu 7.04, same laptop, same partitions.

Fingers crossed. I REALLY want it to work  :)
So I am giving it a try again.   

I noticed that 1 of the apps in the installer crashed during the installation:
**ma-search-users**
I will check this out on the forums after writing this, but I do not think it is critical (I think it might  be a setting import app).

After the install (during reboot) I noticed that there was an message that momentarily displayed.  Something like FSCK found a problem with the disk?
I looked /var/logs/fsck and found:
/dev/sda2: clean, 98191/2992416 files, 618519/5980196 blocks

I don't think it was a problem and I cannot see anything in else in error logs.

I guess I will try stress test it now, once again thanks.

---

### Post by gmc on 2007-04-27
> **skubisnack said:**
> 
I did get an error log message:

E [26/Apr/2007:18:31:33 -0400] Creating missing directory "/var/run/cups/certs"

I'm not sure what part of the cups printing system screwed up but I think we can safely rule out a missing directory as the source of the crashing.

Gord

---

### Post by gmc on 2007-04-27
> **secret_squirrel said:**
> Happily for Ubuntu and less happily for my wallet, I've confirmed that the crashing I've been seeing is definitely a hardware problem with my laptop; just coincidence that it started going wrong about the time I upgraded to feisty.

:-( That sucks. I take it that your warrenty had expired?

Sympathy
Gord

---

### Post by gmc on 2007-04-27
Hi,

> **YetAnotherNoob said:**
> I really appreciate your help.  The noacpi option did not work (or I did not set it up properly).  The crash happened again.  It seems to crash most often using GIMP and firefox.  However, logically I use these two apps the most...so stands to reason.


The correct usage is 'acpi=off' added to the kernel parameters, assuming this is how you used it, try 'pci=noacpi' and see if that helps.

> 
Unfortunately I have bandwidth issues and cannot download the 6.10 distro at the moment.  


Damn, I just checked the shipit website and they are no longer offering to mail 6.06/6.10 cd's. I guess that option is out.

> 
I was running out of ideas but tonight I had two hours spare.  I have reinstalled ubuntu 7.04, same laptop, same partitions.

Fingers crossed. I REALLY want it to work  :)
So I am giving it a try again.   

I noticed that 1 of the apps in the installer crashed during the installation:
**ma-search-users**
I will check this out on the forums after writing this, but I do not think it is critical (I think it might  be a setting import app).


That file (I think) is part of ubiquity package (it's a migration assistant program). You may want to use your favorite package manager (Synaptic?) and re-install it or fully remove it (it's not installed by default here). Though I doubt it will anything to do with the main problem.

You might also want to boot that cd and have it check the files on the disk. If the package errored during install from the cd, the disk might be a bad burn.

> 
After the install (during reboot) I noticed that there was an message that momentarily displayed.  Something like FSCK found a problem with the disk?
I looked /var/logs/fsck and found:
/dev/sda2: clean, 98191/2992416 files, 618519/5980196 blocks

I don't think it was a problem and I cannot see anything in else in error logs.


The good news here is that no files were lost and then recovered with fsck, and considering a hardlock up doesn't allow linux to cleanly shutdown the harddrive (flush cache), these disk checks are to be expected.

> 
I guess I will try stress test it now, once again thanks.


Not a problem. A few years back, I had a system that did the same thing, worked fine in windows and crapped out under linux. In my case we traced it down to a flaky memory chip. Though all memory tests failed to find the problem.

Regards,
Gord

---

### Post by gmc on 2007-05-01
Hi Folks,

S'been a couple of days since anyone posted here. Anyone still having this probem or can I assume the best and everyone is happy.

Gord

---

### Post by skubisnack on 2007-05-01
I've not had any more issues.  I'm happy as a clam ;)

---

### Post by YetAnotherNoob on 2007-05-29
I was on holidays.  ;)
Honestly thanks for all your help, but I am completly out of ideas.  The problem was intermitten (the comp. was stable for hours) then might crash 3 times in 30mins.  The problem was so disruptive to my work I had to give up.  I am back using windows which does not have any problems (runs continually for days/weeks).  In a version or two, I'll come back and try again.

---

### Post by Angelbeast on 2007-05-29
I am having this same problem. And i see lots of others are too. I get the flashing caps lock and num lock every time. I can go up to 2-3 days with no crash though. And as often as once a day. It's getting annoying. If i remember correctly i went the first week with Ubuntu crash free and then it started. And if i am playing any music and it crashes it skips like a broken record. a sure fix would certainly be nice.

---

### Post by YetAnotherNoob on 2007-05-29
> **Angelbeast said:**
> I am having this same problem. And i see lots of others are too. I get the flashing caps lock and num lock every time. I can go up to 2-3 days with no crash though. And as often as once a day. It's getting annoying. If i remember correctly i went the first week with Ubuntu crash free and then it started. And if i am playing any music and it crashes it skips like a broken record. a sure fix would certainly be nice.

This sounds like my problem exactly, but perhaps it is happening more frequently on my pc.  In a strange way it's nice to know I am not the only one!  :p

---

### Post by Angelbeast on 2007-05-30
Well now i'm up to a crash once or more per DAY since an update the other day that included a kernel update. This is just infuriating. I would go back to windows were it not that i seem to have misplaced my windows disk. Has ANYONE found a viable fix for this problem yet? i'm fiarly certian that it wouldn't be a hardware issue sonce itgot worseon a SOFTWARE update...

---

### Post by YetAnotherNoob on 2007-06-04
I think it is a kernel problem.  But have you tried running the memory tests?  It takes about 30mins or so.  I did not find any problems.  But it is one possibility to eliminate.

---

### Post by Angelbeast on 2007-06-06
> **YetAnotherNoob said:**
> I think it is a kernel problem.  But have you tried running the memory tests?  It takes about 30mins or so.  I did not find any problems.  But it is one possibility to eliminate.

i uninstalled google earth and disabled 3d acceleration for my ati video card and haven't had a crash in 3 days...of course now that i've said something i probably will *LOL*

---

### Post by bomanizer on 2007-07-24
Any updates on this? I'm getting similar hangs/crashes on my Thinkpad R50. I has crashed two times, both times I was on battery power, browsing with Firefox. I've got 7.04 Feisty, all normal updates via apt-get and the usual automatix-stuff. I'm not running any printer, web, etc services. The system has to be hard-booted, at the first time it didn't even react to the power button, I had to remove the battery. The second time I powered off with the power button.

edit: a quick look at /var/log shows nothin unusual, then again, I'm not so good with this stuff...
edit (2): Memtest86 shows no bad memory (the grub option), I'll run some CPU tests later...
edit (3): Ok, so far I've isolated some things:
- the crash happens only when running on battery
- /var/log/messages shows something about nm-applet, I'll dig the log once I get home from work
- I was running apmd and acpid both at the same time, which is not a good idea :D. Ok, I disabled apmd but still the system hangs, like described above.
- CPU tests show nuthing. (I performed tests with the [ultimate boot cd]("http://www.ultimatebootcd.com/"))
- I've got only 256mb of ram, could it be an issue?

---

### Post by biggyfries on 2007-07-29
hi, all. Ii guess Im a born-again forum user, since i havent posted for over a year.

Anyway, I, too, am having the same problem. I was running kubuntu breezy, and having a lot of system crashes on DVDShrink converting movies. this weekend, I started over with kubuntu 7.04 Fiesty.  I installed all my regular programs (firefox, dvdshrink/wine, flash, etc).  I also tried out Devede.  

My system is now crashing on Devede, when it is converting MOV to mpeg.  it can get through the small moveis, but it crashes on a 120mb MOV file.

i have test memory with Memtest 86, with no errors, so far.  I reinstalled from the cd, redid my partitions, verified the cd, and tried a fresh install with just Devede installed, with no other extras (browsers, java, wine, etc).  the crash is still happening.  I thought this sounded like a memory problem, where the buffer/memory was getting corrupted, esp. on big files, but it will crash at different percentages of completion, and only happens in dvdshrink and devede, so far. 

dont know if it helps or not, but wanted to let someone else know.  

edit: i am using a home-built desktop. wanted to specify since it seems that other people are using laptops.

d

---

### Post by Slimo on 2007-07-29
Hi guys,

I am running Feisty and have had similar problems by the sound of it - and it's driving me insane.
At first I thought it was my monitor as the system would not return from suspend mode, not even restarting the x-server.  This meant I had to do a hard reset, and while restarting the boot screens were kinda laggy and frozen - hard to explain, but was definitely not normal.

I reinstalled feisty but still get fairly regular crashes - usually while using firefox - although music will keep playing, I just cannot click anything on screen, and ctrl+alt+backspace does not work.

I have had a quick look on the forums and it seems people may be having similar problems.  The crashes also occur when running a Gnome failsafe session - so would that mean it is not driver related?  From those of you who have scoured the forums looking for an answer, does it appear to be a problem with the latest kernel?

I would appreciate any help or advice, or even just some encouragement!!  Ubuntu is great - I have been using it for about 6 months now, but things like this can be a real downer.

---

### Post by perspectoff on 2007-08-03
Google Earth kept crashing for me until I figured out the problem was with the display, not with Google Earth.

I found out that the Ubuntu installer had denoted "VESA" as my standard graphic card in /etc/X11/xorg.conf:

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:0:2:0"
EndSection

However, my system has an Intel 865G chipset with Extreme Graphics 2.

The appropriate graphics driver is i810, not VESA.

I therefore substituted the section:

Section "Device"
	Identifier	"Intel Corporation 82945G/GZ Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

and changed the section:

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
...

to
Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82945G/GZ Integrated Graphics
...

Now both Stellarium and Google Earth work fast and without problems.

The problem seems to be that the auto-detection of my graphics card by the Ubuntu Feisty installation did not accurately identify the graphics card driver needed. This was not a problem in Dapper; I don't know what changed.

---

### Post by ac7ss on 2007-12-12
I am now having the flashing CAPS and SCROLL lights accompanying a lockup. I am running 7.10 on this one, sometimes the system locks when 'reading files to boot' (or something like that.) just after grub.

Funny thing, same thing just started happening on the windows/linux box about the same time. That one is running XP and 7.4. The only thing they have in common is that I replaced the power supplies at the same time. Could this be a power supply problem?

Yes, I have run memtest and not found any trouble. I am now running off of the Live 7.10 and will let you know how long it lasts. (so far so good. but only at 30 min.)

---

### Post by FRuMMaGe on 2008-01-04
THIS HAS BEEN HAPPENING TO ME FOR MONTHS!

However, it usually happens after I leave my laptop lid closed for 10 minutes or more. Sometimes I am just happily working on my laptop when it becomes unresponsive. The screen then starts to systematically fill with "junk" and the computer fan goes nuts.

SysReq does not work.

The other day I noticed my capslock was flashing because of it.

Please help!

---

