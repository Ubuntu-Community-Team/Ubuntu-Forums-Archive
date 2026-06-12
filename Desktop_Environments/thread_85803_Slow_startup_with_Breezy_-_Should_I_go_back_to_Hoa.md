---
title: "Slow startup with Breezy - Should I go back to Hoary?"
date: 2005-11-03
forum: Desktop Environments
---

### Post by bhishma on 2005-11-03
I'm using Breezy on my Fujitsu P2120 laptop (Transmeta Crusoe 933MHz CPU / 256MB RAM). It is no workhorse, but Windows XP boots up in 2 minutes, and Hoary booted up in around 4 minutes.

I installed Breezy anew after deleting the partitions for Hoary. But not only did Breezy take much longer to install, it is also taking much longer to boot. I need to wait more than 7 minutes to see the GNOME desktop.

I've searched the forum, and apparently many people believe that the clock synchronization is probably the culprit for a slow startup. But in my case, this is not true. It takes around 2 minutes for "Creating initial device nodes", and it takes another 2 minutes for "Starting hotplug subsystem". The clock synchronization, in comparison, takes very little time.

To me, it seems that Breezy is just taking too much time looking for all kinds of hardware that doesn't exist on my system.

Hoary, although it didn't handle hibernation properly, correctly detected all the hardware that I actually use (Wireless LAN, trackpoint, and USB). And while definitely slower than Windows XP, Hoary was a pleasure to use.

Now, here's my question:

Is there a way to decrease the Breezy startup time to the Hoary level? Or would it take so much effort that I'm better off going back to Hoary?

---

### Post by mlomker on 2005-11-03
I'd probably go back to Hoary or leave the machine running if I were you.  There's no doubt that the boot times took a significant turn for the worse in Breezy.

Have you considered compiling a custom kernel with only the things that you need?  I'm not sure how technical you are, but that would at least reduce the hotplug times.

---

### Post by Xian on 2005-11-03
[QUOTE=bhishma]It takes around 2 minutes for "Creating initial device nodes", and it takes another 2 minutes for "Starting hotplug subsystem". The clock synchronization, in comparison, takes very little time.

