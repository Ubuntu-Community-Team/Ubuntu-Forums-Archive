---
title: "Let's talk about crashes/lockups..."
date: 2005-10-14
forum: Desktop Environments
---

### Post by Joey French on 2005-10-14
My new Breezy install has some problems with locking up (hard, unable to restart X) mostly when using Firefox. It seems to be very random, and not really linked to any specific task at all (maybe firefox, I have it running almost all the time when I am on my box, minimized when doing other things). While I am not looking for any sort of diagnosis from you guys, what I am looking for is a good way to find out what the problem is. Is there any sort of log I can look at, anything that can tell me what caused the problem? How should I go about diagnosis?

I am not a new user, I ran Hoary when it released, but it was a lot more stable than Breezy from the onset, from what I gather. As a sidenote, I run Breezy 32 bit with the K7 kernel on an AMD Athlon 64, because of a lack of packages I see as crucial. Could this be causing some of my problem? Is this configuration less stable than Breezy 64 on my 64 bit processor?

Thanks, Joey

---

### Post by fishfork on 2005-10-15
If you haven't already, I'd check your hardware with memtest - press ESC at the start of bootup and select it. Let it run for a few passes.

You could try disabling various drivers: are you using proprietary graphics drivers, for instance?

Good luck. These type of problems aren't so easy to track down.

---

### Post by az on 2005-10-15
There is a graphical log tool.  Use that. 

I once had that kind of problem using a usb wireless adapter, a usb pen drive  and a usb mouse all at the same time.  

I would download something to the usb pen drive and move the mouse and the lights would dim....

---

### Post by Joey French on 2005-10-15
I have tried memtest. This machine is running 2 sticks of 1 gig corsair, tested and in good shape. I would hope that would not be the problem. In fact that was the first thing I tried. No proprietary drivers either, all of my hardware, even 24 bit audio card as well as video card (not really high end) were detected at boot. I also have a hp deskjet that was detected and drivers were installed quickly and painlessly. That's the thing. I love Breezy, it seems to just work out the box...The trade off is, I'm afraid that my machine is going to lock up before I get to the end of this sentence. Add to that the fact that I can get no diagnostic tools, and it is a little worrying.

---

### Post by az on 2005-10-15
Well, the logs are a powerful diagnostic tool.  Can you remember the last time it locked up?  

Look in the logs at the time and date and see what was the last things that happened before it locked up.

---

### Post by barakab on 2005-10-15
hey Joey!!
same problem here..
i upgraded by net from hoary to breezy - all went cool
except 4 this strange freeze / lock up ...
hoary worked gr8 !
and breezy is amazing but these lock ups really ruins it.
i looked at the logs and couldn't find any clue there.
it heppens randomly - no matter if the cpu is idle or not, and no matter what application is open
i'm running IBM thinkpad r50e.

any idea?
(i'll try tommrow to leave it on with hoary's "old" 2.6 kernel)

---

### Post by talkingwires on 2005-10-15
[QUOTE=Joey French]My new Breezy install has some problems with locking up (hard, unable to restart X) mostly when using Firefox. It seems to be very random, and not really linked to any specific task at all (maybe firefox, I have it running almost all the time when I am on my box, minimized when doing other things).[/QUOTE]
Ditto. My first thought was Quod Libet, because it was running the first few times it happened, but I think I've ruled that out. I don't believe it's Firefox; once I had to do a hard reset because of the lock up and it happened a second time right after the reboot with nothing but a Nautilus window open.

My memtest comes back okay, and I'm at a loss as where to even begin troubleshooting this lock up. I stuck with Breezy during the entire development, and this issue only appeared after the last round of dist-upgrades.

---

### Post by doclivingston on 2005-10-15
Are you using the propietry nvidia drivers? If so, it might be [bug 7183](http://bugzilla.ubuntu.com/show_bug.cgi?id=7183), which seems to happen most when scrolling in applications (especially Firefox or Epiphany)

These are the steps I had when trying to determine the cause of the above problem (before I read that bug).

* Notice that my music kept playing and application were still running, so it was only X that had lockup up not my entire computer.
* As I have ssh-server installed, I tried ssh'ing into my locked-up machine from another one. I could, and running top indicated that the X process was hung using all the CPU.
* I killed X, and then looked at the X logs (/var/log/Xorg.0.log), which has a strange error message from the nvidia drivers right before hanging.
* I switched back to the open-source "nv" driver, and tried to get it to hang (which seemed to happen when scrolling in Epiphany/Firefox or editing the toolbar in Epiphany). It didn't happen with the "nv" driver, but was regularly happening with the "nvidia" driver.
* Googled around and looked on the Ubuntu bugzilla. Reports seemed to indicate that turning off "RenderAccel" would fix it, so I tried that and it worked.

---

### Post by xombie on 2005-10-16
I had a box that was locking up hard constantly. I removed powernowd and its been up ever since.

---

### Post by solstice on 2005-10-16
This is my first time using gnome, and the first time i have had a linux install never lock up. This must be my lucky install, super stable. 

I have always run KDE before, i'm guessing that was the source of my problems (at least on the machine i'm running).

---

### Post by Joey French on 2005-10-16
Okay, so the log file to check next time it hangs/locks/whatever is at /var/log/Xorg.0.log, so I should wait for it to lock, and check it after reboot? This is encouraging, as at least it is a place to start. Also, what is this "powernowd", and how would I look at it's affect on my machine? 

I don't have any proprietary drivers for sound or video, I don't think, all of them were handled at install by breezy. I have not installed a driver under Ubuntu thus far.

I have no idea what Quad Libet is. I have had the whole lock up with FF running/reboot/lock up a minute later without FF running- scenario as well.

Strangely, it hasn't locked up in the last few hours since I posted this. Typical...

Again, does anyone think that running 32-bit on a 64-bit processor is a problem? Would a kernel recompilation for my machine help matters at all, maybe cleaning up things a bit, or have I got the wrong idea about kernels? 

I will post the log from Xorg the next time it locks up, so maybe someone can help troubleshoot. Thanks for the replies!

---

### Post by doclivingston on 2005-10-16
[QUOTE=Joey French]Okay, so the log file to check next time it hangs/locks/whatever is at /var/log/Xorg.0.log, so I should wait for it to lock, and check it after reboot? This is encouraging, as at least it is a place to start.[/quote]

If you've restarted normally, and X has loaded, it will be moved to /var/log/Xorg.0.log.old You can either check that, or restart in "recover mode" and it will still be in the original location.

> I don't have any proprietary drivers for sound or video, I don't think, all of them were handled at install by breezy. I have not installed a driver under Ubuntu thus far.

If you have a nVidia card, I'm fairly sure that Ubuntu installs the proprietry nvidia drivers by default (but I could be wrong).


> Again, does anyone think that running 32-bit on a 64-bit processor is a problem? Would a kernel recompilation for my machine help matters at all, maybe cleaning up things a bit, or have I got the wrong idea about kernels? 

Running a 32-bit installation on a 64-bit system shouldn't be a problem at all. Many people do it because they want/need the 32-bit flash plugin, video codecs et al, which can be awkward to install on a 64 bit system (chroots and the like). You shouldn't need to recompile your kernel unless you have a good reason like adding/removing drivers or playing with kernel patches.

---

### Post by Joey French on 2005-10-16
Yeah, that's what I was thinking. I ran Hoary 32-bit on this box fine. I will have to check on the drivers, I have no idea which one's installed right now. It just worked out the box, so I didn't question it. 

What you're saying is, I should check the log in safe mode after rebooting? Otherwise the log moves to another location? Okay, now just have to wait for it to freeze again.:rolleyes:

---

### Post by doclivingston on 2005-10-16
[QUOTE=Joey French]What you're saying is, I should check the log in safe mode after rebooting? Otherwise the log moves to another location? Okay, now just have to wait for it to freeze again.:rolleyes:[/QUOTE]

Yep, when X starts it moved "Xorg.0.log" to "Xorg.0.log.old" and then writes the new one. So if you've restarted X more than once the log is gone (unless it archives it somewhere that I don't know about).

---

### Post by barakab on 2005-10-16
hey! Joey!
since i took the powernowd no lock up appeard !
i'll leave it on and i'll update u l8er.
btw - anyone know if it is safe to work without it? (powernowd)

---

### Post by doclivingston on 2005-10-16
[QUOTE=barakab]anyone know if it is safe to work without it? (powernowd)[/QUOTE]

It's used to control processer voltage and speed, and fans. So unless you're using a laptop it probably isn't that useful.

---

### Post by barakab on 2005-10-16
Hmmm
thanks for the quick post!
i've read now on powernowd project site that it is unstable... strange it's official on breezy...
anyway, acpi is not enough for my laptop?
it is also caused me to think - a classic lock up appear when the cpu reachs high temp. - maybe powernowd is preforming bad ?

Thanks in advance!

---

### Post by Joey French on 2005-10-16
So, who else believes powernowd may be a reason for my crashes? Is it something that is easily disabled? I have noticed strong spikes in my cpu when opening certain applications (Firefox again) but top says it's only using a small amount of system resources.

I am still waiting for my system to crash so I can check the logs. Funny how that works.

---

### Post by xombie on 2005-10-16
You can just use synaptic package manager to remove powernowd or dpkg --deinstall powernowd. In synaptic if you highlight a pkg it gives you a description of the pkg.

Over the last several years power management is probably the number one cause of hard lockups. The combinations of motherboards/processors and the quality of the bios (the controll of the voltage regulators and clock chips) make it very difficult for the software developers to achive a robust universal solution.

Its is however noble to try to make it work because of the energy savings possible. Unfortunately for some of us it does not currently work on our hardware.

---

### Post by barakab on 2005-10-16
hey Joey ;]
same here, still waiting for a freeze.. :]
but the diffrance between us is that i took off the powernowd !

good luck 2 both of us :]]]