To me, it seems that Breezy is just taking too much time looking for all kinds of hardware that doesn't exist on my system.[/QUOTE]
That is an insane amount of time to boot. My Ubuntu 5.10 box is up and at the Gnome Desktop in well under two minutes. You really should file a [Bug Report](http://bugzilla.ubuntu.com/) and include all your hardware specs so that this can be investigated.

---

### Post by mlomker on 2005-11-03
[QUOTE=Xian]That is an insane amount of time to boot.[/QUOTE]

A 900 mhz Transmeta is not a barn-burner.  I have an older IBM 240x that takes about the same time to boot.

---

### Post by Xian on 2005-11-03
[QUOTE=mlomker]A 900 mhz Transmeta is not a barn-burner.[/QUOTE]
Granted, but this should not result in a +7 minute boot time.

---

### Post by mcduck on 2005-11-03
[QUOTE=mlomker]A 900 mhz Transmeta is not a barn-burner. I have an older IBM 240x that takes about the same time to boot.
[/QUOTE]
I have one AMD-K6-2 @ 500MHz, with 128MB of ram and even _that_ boots Breezy in less than 4 minutes to Gnome desktop. With a 7 minutes boot time there sure is something wrong..

---

### Post by mlomker on 2005-11-03
> With a 7 minutes boot time there sure is something wrong..

They can file a bugzilla, then.  I've never timed my older machines.  That's usually when I get coffee.

---

### Post by bhishma on 2005-11-03
[QUOTE=mlomker]Have you considered compiling a custom kernel with only the things that you need?  I'm not sure how technical you are, but that would at least reduce the hotplug times.[/QUOTE]

I'm pretty much a newbie, and I think I need a few more months before even thinking about compiling a custom kernel. ;)

---

### Post by bhishma on 2005-11-03
[QUOTE=mcduck]I have one AMD-K6-2 500MHz, with 128MB of ram and even _that_ boots Breezy in less than 4 minutes to Gnome desktop. With a 7 minutes boot time there sure is something wrong..[/QUOTE]

I'm quite sure that the AMD-K6-2 @ 500MHz can actually outperform a Crusoe 933MHz. Trust me. A Transmeta Crusoe is a painfully slow chip. :???: Also, it's a laptop that I'm talking about. Since the hardware deviates somewhat from the "mainstream" desktop, I do expect somethings to be far from optimized.

I'm not so sure that I should file a bug report, since I don't see any error messages and Breezy does boot correctly if I just wait long enough.

But I do know another post complaining about a slow Breezy startup.

[http://ubuntuforums.org/showthread.php?t=84485&highlight=creating+initial+device+nodes]("http://ubuntuforums.org/showthread.php?t=84485&highlight=creating+initial+device+nodes")

This guy has a very fast system, and yet he is also suffering from the steps "creating initial device nodes" and "starting hotplug subsystem" taking a lot of time to complete.


At the moment, I'm really thinking seriously about going back to Hoary. It took me less than 2 hours to install Hoary, compared to Breezy's 5, and so it should be a less painful process. ;)

---

### Post by Xian on 2005-11-03
[QUOTE=bhishma]I'm not so sure that I should file a bug report, since I don't see any error messages and Breezy does boot correctly if I just wait long enough.[/QUOTE]
You are of course welcome to do as you wish. However, let me just point out that it would be improper to surmise that the lack of an error message means there is not a problem. In fact, the majority of issues that desktop users encounter do not have an error output whatsoever. The core of the matter here is that Breezy takes nearly twice as long to boot as did Hoary on the same machine. That is a definite issue no matter what your hardware configuration.

---

### Post by bhishma on 2005-11-04
[QUOTE=Xian]In fact, the majority of issues that desktop users encounter do not have an error output whatsoever. The core of the matter here is that Breezy takes nearly twice as long to boot as did Hoary on the same machine. That is a definite issue no matter what your hardware configuration.[/QUOTE]

Thanks for your input. I'll try to file a bug report then.

At least I'm somewhat relieved to see that I'm not the only one who feels that Breezy takes longer than Hoary to boot up.

---

### Post by mlomker on 2005-11-04
> The core of the matter here is that Breezy takes nearly twice as long to boot as did Hoary on the same machine. That is a definite issue no matter what your hardware configuration.

Twice as long is pretty tough to deal with.  I'd say that all of my Breezy machines take 50% longer to boot.

---

### Post by bhishma on 2005-11-04
[QUOTE=mlomker]Twice as long is pretty tough to deal with.  I'd say that all of my Breezy machines take 50% longer to boot.[/QUOTE]

Why is that? Why does Breezy need more time than Hoary to boot?

Now I'm starting to worry that Dapper Drake might be even slower! :confused:

I filed a bug report, BTW.
[http://bugzilla.ubuntu.com/show_bug.cgi?id=18891]("http://bugzilla.ubuntu.com/show_bug.cgi?id=18891")

---

### Post by mlomker on 2005-11-04
> Now I'm starting to worry that Dapper Drake might be even slower! :confused:


I don't know.  It might be trying to detect a wider variety of hardware or it might be a byproduct of the graphical bootscreen (usplash).

---

### Post by bhishma on 2005-11-04
[QUOTE=mlomker]I don't know.  It might be trying to detect a wider variety of hardware or it might be a byproduct of the graphical bootscreen (usplash).[/QUOTE]

I'm not sure if it's relevant, but in fact my Breezy exits the graphical bootscreen at the "creating initial device nodes" stage and continues on with the plain terminal bootscreen.

---

### Post by bhishma on 2005-11-06
I finally deleted the Breezy partitions and installed Hoary.

Hoary indeed boots much much faster than Breezy, and it takes around 4 minutes until the GNOME desktop + all the applets in the panel are loaded.

---

### Post by Swifty on 2005-11-06
Usplash produces a negligible bootup difference, in fact, none at all because the services are continuing to start in the background.

I too have an extremely slow startup when it gets to the "Starting hotplug subsystem" and i've targetted the problem, it is **when my epson scanner is plugged in** (Which, by the way, works perfectly in Linux)

---

### Post by bhishma on 2005-11-07
[QUOTE=Swifty]I too have an extremely slow startup when it gets to the "Starting hotplug subsystem" and i've targetted the problem, it is **when my epson scanner is plugged in** (Which, by the way, works perfectly in Linux)[/QUOTE]

Interesting. In my case, I didn't have any external hardware plugged in. However, the modular combo optical drive is a hot swap device, and maybe that's the reason why Breezy stalled. Well, no way to find out now. :)

---

### Post by sevenrechlin on 2005-11-09
I'm having the same slow startup problem here.  Running a pentium 4, 2.8ghz.  WinXP takes about 45 seconds to load, and Breezy takes about 10 minutes (seriously).  It also took a very long time to install...

---

### Post by Juzz on 2005-11-09
Weird - I have actually experienced a shorter bootup when I switched to Breezy.

I have a netcard builtin in my mb, but no wire plugged in - since I am using a wireless configuration at home.

I think that the point that speeded up a lot is the point where it tries to probe my netcards.

---

### Post by bhishma on 2005-11-10
[QUOTE=sevenrechlin]I'm having the same slow startup problem here.  Running a pentium 4, 2.8ghz.  WinXP takes about 45 seconds to load, and Breezy takes about 10 minutes (seriously).  It also took a very long time to install...[/QUOTE]

Ouch. I feel for you.

So I guess the problem is not really related to the CPU. And since there are people like Juzz who are not suffering from the slow startup, I guess Breezy is particularly bad at detecting and loading some specific hardware, for example the Epson scanner mentioned by Swifty.

sevenrechlin, what kind of system do you have? Do you have any hardware inside or connected to the computer that's a bit uncommon?

I have a hunch that in my case it could have been the hot-swappable optical combo(CD Read/Write, DVD Read) drive. I read somewhere that in Hoary the system would halt if you pulled out the drive while the system is running. I never tried it myself with Hoary, but in WinXP, you can do "safely remove blah blah blah" and then really pull it out. Maybe Breezy supports hotswapping as well, or at least is trying to, and in the process bogs down the startup.

Hmm... I should have tried starting up with the optical drive detached. But now I have a Hoary running beautifully, and I'm really reluctant to go through the 5-hour Breezy installation to check that out.

But when I get home, I'll find out the exact optical device product name and post it here.

---

### Post by antwerx on 2005-11-10
[quote=Swifty]Usplash produces a negligible bootup difference, in fact, none at all because the services are continuing to start in the background.

I too have an extremely slow startup when it gets to the "Starting hotplug subsystem" and i've targetted the problem, it is **when my epson scanner is plugged in** (Which, by the way, works perfectly in Linux)[/quote]

My Breezy stalls a the same place as noted by Swifty, only when my Netgear wireless card is inserted. Remove the card or ctrl-c past 'Starting hotplug subsystem' and my laptop starts up in a normal amount of time.

Steve

---

### Post by wrtrdood on 2005-11-10
[QUOTE=bhishma]

Hmm... I should have tried starting up with the optical drive detached. But now I have a Hoary running beautifully, and I'm really reluctant to go through the 5-hour Breezy installation to check that out.
[/QUOTE]

I doubt it would make any difference.  I'm running Breezy on a Fuji P1120 and I get the same results you reported and at the same places.  I think my boot time might actually be a bit longer but I've not timed it.  Hoary was a good deal faster at boot and under use.  It doesn't seem to take much to bog it down, either.  Get a few apps going and the processor is pegged all the time.  I plan to build a custom kernel (probably this weekend) to see if I can streamline this puppy a bit and I'll let you know my results.

It's a good thing the suspend/resume cycle works flawlessly, though.  There's no way I could handle having to boot each time given the way it works now.

---

### Post by bhishma on 2005-11-10
[QUOTE=wrtrdood]I doubt it would make any difference.  I'm running Breezy on a Fuji P1120 and I get the same results you reported and at the same places.  I think my boot time might actually be a bit longer but I've not timed it.[/QUOTE]

Wow! A fellow P-series user! :) So did you already try booting with the optical drive removed?