(thnx xombie - if it is indeed the powernowd - i'll use synaptic)

---

### Post by Joey French on 2005-10-16
Okay, mine crashed. Only thing is, I looked in xorg.0.log.old and xorg.0.log and there was nothing there. Empty. What's going on here? 

I will try powernowd removal via Synaptic, and report back soon.

---

### Post by ameerirshad on 2005-10-16
I have a likewise problem and I doubt if it is a hardware problem. As I have used Hoary for a long time, upgrading the Firefox with some backports and all worked fine. Even when I upgraded to the pre-release of Breezy my computer worked fine!

But now I have upgraded to the final release of Breezy, and my firefox starts to crash. Even making my whole system stalling. I mean, it feels like I'm running windows. Something I'm not used of Ubuntu. 

So I checked one time (when, with great difficulty I was able to get "system monitor" running, and saw the memory usages of Firefox way above 100MB, the only other program reaching that is aMule (which I first acused of making my system crashing). 

Are there any possible issues known around this?

---

### Post by Joey French on 2005-10-16
Um, when I go to synaptic to remove powernowd, it says ubuntu-desktop must be removed as well!

What in the world...? Ok, now I need some more advice.

---

### Post by Joey French on 2005-10-16
Also, I have been using Epiphany browser for the last day, so it isn't FF either. I was using Epiphany when it froze 30 minutes ago.

---

### Post by fishfork on 2005-10-16
[QUOTE=Joey French]Um, when I go to synaptic to remove powernowd, it says ubuntu-desktop must be removed as well![/QUOTE]

Don't worry, this is just a metapackage and can be removed safely. This happens if you try to remove anything in ubuntu main.

---

### Post by Joey French on 2005-10-16
Okay, will report back soon.Still looking for opinions of whether powernowd should be first area of investigation...

Thanks all!

---

### Post by Joey French on 2005-10-16
Done. Will see how it goes for a bit.

---

### Post by barakab on 2005-10-16
hey Joey!
just got back to my box - it is still on!
no freeze!
it is probably with no doubt the  powernowd !
i'll use synaptic to remove it & i'll report tommrow to the bug tracking system (where ever it is...)
good luck 2 u ;]


btw... all those with FF and other crashs - i (and i think joey 2) talked here about a sudden freeze of the machine which only a reboot recovers from it... nothing like 100% of cpu usage... it has nothing to do with apps - except 4 powernowd.

hope it will help anyone else, ciao.

---

### Post by Joey French on 2005-10-16
I have removed powernowd, and I have not seen a crash yet. it has been only a few hours, though. There's still time.

Keeping fingers crossed...

---

### Post by barakab on 2005-10-17
joey don't ask...
had 3 freezes allready !
it is not the powernowd (4 me at least..)
one freeze accured while boot, i have no idea.
i'm trying the 2.6.10 hoary kernel now - inform u l8er,
bye

---

### Post by talkingwires on 2005-10-17
[QUOTE=doclivingston]Are you using the propietry nvidia drivers? If so, it might be [bug 7183](http://bugzilla.ubuntu.com/show_bug.cgi?id=7183), which seems to happen most when scrolling in applications (especially Firefox or Epiphany)[/QUOTE]**snip**[QUOTE=doclivingston]* Googled around and looked on the Ubuntu bugzilla. Reports seemed to indicate that turning off "RenderAccel" would fix it, so I tried that and it worked.[/QUOTE]I tried your suggestion last night and haven't had the freeze since. Hopefully a solution or patch will present itself in the future, as the lack of hardware acceleration might put a damper on Gnome's Cairo plans...

---

### Post by baronKarza on 2005-10-18
Hi guys! I also had some crashes/freeze of my Dell precision M70.
I was not able to guess what's the problem: suddenly my pc freezes and it is impossible to ping or ssh. At beginning I thought it was due to X or some nVidia driver but, since the machine becomes unpingable, probably the problem resides somewhere else.
The bad news is that the problem occurs (sometime unpredictable, with the more different application: Firefox, eclipse, synaptic, totem,...) both on Hoary and Breezy.
Any idea?
Thx in advance.

---

### Post by barakab on 2005-10-18
hey u
same here - except that i had no such locks on hoary.
anyway, i'm still on the 2.6.10 (hoary's) kernel with no freeze yet since yesterday.
waiting for joey's situation.
if you get some info. plz note us, i have no clue how to figure it out. the log files seems fine.

---

### Post by Havoc on 2005-10-19
Hi.I've been having the same kind of crashes for quite some time now, both in hoary and breezy (Which I use now).

The problems started after I "found" a bug in DR-DOS that erased the partition table of my Hoary HDD.So, I thought I would try out Gentoo.I found out I wasn't ready, and after I reinstalled Hoary on a clean HDD, the problems started happening.So, It's not Ubuntu on it's own, but a more complex problem going on.I have a Nvidia TNT2, and whilst I used the "nvidia-glx" (That uses "nv") driver on Hoary, now it refuses to work properly, and so I have to install "nvidia-glx-legacy", that uses the "nvidia" driver on xorg.conf.

I'd like to point out that the computer freezes rather randomly, and the freezes do not seem to be connected with a particular action.Either I'm surfing with Firefox, or browsing Synaptic, or using Azureus, or whatever.Also, and this is very interesting, the computer refuses to freeze in a virtual terminal (CTRL+ALT+F1 - F6), even when gnome is running in the backround, so, the freezes seem to be connected with X doing something in the foreground.I've tried running with "nvidia-glx", "nvidia-glx-legacy", or nothing of the both, and it still freezes.

This is quite annoying.I've used memtest and no problems, disabled "powernowd" or whatever, and nothing, played with the nvidia drivers, as I said, and nothing....The annoying thing is that, I KNOW It's not the distro, I know It's not the drivers (at least on their own) and since it seems quite widespread, I know It's not the hardware (At least on it's own).The only explenation is that, the Nvidia Drivers are passing something the cards can't handle.Maybe It's got something to do with that "RenderAccel" thingie...Where can I find that? :confused: 

Thanks! :D

---

### Post by Robgould on 2005-10-19
Hey everyone,
I am new to Ubuntu...came from Fedora and love it.  It works.  That simple.  My only gripe is the freezeing issue that I am having as well.  I am using a Toshiba Laptop.  I think I can help rule out the Nvidia link, as I use ATI video card.  I noticed that everytime I freeze my CPU usage goes to 100%.  As soon as this happens, a freeze is about to happen.  This mostly seems to happen when I am running Java applications....Azureus, Limewire, that type of thing.  Every time I start Azureus, in a matter of minutes the CPU usage goes to 100% (I am using a p4 with HT and the SMP kernel) and then the system locks.  This also happens with Bittorrent, limewire, etc....  I wonder if when you crash withe firefox if you are a java page or something.  Not sure how that works.  I am considering going back to Fedora.  It is not as nice as Ubuntu, but It NEVER crashes like that.  Anyway, that is my two cents, hope it hleped.  I am also using 512 ddr sdram.  There is no way that my processor should be goint to 100% to run limewire.  In thinking about it, I don't think my Ubuntu has ever crashed until after I have added applications.  One of the first things I alway have done is run automatix or easy ubuntu, both of which install java.  Maybe I am way off.

---

### Post by Havoc on 2005-10-19
Well, It COULD be java.See, I'm not having this "100 % CPU Usage Thingie" and I bet the rest of the guys here have the same opinion.The only thing I could suggest is, uninstall the java package, through synaptic, and replace it with the java package found in "Applications--->Add Applications", the one named "Black down Java" or whatever.I've found it much better than the "official" Sun Java Package.

If that doesn't solve your problems then...Unless you be patient for a while to try and diagnose your general problem, we can't help you all that much.

---

### Post by Robgould on 2005-10-20
Ok, here is an update.  I did a clean install of 5.10 (again) last night, and just let it run.  No additional packages whatsoever.  I never had a lock-up.  So I got to looking around.  I added system monitors to my task bar and added a processor speed scaling thing.  And I watched them as I worked.

I have a Toshiba Satellite Laptop that I use wireless.  Atheros wifi, ATI graphics, Pentium p4 (3.46 ghz with hyperthreading), alps touchpad, usb mouse.  

When I added the cpu scaling monitor I noticed immediately that my CPU was scaled to 1.8 ghz, about half of its capacity.  This was true even though I was plugged in.  I ran some stuff and noticed very large spikes in CPU usage that the processor scaling did not seem to respnd to at all.  I am not sure how this is supposed to work exactly, and since I am trying to limit variables, I killed poernowd.  As soon as I did my processor went to full speed (3.47 ghz actually reported).

My memory said it was runnin 95% - 40% of it cache, when the system was just sitting there idle.  So I tried to look at my services and see what I could kill, but in Ubuntu this menu seems to be restricted, only showing cups, cron and a few others, not the list I am used to seeing....I had class last night, so this will wait.

Everything seemed ok so far, so I installed the SMP kernel that I think I should be running with my processor.  I read that the hypertrheading cpu's appear to the system as two.  I am not sure this is correct, but it is what I am operating on.  When I installed the smp kernel, my system looked much better.  I have not seen a cpu load above 50% and my memory went down to 66% on start-up.  After the system runs idle for a while my memory usage creeps up though and ends up running at about 75%.  Still better than the 95% with the other kernel.  I let this run all night all long with the screen savers running.  No lock ups.

It looked like the screen saver was stalled this morning, but a wiggle of the mouse and I was going.  I don't know how much of a test this was, but I am moving forward.  Tonight I am going to install some of the apps that I like and use the system some and watch what happens.  I am going to avoid Java based apps.  I will report back.  I hope I am helping, if not tell me to be quiet.  

I do have a couple other questions after last night.  

1.  Is the smp kernel the right one for my proceesor?

2.  I have 512 DDR Ram, should my memory be running at 75%, 48% of that cache?  Is this a normal load?

3.  Most of the hardware on my computer shows as unknown in the gnome applet.  cpu-unkonwn etc....  Could this be part of my issue?

Thanks for all the help.  Ubuntu has an awesome community, I'll give you that for sure!

---

### Post by doclivingston on 2005-10-20
[QUOTE=Robgould]2.  I have 512 DDR Ram, should my memory be running at 75%, 48% of that cache?  Is this a normal load?[/QUOTE]

That means 27% of your memory is "in use", which is ~130Mb. Depending on your exact system and what you have running, that is about normal.

---

### Post by Robgould on 2005-10-20
[QUOTE=doclivingston]That means 27% of your memory is "in use", which is ~130Mb. Depending on your exact system and what you have running, that is about normal.[/QUOTE]

Thank-you for the reply.

---

### Post by Robgould on 2005-10-21
update...installed software last night....everything looked ok.  So I got over zealous maybe.  Installed Java and Azureus. Worked fine.  Running azureus now with no cpu issues at all.  Let it run all night....

Woke up this morning to a locked up system.  Fan running wide open.  Could not see the sensors as the screen saver image was locked on screen.  The screensaver that was running is gears (planetary).  I guess that makes me think about my vide driver....anyway, I set the screensaver to blank screen and fired it back up this morning.  Hopefully when I get home tonight I wll have my copy of Aleaxander ready to watch.

---

### Post by regeya on 2005-10-21
Adding my voice to the 'I'm experiencing random lockups" complaints.  I thought it was because I have an extremely (some would say excessively) gimpy Via-based system, and that maybe someone had compiled something important with CMOV enabled.  If a bunch of y'all are complaining about it, though, I'm betting that's not it.

I did a clean Breezy install and I'm experiencing lockups.  A couple of times my machine has frozen at the KDM prompt; the rest of the time, there doesn't seem to be any connection.  I've tried to keep track of it but I've been doing different, yet equally mundane, things when it happens.  Most frustrating of all is knowing that my machine, thanks to backports and unofficial repos, was more-or-less up-to-date before the Breezy fiasco and with absolutely no unexplained freezes whatsoever.

This is what I get for mouthing off about Ubuntu just sitting there and working; this is reminiscent of my first experience with Windows 98. :-(

So I'm not seeing anyting out of the ordinary in the logs.  Or am I?  I'm seeing something right before I restart that I suppose could cause the problem, but I'm not sure:

```
Oct 21 09:18:21 leto kernel: [4295534.890000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Oct 21 09:18:21 leto kernel: [4295534.890000] apm: disabled on user request.
Oct 21 09:18:21 leto modprobe: FATAL: Error inserting apm (/lib/modules/2.6.12-9-386/kernel/arch/i386/kernel/apm.ko): No such device

```

can anyone confirm or deny this?

I've removed powernowd, which has the unfortunate side-effect of removing kubuntu-desktop.  Not sure if that has any bad effects or not.

---

### Post by Robgould on 2005-10-22
Well I am updating again....from windows xp.  Ubuntu is comletely unusable for me.  I have given up for now until I read an update on here.  Locking up at random several times a day is simply not going to work.  I have tried everything that I can think of.  ati driver does not work.  fglrx does not work.  vesa, no lock ups, but video does not work for crap.  This is not bashing......I really like Ubuntu and I tried.  I have a partition on my hard drive just waiting for it, but I will be cautious now.  The bad part is, I used the release candidate for a couple of weeks with no trouble.  In reply to regeya, win98 did not crash this much.  I am sure that I am in the minority and the trouble lies in my hardware.  I will try another day.

It looks the people of ubuntu are aware of this issue and hopefully will fix it.

[bug 10579]("http://bugzilla.ubuntu.com/show_bug.cgi?id=10579")

---

### Post by Havoc on 2005-10-23
Ok, here's some more feedback by me.

First of all, it does NOT seem to be a Xorg problem.I booted up in recovery mode, and checked the logfiles, and everything seemed ok, until the crash/freeze.The only thing that concerns me is there is no "crash dump" inside the Xorg logfiles.So, Xorg might be freezeing up, hard, but it does not seem to be the problem.

In one of my posts before I told you that It won't crash inside tty.I was wrong.It probably was a devilish coincidence, but it has crashed on me, twice.The first one gave me no feedback, which was the original purpose, and so it made me think that it's not a Kernel Panic either, just a freeze caused by the Graphics card along with the drivers.BUT, yesterday, the system crashed again, and this time, it gave me feedback, but it seems it was not able to give a full report, just 4-5 lines.Here's what I wrote down:

```
Machine Check Exception ....
bank1:00000000000001
bank2:0000000....
Kernel Panic - not syncing: CPU context corrupt 
```

Of course, I just wrote down what I thought was the most inportant parts, not everything.Could someone with experience tell me what this means?

Thanks!

---

### Post by ThaRabbit on 2005-10-23
This may seem trivial, but is your system suffering from the double clock speed issue ? You can easaly check so by launching a cpu load monitor to see if it's under 50% load when doing nothing.

I installed 32 bit ubuntu on my 64 bit amd box a while back which caused simmilar problems at the time.

just my 2ct.

---

### Post by Havoc on 2005-10-23
If you're talking to me, then no.There has been no suspicious things going on with my computer.That's why I'm confused.

Now, I know It's NOT the kernel.I'm on a Athlon XP (32 bit) and the crashes happened with Hoary's i386 kernel, and now they've been happening with Breezy's default 386 kernel, the 686 kernel and the k7 kernel, which I'm using now.

I guess I've got that cleared up. :D

---

### Post by barakab on 2005-10-23
well, for me it's the kernel for sure.
since i'm using (almost a week) the hoary's kernel - 2.6.10 - i had no freeze.
i have no idea y is that.
:/

---

### Post by Havoc on 2005-10-23
What are the "side effects" of using the Hoary Kernel?

---

### Post by barakab on 2005-10-23
no usplash at boot? :)
that's all 4 me...

altough i'm sure i can easily configure it to work with this kernel also.

---

### Post by Robgould on 2005-10-23
I am having success now.  I got to thinking about hte kernel thing.  I re-installed.  This time I am using the regular 686 kernel instead of the 686-smp.  Been since last night.  So far - no lock ups.  Nothing bad at all.  Just smooth operating.  I think it was the smp kernel causing me the trouble.  

Brings me to this question again....should I be using the smp kernel with my processor?  I am using a p4 with hyperthreading.  I read somewhere that I should use the smp, but I'm not sure.  

Anyway, I'm a happy man so far.  Will post if issues return!

---

### Post by nix4me on 2005-10-23
Mine works fine.  The brezzy version of Firefox sucks so i installed the beta from mozilla.  Not a single problem since I installed except for Firefox.

nix4me

---

### Post by Robgould on 2005-10-24
Update....Moday morning....still going with no lock-ups since Sat night.  I am convinced, it was the smp kernel.

---

### Post by Havoc on 2005-10-24
Well unfortunately, the Kernel seems to fine, since I've used every damn kernel there is, and hoary's 386 kernel did not make a difference.So, it's not Linux.

I give up.I've tried everything (Well not really).I'll have to live with the crashes till I figure the problem out.And NO, I'M NOT GOING BACK TO WINDOWS!!

Linux is still more stable than Windows. :cool:

---

### Post by jshein on 2005-10-24
I was running x86_64 Breezy for the last month and a half, and for package reasons switched to the 32 bit version of ubuntu.

Acer TravelMate 4400 Laptop
AMD Turion 64 ML-30 cpu
512 mb ram

Here is what I have found:

First of all, switching to 32 bit almost doubled my battery life !!!


i386 kernel runs OK. Had 1 lock up.

k7 kernel runs slower, and wil not properly resume from hibernation, occasional lock-up

i686 kernel runs perfectly. longer battery life, resume, suspend to disk and to ram.

---

### Post by Robgould on 2005-10-24
still going!

---

### Post by RAOF on 2005-10-25
[QUOTE=Havoc]...BUT, yesterday, the system crashed again, and this time, it gave me feedback, but it seems it was not able to give a full report, just 4-5 lines.Here's what I wrote down:

```
Machine Check Exception ....
bank1:00000000000001
bank2:0000000....
Kernel Panic - not syncing: CPU context corrupt 
```

Of course, I just wrote down what I thought was the most inportant parts, not everything.Could someone with experience tell me what this means?

Thanks![/QUOTE]That kernel panic says, I believe:
"I tried to switch threads, or from userspace to kernelspace, but when I restored the CPU context for the thread (the instruction it was running, the CPU registers, etc), it turns out that it was corrupt.  This is so terribly bad that there's no way I can sensibly recover.  Have a kernel panic :)"
If you can get this to happen on multiple kernels, I imagine it's an intermittent hardware problem, which could be anything from an overheating cpu, to bad ram, to a poor power supply which goes undervoltage sometimes...

---

### Post by RaHarakhte on 2005-10-26
I've been going crazy over the lockups myself.  As a Linux n00b who came to Ubuntu after a glowing recommendation, this was hard for me to deal with.  Hoary worked wonders on my system as compared to Windows and actually helped fix a real funky lockup I would experience with my sound card, but Breezy was killing me. Over dinner tonight, though, I think I found my solution.

My Breezy lockups seemed to relate either to APIC or to power management issues.  I still haven't decided for certain which it was in my case, but I did notice a lot of APIC errors in my log in the neighborhood of crashes; it raised suspicions.  But either problem can bite you either way, so I decided to just kill two birds with one stone)  I took the following steps:

To deal with APIC, you can pass the noapic option through GRUB as you boot.  Alternatively, to permanently add noapic to the boot process, you can do the following:

In your terminal, type:
[LIST=1]
[*]```
sudo gedit /boot/grub/menu.list
```
[*]Add noapic after your kernel of choice and save.
[/LIST]

That deals with APIC.  Now, for power management, you can try to deactivate APM and ACPI from your BIOS.  Mine didn't allow this, so I had to manually instruct Ubunbtu to stop them.  You can do this, again, in your terminal using the following commands:

```
/etc/init.d/apmd stop
/etc/init.d/acpid stop
```

I've added these two instructions to my Sessions manager so that they are done automatically at each boot.  Go to System -> Preferences -> Sessions, select the Startup Programs tab, and add the following:

```
/etc/init.d/apmd stop & /etc/init.d/acpid stop
```

(Someone please correct me if my contruction is wrong.  This is cutting-edge n00b4ge happening here. :lol: )

I've been running fine for hours now since implementing these fixes--which is unprecedented for Breezy on my desktop.  I may one day go back and determine exactly which issue was *the* issue; right now, though, I'm quite content to just enjoy my happily-buzzing-along (at last) install of Breezy! :grin: 

I hope this helps someone (or everyone :)  ) out there.

These steps, for the record, were googled up from within the forums themselves:
[http://ubuntuforums.org/archive/index.php/t-14971.html]("http://ubuntuforums.org/archive/index.php/t-14971.html")
[http://ubuntuforums.org/showthread.php?t=39819&page=2]("http://ubuntuforums.org/showthread.php?t=39819&page=2")

---

### Post by Havoc on 2005-10-26
Hey, thanks! I never thought of that.Great first post!
Anyways, you can download BUM (Boot Up Manager) for all your boot services needs.It's much easier than most workarounds posted around here, and even more efficient.

As for RAOF's post, thanks for the clearup.A couple of weeks after the crashes started happening I checked for a possible hardware failure and I found I had disconnected the northbridge fan, because It was making the most annoying sounds (But it otherwise worked great).I think I disconnected it about the time that the crashes started...It COULD be this, but I'm not 100% sure.But my box sure gets HOT in there!

Thanks everyone! Ubuntu still rocks for me! I'll try everything you said and I'll return with results.

---

### Post by Joey French on 2005-10-27
Okay, so I am back. 

After following the advice of a previous poster, I removed powernowd, and have been doing regular updates. NO LOCKUPS since. What is going on? Is powernowd that big of a deal, and what effect (potentially) could removing it have on my system? I am very happy that my system is stable after this change, but is it the powernowd, or maybe an update that fixed my problem?  

So, something I've noticed, and it it related to the FF thing... If I am listening to something on RealPlayer/ XMMS/ whatever, and browsing using FF, when I scroll quickly the sound cuts out for a split second, and the processor load jumps to 100%. Only for a second, though. Are the crashes I was experiencing earlier and this phenomenon related?

---

### Post by Havoc on 2005-10-28
Well, as suggested by previous posters, I've disabled everything and the system is working great!

No, really, I disabled powernowd, and nothing.Then, i disabled apm, acpi through BUM, and put the "noapic" argument in menu.lst, and no crashes since!

Thanks, megashake! :cool:

---

### Post by Robgould on 2005-10-28
I am running all of those services....disabled nothing and having no more lock ups....for almost a week now.  All I did was switch the 686 kernel.  I am running poernowd.  Like I said, nothing at all disabled.

---

### Post by Robgould on 2005-10-28
poernowd is used to control your CPU speed, specifically to slow it down when the speed is not needed and keep your system cooler and extend battery life on laptops, etc.....   When your CPU load goes up, powernowd shoule respond and increase your CPU speed in response.  I have it running on my lpatop and it works fairly well.  You can see what it it doing by adding a little icon to your bar on your desktop.  click on the add to bar thing and select cpu scaling monitor (going off memory here, I am at work).  This will show you your CPU speed.  You can watch it respond and change speeds as you work.  If you disable poernowd, your cpu will run at full speed all the time.  This is not a horrible thing if you are not worried about heat or battery life.   There are really no negatives to diabling it other than that.

---

### Post by JordanH on 2005-10-30
I have been having the same issues.
See: [http://www.ubuntuforums.org/showthread.php?t=80704](http://www.ubuntuforums.org/showthread.php?t=80704)

For me, the "crash/lockup" isn't really a crash, it's an extreme slowness.  Like it takes 10 minutes for it to go from login to showing the password prompt.  (with patience, this gives me time to umount my data partitions)

I have disabled power management in my bios, turned off acpid from my init scripts, ensured powernowd isn't running... (Did you disable or remove powernowd to work around your issues?)

Still no luck.

---

### Post by Joey French on 2005-10-30
Wow, I don't have those problems. My box is fairly speedy, just locked up now and again. I actually removed powernowd via synaptic. Seems that if I need to, reinstalling will be no problem.

---

### Post by JordanH on 2005-10-30
[QUOTE=Joey French]Wow, I don't have those problems. My box is fairly speedy, **just locked up now and again.** <snip>.[/QUOTE]
:???:  You shouldn't accept a lock-up every now and then.  My linux boxes have routinely run for 3-9months without needing a reboot. I typically plan on rebooting them once every 3 months for maintenance...  So ANY lockup is a bad lockup.

---

### Post by speedsix on 2005-10-30
Is anyone else having hangs when shutting down? My gdm seems to have trouble terminating sometimes, I can ctrl-alt-f1 and shutdown from there. Only happen occaisonally but v annoying. Hoary was fine.

I also had the powernowd issue when Hoary was first released, no idea why it hasn't be fixed/exluded from Ubuntu by now.

---

### Post by Joey French on 2005-10-31
> You shouldn't accept a lock-up every now and then. My linux boxes have routinely run for 3-9months without needing a reboot. I typically plan on rebooting them once every 3 months for maintenance... So ANY lockup is a bad lockup.

Well, that's why I started this thread. Anyway, since this thread has started, It was suggested that my powernowd was broken, so I removed it, and my box has been up for the last two weeks, no problem. I realize that Linux as an OS should be running quite stable, unless there is something is very wrong. My Hoary install went down twice: when lightning knocked our power out, and when I moved to Breezy!

---

### Post by barakab on 2005-10-31
Well joey... same here but now i'm using the hoary kernel 2.6.10. not experiancing any locks with it - u tried it ?

---

### Post by JanZ on 2005-11-02
Hi guys,

my 5.10 started playing tricks on me too. I am not able to eject the CD-ROM, not with the eject menu, not with the external button on the drive itself. A minute or two after attempting to do that, the system totally freezes. No mouse activity, nothing. I have to use the reset button on my machine to reboot. After that, as I log on, the CD-ROM opens nicely. But then, after some relatively minor uptime, I encounter the same problem again.

Now, I hope the problem is not connected with Mozilla, because I lost all Mozilla's bookmarks after the last freeze. Actually, sometimes I get spontaneous Mozilla crashes too.

Any ideas?

---

### Post by Joey French on 2005-11-04
Hmmm. I don't know about that one. Are you playing movies, burning, listening to cds, what's going on while the tray is locked? What programs are running when this happens? FF? Need a little more info.

---

### Post by LazyTux on 2005-11-07
Hi guys, I'm a avid linux convert after MS made me angry after telling me I couldn't install and verify my own software because I had formatted and reinstalled it on the same machine too many times...

Nonetheless, I've been running Breezy on my laptop for while, no problems, but my desktop keeps locking up.  It only seems to lock up at night or when I'm not at it for some reason, never while I'm using it, which makes me think it has something to do with power management as well, or perhaps the nvidia drivers.  I'm going to try tonight when I get home to uninstall powernowd and the other power management options you mentioned.  I've formatted several times, reinstalled both the 64 bit and 32 bit versions using the standard kernel that comes with breezy.  

I have a AMD64 machine with Nvidia 6600 video, 2GB corsair (good, ran memtest), and a 10Krpm maxtor.  I'm trying to get it set up as an apache, ssh, and ftp server, and it is about to make me scream having to reboot my machine two or three times a day.  In contrast, I installed Breezy, apache, and SSH on an old machine at work and its been running flawlessly for 2 weeks...grrrrrr....:confused: 

I'll try the powernowd and nvidia uninstallation, and let you know if I have any luck.  Any other suggestions are welcome.

---

### Post by FX on 2005-11-08
Well I have been having the same problems. Read through this post and decided to try removing powernowd. Before I did that if I had noatun running with xchat/gaim/opera it would lock up. After I removed powernowd I could do all of that with no problems. I THOUGHT it was fixed. After leaving the laptop up all day I come home and it was fine. Came here to post that my problem was fixed and it locked up.

I'll play around for a little bit and see what happens.

By the way the system specs are....

Toshiba laptop
P4 2.8 HT
SMP Kernel
512 megs ram
Nvidia Drivers installed.

---

### Post by LazyTux on 2005-11-08
Well, since I reinstalled about 18 hours ago I haven't had any lockups...doesn't mean its not coming though.  What is noatun?  I read to put 'noapic' after the kernel options on bootup.  I haven't installed the nvidia drivers yet, and the only problems I'm having seem to be with Firefox making X go crazy and my screen going part white/part multi-color and it won't fresh anymore, but that's probably a whole seperate issue.  Do you have good success with Opera, if so, I may swap to it.

---

### Post by FX on 2005-11-08
Noatun is a media (mp3/music) player for kde.

---

### Post by brickpit on 2005-11-10
[QUOTE=azz]Well, the logs are a powerful diagnostic tool.  Can you remember the last time it locked up?  

Look in the logs at the time and date and see what was the last things that happened before it locked up.[/QUOTE]

What logs are you referring to?  (I am a newbie, so forgive my ignorance).  Are they in a paticular file or are you looking at something in the GNU GUI?

My install of 5.10 is freezing up in GNU regularly.  I'm thinking it could be a RAM issue.  I only have 128 Mb.   I've run memtest but it shows no errors, but when I log onto the GUI I can see from the system processes that my User Memory is already at 70-80% capacity.

Any logs you can point out that would help me diagnose the problem would be helpful.  Also, are there any vanilla processes that I can "kill" to help conserve RAM?

---

### Post by etc on 2005-11-10
Whenever I play a graphics intensive game on my laptop (uses an integrated video card and shared memory), X quits, tries to restart and gets caught in a loop of quitting and restarting.
I mean sometimes things like bzflag trigger it to do this.

---

### Post by andril on 2005-11-10
Please :confused: bless me with resolution with my headache - it runs smooth at times and then again it seems slower than Hoary.

---

### Post by Limulus on 2005-11-11
OK, I don't know why exactly, but in the last week I have had two remarkable (for Ubuntu ;)) crashes which occurred under similar circumstances.  I had been running my computer for many hours and while using Firefox, I would navigate to some innocuous page I had been to before without incident and WHAM!  Firefox would crash, taking out Gnome and then from the command line login which appeared, the computer would just shut down >_<;;;

Dunno where the problem is...  I have my /home folder on a separate partition; should I consider reinstalling Ubuntu? -_-;  I upgraded from Hoary (worked fine) to Breezy Colony 4 and then Breezy via repositories (some minor problems since then).

**Edit:** It seems it wasn't Firefox's fault. See [http://ubuntuforums.org/showthread.php?p=543549](http://ubuntuforums.org/showthread.php?p=543549)

---

### Post by harkonen on 2005-11-11
Hi!

I've experienced lockups too. :(  The situation is:

I've put together a system, that is made of:

Shuttle XPC ST61G4
Intel Celeron D 325
512mb memory
160gb seagate SATA drive
integrated graphics, sound and network

For two weeks, everything worked perfectly, from installation to printing and burning dvds. It was sweet ride. :) Until two days ago, lockups started to occur. First I thought that they happen because I changed audio sink settings from ESD to ALSA, but changing them back and/or disabling system sounds didn't work.

The main observation is: lockup _only_ when browsing web, with galeon or with firefox, no difference, and _only_ when loading a web page (random). And even further, seems that they occur atleast more easily, when trying to scroll down the page while it is still loading.

I tried to disable the powernowd as someone suggested, and still waiting for a lockup... ;) Hope that helps, but it is too early to tell...

-Henrik

---

### Post by barakab on 2005-11-11
Hey all, 
i'm updating from kernel 2.6.12 of breezy (4 those who don't know, i draw back to hoary's (2.6.10) kernel to avoid the lock ups).
since i removed the DPM (Display Power Managment) i had no freeze. I hope this is the solution. (it was posted earlier in this thread i think)
if anyone else wanna try it just disable the power managment inside the advnace tab of the screen saver settings.

i'll update again if i will experiance a freeze or in a week.

just a note to all the guys with high cpu load or Firefox crashs etc. - plz read the 1st post of Joey again. this thread is about system freeze/lock, not about some applications crash or so. if any of the forum admins would clean this thread from these non-related posts - users who have system lock ups/freeze will be able to solve thier problom much easier.

---

### Post by harkonen on 2005-11-11
*sigh*

Another complete lockup... my gf seems to be very good at reproducing this. :) Again, when galeon/ff loads a webpage and turning the scroll wheel to go down. So powernowd removal didn't work for me. I guess that's for AMDs anyway? Or processors that can throttle clock speed and voltage.

So... what next? One thing I remember changing, was AGP aperture size from bios. From original 64mb to 32... set to  64 again. (propably doesn't affect)

Guess I'm going to try those acpi/apic disable-thingies I read earlier...

This is SO annoying! Grrr!

-Henrik

---

### Post by harkonen on 2005-11-16
Good news! :)

No more lockups so far... my wife-to-be has been testing this very hard :) and nothing for few days now. The change: I put the AGP aperture back to 64mb from 32mb, and am using the original stock kernel (386) again. Don't know which one did the job, and don't care. ;) Maybe I'll experiment later if I have time and energy...