I tried removing the optical drive while Hoary was running. The system just paused for a second and then went on just fine. I inserted the optical drive back in, and I could read from the device again without a problem. So apparently, "hot-swapping" is supported in Hoary, and thus it may not be what's causing the slow startup.

> Hoary was a good deal faster at boot and under use.  It doesn't seem to take much to bog it down, either.  Get a few apps going and the processor is pegged all the time.  I plan to build a custom kernel (probably this weekend) to see if I can streamline this puppy a bit and I'll let you know my results.

Great! I am really interested to know how much performance gain a custom kernel can bring on.

> It's a good thing the suspend/resume cycle works flawlessly, though.  There's no way I could handle having to boot each time given the way it works now.

Actually, I think the suspend/resume also works with Hoary now. I can now suspend to RAM or disk, and come back without any errors. The audio is fine on resume, and I just need to press Fn-F4 to reactivate the track point.

Coming back from hibernation breaks the wirelss connection, but doing suspend/resume fixes it.

Anyway, I would also prefer to use Breezy, if it wasn't for the slow startup. I really hope that the problem gets fixed.

---

### Post by sevenrechlin on 2005-11-10
Well the only things I have hooked to my computer are my printer, mouse/keyboard etc, and a network cable going to my router. Oh, and my speakers are hooked up but that's all.  I think the problem is somewhere in my HD, but guess I'll find out soon... Just bought a new 120gb HD since it was really cheap (is that going overboard?) :p.

Also, Ubuntu runs extremely slow once booted up as well, sometimes freezes for 5 minutes???  It's crazy.

---

### Post by bhishma on 2005-11-11
[QUOTE=sevenrechlin]Well the only things I have hooked to my computer are my printer, mouse/keyboard etc, and a network cable going to my router. Oh, and my speakers are hooked up but that's all.  I think the problem is somewhere in my HD, but guess I'll find out soon... Just bought a new 120gb HD since it was really cheap (is that going overboard?) :p.

Also, Ubuntu runs extremely slow once booted up as well, sometimes freezes for 5 minutes???  It's crazy.[/QUOTE]

Could you try booting with the printer unplugged and give us the results?

For me, breezy worked well once after it booted up -- maybe slightly slower than hoary, but not by much.

Congrats on your new hd. wow. 120gb! I guess you have to install breezy anew? But is there any reason to believe that your current HD is not working well with breezy?

---

### Post by sevenrechlin on 2005-11-11
Well my old HD was from a really old computer of mine that was having problems when I "dumped" it.  Wasn't ever sure what the problem with it was, though I was pretty sure at the time it had something to do with the computer itself, and not the hard drive.
But anyways, installed my new hard drive and everything is running perfectly.  So...  Either it really was a piece of junk, or had something extremely wrong with the install, but I'm leaning towards the first.
Oh well though, it's all over now and I can finally really try out Ubuntu :).  Thanks for all the support along the way so far everyone!

EDIT: BTW, also have a load time of about 30 seconds until I can get in and do stuff on Ubuntu, which is a great improvement to WinXP!

---

### Post by wrtrdood on 2005-11-11
[QUOTE=bhishma]Wow! A fellow P-series user! :) So did you already try booting with the optical drive removed?
[/QUOTE]
  Yup.  Love my P. :D

   Well, see, that's just it.  The 1000 series has no internal drive.  I never had one attached (except to install the OS).

[QUOTE=bhishma]
Great! I am really interested to know how much performance gain a custom kernel can bring on.
[/QUOTE]
  You'll be very happy to know that it affords a significant boost in performance.  I'm still tweaking it some and it's possible that the 2.6.14 kernel itself offers some improvements as well.  Big improvement.  Though I've not timed it, I would say that it takes less than 3 minutes.

Actual time = 2.5 minutes to boot (from grub menu), 1.5 minutes to login

[QUOTE=bhishma]
Actually, I think the suspend/resume also works with Hoary now. I can now suspend to RAM or disk, and come back without any errors. The audio is fine on resume, and I just need to press Fn-F4 to reactivate the track point.

Coming back from hibernation breaks the wirelss connection, but doing suspend/resume fixes it.

Anyway, I would also prefer to use Breezy, if it wasn't for the slow startup. I really hope that the problem gets fixed.[/QUOTE]

Yeah, I had it working under Hoary and had the same problems.  I solved the wireless problem by removing orinoco_pci and adding it back.

I'll tune up this kernel build some more and find a way to post it some place for others having this problem on a Lifebook P series.

---

### Post by bhishma on 2005-11-12
[QUOTE=wrtrdood]I'll tune up this kernel build some more and find a way to post it some place for others having this problem on a Lifebook P series.[/QUOTE]

Fantastic. Please leave a note here as well. Also, please do make the howto newbie-friendly. :)

---

### Post by wrtrdood on 2005-11-14
Actually, there's a HOWTO already written:

[http://www.ubuntuforums.org/showthread.php?t=84174&highlight=2.6.14](http://www.ubuntuforums.org/showthread.php?t=84174&highlight=2.6.14)

Follow it and you'll have what I have (mind you this take a while to build though...)

---

### Post by ian-johnson on 2005-11-17
I had the same problem with a very slow boot.  It was stuck booting the networking portion of the boot.  I searched the wiki and found a method of changing some text in a text file and now my laptop boots in less than a minute...faster than booting into windows.  My suggestion is to keep looking for a solution.  Sorry I don't remember the details.

---