-Henrik

---

### Post by JordanH on 2005-11-27
I really think the problem is not with power but with Gnome.
[http://www.ubuntuforums.org/showthread.php?t=80704&page=2](http://www.ubuntuforums.org/showthread.php?t=80704&page=2)

Does anyone have any ideas how I can narrow down exactly which piece within Gnome it is that is causing the problem?

---

### Post by Alex1770 on 2005-12-04
Just for the record, I have a clean install of Ubuntu 5.10 on an AMD64. I was experiencing random freezes which would require hard resets, and other glitches which would occur for no apparent reason (though perhaps they were related to processor use). The mean time between crash/glitch was about 15 minutes. Memory checked OK using memtest86. I deinstalled powernowd as suggested above, and now it seems to be running OK. (Crash-free for the last 8 hours, anyway.)

---

### Post by Havoc on 2005-12-05
Hi, I'm one of those crackheads from page 6 that actually got something going.
The only "total" solution I've found for crashes is this:

**Do a:**
> sudo gedit /boot/grub/menu.lst
**from the terminal.**

**Go down, and on the Kernels list, on the kernel line, add these:**

> noapic
nolapic
pci=noacpi

**in order to make it look something like this:**

> title		Ubuntu, kernel 2.6.12-10-686 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-686 root=/dev/hda1 ro quiet noapic nolapic pci=noacpi splash vga=792
initrd		/boot/initrd.img-2.6.12-10-686
savedefault
boot


The disabling of boot services (from BUM or Services in the Administration menu), or selecting a different Kernel does not seem to affect the crashing (Not permanently, at least for me).So, before you touch any of the boot services, try the Kernel comments.Please.

I'm waiting for feedback. :cool: Have a nice day!

---

### Post by Havoc on 2005-12-05
Oh, and as for disabling services, first, download BUM (Boot-up manager, it's in the repositories).

The ones I have disabled are these:

> acpid
apmd
powernowd
acpi-support

I'm out!

---

### Post by GeneW on 2005-12-07
I was having the system lock while the screensaver was running everytime.  I changed the screensaver to just blank the screen and also turned off the power management.  So far it's been running for 9 and half hours without a freeze so one of those must have been causing the freezes.  I have an nvidia 4 system so I might guess that it was an openGL screensaver causing the lockups but I'll have to experiment more to be sure.

---

### Post by Joey French on 2005-12-08
I have tested powernowd under gnome, kde and xfce desktop, and so far, powernowd being installed has coincided with crashes, and after removal, the system has been crash-free. I have repeated this three times now, in all environments. I believe there is something very wrong with powernowd. Or, it just doesn't like my system.

---

### Post by JordanH on 2005-12-11
You're killing me here.  That may have fixed your problem, but it's not helping with mine.  I've tried everything, including the full line above, and I'm still having issues.

Today was slightly different; up until today, the crashes only occured while I was logged into Gnome.  In this case, I was at the ubuntu login, no screen saver, booted under there 686 kernel with options noapic nolapic pci=noapci, powernowd not started at boot, apmd not started at boot.  The computer was serving one SSH connection and one SMB connection.  When I left at 1:30pm all was well.  The clock on the login screen slowed to such a crawl, it didn't make it passed 7:13pm, I returned home at 1:00am...  THe computer just ground to a halt... another 4 hour reboot process.  Holy jumpin.

---

### Post by Joey French on 2005-12-12
Oh, man. That sucks bad. I wish i could help with that, it is frustrating as heck. I was lucky to find that removing powernowd fixed my setup. I started this thread, and I haven't had a crash or lockup in weeks! What about kernels, have you tried all of the ones available to you?

(Thinking of what I've tried in the past...)

---

### Post by ScreaminIke on 2005-12-17
hi.
ok, i found this forum cuz i HATE that i keep locking up... and your problems sound SO much more serious than mine. i actually found awork-around... but i shouldn't need it...
ok
here's my problem, and i think it's gnome-related
when i boot, after i log in, if the first thing i do is NOT run synaptic... whenever i run another app, and begin typing... it locks up. not entirely. but keyboard input is ignored. also, menus HIGHLIGHT, but won't drop. right-click becomes useless. new windows can be generated with point-n-clicks....

i don't know ALL of the keyboard shortcuts... but the only one that works for me is ctrl-alt-backspace. i kill x, and log in, then run synaptic.
that is STUPID... any ideas what is wrong? btw, my account is the only one that does this, but it is the only one that is heavily configged.

---

### Post by TudorB on 2005-12-28
Well, unfortunatelly, it`s back to Windows XP for me. Yep, maybe in april, when the next version of ubuntu will hit the web, I`ll give it another shot, but for now, I just can`t afford the data loses due OS freezes.

---

### Post by maltron on 2006-01-02
Well I hope this thread is still open... this issue has been a real let down for me with regard to Ubuntu.  Here's what I did:

I tried pretty much all the relevant fixes suggested here - noapic, acpi off, remove the powernowd package, change the agp aperture, install a new kernel - nothing worked.  I tried getting on the #ubuntu channel on irc.freenode.net and someone suggested installing the fglrx drivers.  That _sort_ of worked.  Instead of crashing within a few seconds it would work, but the behaviour was a bit shonky - glxgears would freeze occasionally, or would slow down massively when I opened up the xscreensaver preferences (with antinspect as the first screensaver shown, usually).  What's more, if I went into a virtual console and then killed gdm, the machine would now hang if I tried to switch consoles (I'm not sure if it hung if I hadn't killed gdm, but this shouldn't happen anyway - I don't think I've ever managed to properly crash a machine in a non-graphical console before...).   I've never liked the fglrx drivers - I had been using them for a year or so on my debian sarge laptop, and finally decided I was better off without them after several X hangs and crashes and whatnot.  The open source ati drivers may not be perfect, but they don't die randomly, at least.  But one thing came up in this effort which I thought would be worth further exploration.  When you run 

sudo dpkg-reconfigure xserver-xorg 

you get a menu asking you about using the kernel framebuffer device (fbdev) - I thought I'd try different permutations of that and the driver, but alas, it made no difference.  The behaviour of both the fglrx and ati drivers remained unchanged. ](*,) 

Now there should be nothing particularly exotic about the setup I was using - Athlon 1800xp on an Asus A7V266-E motherboard and Gigabyte Radeon 9000 graphics (I can't remember the exact model - it's my brother's computer - but that really shouldn't matter (can find out if necessary)).  From what I've been told that motherboard should be a rock, and I've no reason to suspect it's the graphics card itself as no other OS has had this problem, and that includes other Linux distros (although I have to admit I can't remember for sure whether we ran any opengl on them).  

So what's the next step?  I've been using Debian now for a while and while I'm happy with it it's hard to recommend to new users.  I'd like to recommend Ubuntu for many reasons, one of which is that because it's Debian based it's easy for me to work on and help others with, but if it doesn't work - and that's after trying - what do I do?  Is this something that is likely to be fixed or fixable?  Do any Ubuntu maintainers read this stuff?  Should I file a bug report?

I guess the thing that disappoints me most is that, from all I've heard, the previous version had no such problems.  This feels like a step backwards.  I understand that it's difficult getting these things to happen sometimes, but by the evidence on this forum (and not just this thread) a lot of people have been experiencing exactly the same problem with this particular release.  

I guess it should be self evident that despite these problems I rather like Ubuntu and do want it to work, so I don't mean to come across as too negative, and I do hope that a solution is forthcoming.

---

### Post by Rud on 2006-01-05
Same problem here. I've been running Hoary for almost a year without any lockups whatsoever. I loved Ubuntu for it, because it was the first Linux distro that didn't lockup my IBM T41 laptop (I dumped Gentoo and Yoper due to the lockups). I recently upgraded to Breezy and it's been locking up very frequently. I was getting depressed until I found this post. I stopped powernowd and I really hope this is the cause.

This should be a sticky topic.

---

### Post by moon2js on 2006-01-05
I've read over this thread because I'm having problems with random freezes/lockups. My system is a couple year old Athlon 1200MHz Gateway machine. (I don't know if this matters but I think it uses a lot of VIA components.)

I've tried removing powernowd and disabling screensavers, but the system still locks up randomly. The mouse will sometimes still work but everything, mouseclicks, keystrokes have no effect. But I've found that I can ssh into the system while it's locked up. The problem is I'm a newbie and I really don't know what to do at a terminal to find out what's wrong.

Can anyone explain to me how to look around to find out what's wrong?

I'm wondering if it may be power issues or video card issues. I removed powernowd (freezes unaffected), but I didn't try disabling any further power management stuff (it's a desktop system so it doesn't matter) just yet.

Video-wise, my machine appears to be using "ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE] (prog-if 00 [VGA])." I'm really not sure how to begin googling that in order to find out how it works in Linux, but I did search these boards and didn't find anything to lead me to believe this video card has any known problem. Video works fine on my machine, and I'm not sure using other drivers would improve my stability problem.

Also, I've heard people talk about using older kernels from Hoary, etc. Is that something I should try and if so, how do I do that?

Lastly, here are the last few lines from my /var/log/Xorg.0.log. As I mentioned before, I don't know what I'm looking at or what I'm looking for, but any advice would be greatly appreciated.

```
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0
(EE) RADEON(0): Idle timed out, resetting engine...

```

---

### Post by moon2js on 2006-01-06
Does anyone know if going back to an older version of Ubuntu might work? The random lockups/freezes make the system unusable.

---

### Post by Joey French on 2006-01-06
Just as a point of reference, I have recently reinstalled xubuntu-desktop and with that package, guess what, powernowd was reinstalled. Within minutes, my box crashed. I removed powernowd, no more crashy. 

Just wanted to return to this thread to make the point.

Joey French

---

### Post by moon2js on 2006-01-06
After giving up on Breezy, I installed Hoary on an extra partition and it seemed to worked, but now the random crashes/lockups are here too. As a side note, Samba works beautifully in Hoary and I still can't get it to work in Breezy.

I tried hopefully removing powernowd on both my Breezy and Hoary partitions, but both continue the random lockups. I check the X logs after the lockups and they just trail off in error messages about font rendering. During/after a lockup, I can ssh into the system and do just about anything from terminal (however, I don't know my way around a terminal so I can't do much).

I checked "top" and as far as I can tell, nothing is really hogging up CPU time or appears frozen, but I guess I'm not sure what I'm looking at.

Given that the problem with the lockups is all the input/output devices are unresponsive (monitor, mouse, keyboard), I'm guessing maybe I have a problem with X config? Can anyone who knows more about this stuff give me some feedback or advice?

---

### Post by moon2js on 2006-01-07
In case anyone else searches the forums and wonders what people did, I think I found a solution for my problem [here]("http://ubuntuforums.org/showthread.php?p=569166").

My computer was an older Athlon 1200MHz with an ATI Radeon 7000/VE. The latter turned out to be the issue. Disabling DRI in the xorg.conf ended the random lockups/freezes.

Actually I don't know what DRI is, but the most graphic intensive thing I will ever do with this computer is watch a DVD so I figure I don't need it.

---

### Post by handy on 2006-01-07
Just to comment on a couple of recurring points in this thread, that hopefully will be of some help.

The AMD 64bit CPU's are fully 32bit compatible.

And as far as RAM usage is concerned, it is good to use most of your RAM, it's much  faster than reading from your swap file.

May solutions flood to you.  :rolleyes: 

handy

---

### Post by Red Sand on 2006-01-08
Hi,

well I'm having the same problem (sort of) my new install crashes when I have network traffic (any app). But not always. I can test easy by starting a download, and opening several tabs in ff.... freeze nothing responds (external pings get no reply).
I can listen to mp's, gimp around, but when I start browsing it's just a matter of time before I get a total freeze.
Did the powernowd, no luck.
I have the 2.6.12-10-386 kernel, some suggest that a down- or upgrade will do the trick, any suggestions?
Oh and a weird thing is that during the install I used my nic without any problems after the install was finished I configured my wlan card (Linksys fully Ubuntu compatible) and now I have problems. 
Any suggestions?
Thnx in advance, it would be a great help.
------------------------------
Fixed ;) Tryed everything in this thread..... turned out to be a IRQ conflict

---

### Post by peterthebike on 2006-01-09
I have been following this thread as I also have experienced the dreaded lockups.

Tried removing powernowd, added noapic in GRUB, used BUM to remove acpid apmd. 

None of this made any difference and I was thinking, only thinking mind you, of going back to that other OS supplied on most PCs.:) 

Then I unchecked Power Management Enabled in System>Preferences>Screensaver Advanced tab and I have been free of lockups for 48 hours - at last!!

---

### Post by nocturn on 2006-01-09
What graphic card do you have?

I have an Nvidia and see this behavior with FireFox when RenderAccel is on.  I have read the ATI's driver suffer a similar problem.

If this is your problem, it is not caused by Ubuntu or FireFox, it's a programming error in the closed-source drivers.

---

### Post by peterthebike on 2006-01-09
[QUOTE=nocturn]What graphic card do you have?[/QUOTE]
I have got an Intel 82810E, the standard one that came with my Dell.

---

### Post by Rud on 2006-01-09
[QUOTE=Rud] I stopped powernowd and I really hope this is the cause.
[/QUOTE]

It seems like powernowd was the cause. Since I've stopped it, I haven't had a lockup.  I hope others get this lucky.

---

### Post by pauljwells on 2006-01-14
ubuntu desktop is a metapackage, just a list of other packages needed for some purpose. You can remove it without any worries

---

### Post by rasmusbp on 2006-01-24
Hey,

I've had lots of problems with Breezy crashing on me (ie freezing, so I wasn't able to move the mouse or do anything but shut down manually). The problem stopped when I uninstalled powernowd. A few days ago, however, I installed the linux686 (and all the related headers and stuff), uninstalled the 386, and RE-installed powernowd. And I haven't had any crashes in a few days now! 

So, there might be a problem between linux386 and powernowd?

---

### Post by sudirt on 2006-02-08
I am still having problems on my system with lock - ups. 

At first I used the 386 Kern., Uninstalled powernowd, did the acpi tricks. 

Still had lock-ups.

So because I wanted to improve performance and stability, switched to the 686-smp Kern. because I am running a multi processor machine. So I thought perhaps this would help. Reinstalled Ubuntu and all the power junx. It was much worse for me. Uninstalled all the power restrictions because I am running a server that must run at peak for very extended periods of time. No luck, still get a ton of freezes.

Went back to 386, haven't done much of anything...and it is better...but I will run a program through wine and boom...things go bezerk.

System: PowerEdge 2450, dual procs, plenty ram, no sound *which could cause probs I guess* Running Fibre Channel Q-logic raids as well as an on board scsi raid. all drives and raids are perfect.

Any help is always appreciated.

Sudirt

---

### Post by dmartin on 2006-02-10
[QUOTE=pauljwells]ubuntu desktop is a metapackage, just a list of other packages needed for some purpose. You can remove it without any worries[/QUOTE]

This isn't an entirely true.  Granted, it won't hurt your system in the short term.  But you will lose synch with what the distribution provides.  In a way, ubuntu-desktop *is* Ubuntu.

If you uninstall ubuntu-desktop and the developers decide the ubuntu-desktop metapackage needs to change, you won't get those changes.  Small changes could happen at any time, but I suspect there may be big changes in Dapper's ubuntu-desktop, and you wouldn't get those changes.

For instance, let's say (hypothetically) they decide that Banshee is going to replace Rhythmbox.  You aren't going to get this change.  That one may be obvious and you would know to fix it, but if its something more obscure like a library, you may never realize.

I would recommend installing BUM and deactivating powernowd in BUM, rather than uninstalling powernowd and taking ubuntu-desktop with it.  I hope, given the number of stability problems associated with it, they find a replacement for powernowd or take it out of ubuntu-desktop.  I know this would be unkind to the polar ice caps, so preferably the former.

---

### Post by antiemptyv on 2006-03-14
I was experiencing lockups a few months ago, too.  Annoyed greatly by their frequency, I reinstalled Ubuntu.  I went without crashes for a while.  I figured I had reacquired my stable system.  

Recently, I have begun crashing again.  I thought it might be Gnome, and I started using Openbox with the gnome-panel since this setup is lighter on resources to run.  Still crashed.  Uninstalled Openbox and tried XFCE just for kicks (btw I like it a lot.), and I'm still experiencing crashes.  

The mouse can move, but doesn't bring up the main menu when right-clicking on the desktop.  Sometimes the panel buttons don't respond at all, but sometimes they popup a window saying they can't find whatever they point to...  I can't quote right now; I'm at work.

Anyway, I'm running Ubuntu on a laptop, and I don't feel so comfortable disabling powernowd since it may cause issues for me.

Help?

---

### Post by Joey French on 2006-03-22
Hi, all. Since I started this thread, I have gotten my system sorted out, and it is amazing how stable a properly configured Linux box can be. I have not locked, shutdown, etc... my system in like months, and it's still purring like a kitten. 

For all those still experiencing problems, don't lose hope. When it clicks, it is a fantastic thing.

---

### Post by Mustard on 2006-03-22
I'm not sure how helpful this will be but has anyone tried fiddling with some of the power saving options in their bios as well?

I had a few problems with power saving features when I first started running ubuntu with Hoary and apart from disabling power management within ubuntu itself, I also went into bios and tried various settings relating to power saving, either disabling them or choosing another option until the system became stable.  It was a purely hit and miss approach and I have no idea what some of the bios options do.  I have a Via motherboard btw, running a breezy 386 kernel (K7 kernel did not work well for me), if that ends up being a clue for others with this problem.

---

### Post by blackrim on 2006-03-22
hi all,
my computer also freezes. I have tried the kernel boot line, stopping powernowd service, multiple kernels, multiple nvidia settings, ubuntu, kubuntu, and xubuntu (by the way I settled on xubuntu). 
i can't ssh once the system has frozen. 
where do i go from here?
thanks

---

### Post by Mustard on 2006-03-22
[QUOTE=blackrim]hi all,
my computer also freezes. I have tried the kernel boot line, stopping powernowd service, multiple kernels, multiple nvidia settings, ubuntu, kubuntu, and xubuntu (by the way I settled on xubuntu). 
i can't ssh once the system has frozen. 
where do i go from here?
thanks[/QUOTE]

ACPI settings in BIOS?

---

### Post by blackrim on 2006-03-22
i have tried various things in the bios, but what specifically worked for you? turning off warnings etc? I have an Asus A8n Deluxe with AMD X24800. I have tried the x386 and the k7-smp kernels. 
There seem to be an endless number of enumerable options to try and fix this :)

---

### Post by blackrim on 2006-03-22
is it possible for the problem to be hardware other than RAM? can a fulty power supply cause the machine to freeze without completely shutting off, or is this unlikely?

---

### Post by Mustard on 2006-03-22
[QUOTE=blackrim]i have tried various things in the bios, but what specifically worked for you? turning off warnings etc? I have an Asus A8n Deluxe with AMD X24800. I have tried the x386 and the k7-smp kernels. 
There seem to be an endless number of enumerable options to try and fix this :)[/QUOTE]

I wish I could specifically describe what worked for me.  I had some options for changing values like 'S1' 'S3' on one setting (I have no idea what it does, like so much in BIOS),  I found one that worked, but it was in combination with disabling other things in that particular section of BIOS.  I just kept changing settings till something worked. :)

I suppose the best way would be to change one setting at a time and then try it, so that you could isolate the exact change that worked, but that could be a long and laborious task.  The BIOS controls in different models are so varied its hard to know if we are all looking at the same thing.  I'll have a look again one day when I boot up and see what I have currently.

---

### Post by Mustard on 2006-03-22
[QUOTE=blackrim]is it possible for the problem to be hardware other than RAM? can a fulty power supply cause the machine to freeze without completely shutting off, or is this unlikely?[/QUOTE]

Sure, its possible.  You could check RAM with the memtest in the grub menu at startup.  You can also examine the xorg.0.log or the xorg.0.log.old for error messages too (both found in the /var/log/ directory).  The xorg.0.log.old would probably be the more relevant one, since its the one that was created from the boot just prior to the current boot.

---

### Post by duan on 2006-03-22
Blackrim, 

yes other hardware causes lockups. Most often on cheap motherboards the voltage regulators die over a period of 1 - 3 years. I've seen it happen only a few months after a board was bought. They fail to supply proper power and the mobo does all sorts of weird things, like hanging. On mine, the usb ports would fail to respond.

I had lots of lockups on my machine, then I changed the box and manually placed the fans to cool the motherboard instead of just pumping air through empty space. After  installing adjustable fans I could adjust the ambiend temperature and I could cause my linux box to lock up fairly accurately within 24hrs to a week by adjusting the cooling.

:-) It was a tradeoff between noise and stability...

It is progressively getting worse and it is now in a new box with heap big cooling and the lockups are returning....

---

### Post by blackrim on 2006-03-22
what chance does anyone think I have that a clean debian install will solve this? :) of course this is not meant to insult *buntu (i still run it on the laptop and a desktop), but maybe it is a software (distro) issue? just a guess

---

### Post by Mustard on 2006-03-22
[QUOTE=blackrim]what chance does anyone think I have that a clean debian install will solve this? :) of course this is not meant to insult *buntu (i still run it on the laptop and a desktop), but maybe it is a software (distro) issue? just a guess[/QUOTE]

You should use whatever works for you. :)

---

### Post by bfbay315 on 2006-03-23
blackrim,

I've been trying to a fix this for about a month.

Netvista, 'nough said.. 

 ANYONE USING NETVISTA MACHINES WITH ATI 7000 VIDEO CARDS, get a comfortable chair..

Sorry that was a bit off-topic, but If your'e like me you'll install another distro with a faint hope that it may work.   I tried suse.  I hope this doesnt happen, but You'll likely find that it will have the same symptoms on that disto as well.  

I would try something that isnt debian derived....OR get a new chipset!!  MMMM....maybe I should do that...ahh that would be to easy [http://ubuntuforums.org/images/smilies/icon_smile.gif](http://ubuntuforums.org/images/smilies/icon_smile.gif)

Let me know what you find..

good luck ,
brian

---

### Post by dmizer on 2006-03-23
i have been having this problem constantly with my computer.  but oddly enough, i don't get the lock up with the exact same computer while i'm using it at work.  (actually, that's not entirely true ... i do get lockup from cups on occasion).

the only difference between here and at work is:
1) usb mouse
2) ps2 american english keyboard.

now here, it's important to note that i'm using an older japanese model nec laptop with all the little bells and wistles that go along with an international keyboard including toggles for character switches.

in my dmesg, i was getting loads of junk like this:
```
[4335062.871000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4335063.546000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4335063.546000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4335063.607000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4335063.607000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4335073.996000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4335073.996000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4335074.114000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4335074.114000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
```
but my dmesg did not have these indicators at work. i've performed the fix posted in this thread: [http://ubuntuforums.org/showthread.php?p=669419&posted=1#post669419](http://ubuntuforums.org/showthread.php?p=669419&posted=1#post669419) and i no longer have the errors in my dmesg.  i am also lock up free.

so my question here is ... how many people with this problem are using keyboards with special language specific or location specific functions? also keyboards with programable keys and keyboards with wireless ability are experiencing the above dmesg errors.

i know this has been bouncing around alot, so i just thought i'd pop in here with how i fixed the system locks.

---

### Post by cellarguy on 2006-03-23
I've been using Ubuntu breezy for about a month now.
Really liking it - up till this major crash.

I was using **synaptic manager **to install some *gtk* and *mesa* libraries
for nosing around and/or development.  I had several text files open with **GEDIT **
and a couple of **terminals**, mostly waiting for input, not doing anything fancy.

**Synaptic Manager** cacked out with an error.  I tried to write down the error to
send to you guys, but it was no-go: The entire os went **READ ONLY**,
I tried to load* Firefox,* but apparently you can't get it to open if its read-only.
I even had failures when logging out.  Rebooting was out of the question,
as **GRUB** won't load, and the bios says drive failure.

SO I come to you now from the live CD, wondering if I do indeed have
to reformat and try, try again. You're going to tell me its a drive failure.
But I bet I can reformat and reinstall and all will be well.  But I'm hoping
there is a genius out there who can help in the time it takes me to walk
my dog, so I don't have to lose all my precious-to-me info.

---

