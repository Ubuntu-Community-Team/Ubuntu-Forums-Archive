---
title: "Kubuntu very unstable- unusual crashes"
date: 2005-05-31
forum: Desktop Environments
---

### Post by sb73542 on 2005-05-31
Hello, I have kubuntu on a beige box computer, the most important specs are:
300MHz AMD K6-II
128MB RAM
8MB SiS6326 Onboard video
Opti 82c861 PCI USB
cmi8330 onboard ISAPnp Sound
USR5610B PCI hardmodem

I have all of the above components working well after considerable hacking, the problems arising with USB + Sound + modem concurrently.  But I finally got it working with a few manual modprobe scripts of my own, and the "irqpoll" boot option.

However, Kubuntu crashes CONSTANTLY.  Most of the time, it's not just an X-server crash, as happens frequently in other distros, but instead I completely lose control of the computer.  The monitor "clicks" as it does when X crashes, after which I turn it off and on, as is usually necessary to regain a signal.  But with Kubuntu, it's all over after it goes black.  There are no X error messages or any console output.  I hit Ctl+Alt+Backspace, Ctl+Alt+F-keys, Ctl+Shift+Anything-I-can-lay-my-finger-on, but get absolutely nothing.  So I have to turn off the computer.  And that's it.  I have no idea what's happening.  It does this out of the blue, and with there's no pattern.  Sometimes while browsing with Konqueror, once while opening Kate, clicking the K-menu, doesn't  matter.  Generally I can't work for more than a half hour before the system disappears.  Sometimes more, sometimes less.

I have tried everything from Redhat to Slackware to Mandrake to Debian based distros, and none of them are particularly stable on this computer.  I use my computer for a few hours every night, and then shut it off, but X usually crashes during that period on most distros.  Some are worse than others, makes no different which window manager or desktop I use.  Windows 98 SE occasionally gives me a blue screen, but is generally solid, at least when not under load.  But Kubuntu crashes when doing almost nothing.  The problem is NOT bad memory, as some have suggested, because Windows and one or two rare Linux distros are fairly stable, and I've run Memtest for hours with no problems found.  Any ideas what's going on?  I'd like to use Kubuntu because it looks good and has decent performance and has SUPERB HAL/DBUS settings.  But it's unfortunately unusable.  Thanks for your help!

---

### Post by GTvulse on 2005-06-01
I think you won't like this: Your box is just not good enough for nowadays version of KDE (nor Gnome for that matter). 128 Mb RAM means that they will be slower than molasses. The 8Mb SiS on-board video shouldn't be a problem, though it means that you won't get a higher resolution than 1024x768dpi (and not using more than 16bit color if you want the desktop to be responsive).

Adding more RAM works miracles. I installed Ubuntu in a similar box (an old PC-Chips integrated mainboard with SiS video and C-Media sound chipsets) for a friend of mine last weekend but for one big difference: his has 256 Mb RAM.

Before you give up, try with a light weight desktop. XFCE4 is an excellent desktop that integrates Gnome applications nicely. If you want something lighter, there are WindowMaker and AfterStep for the NeXT look, LiteStep or OpenMotif for that corporate look and from there you can step all your way down to twm, which can be impressively flexible and powerful if you hack it with determination. Fluxbox seems to be the most popular in the "small and beautiful" category if we are to believe in Freshmeat stats.

Cheers

---

### Post by sb73542 on 2005-06-01
I don't mind the performance much, it's definitely fast enough with KDE 3.4, at least by my standards, which aren't very high.  :-)  But this stability problem is absolutely ridiculous, makes Windows ME look stable by comparison.  I dug through the /var/log/ messages immediately after another subsequent crash, and can't find any lucid error messages.  This time the crash dropped me to a console, but I still lost everything I was doing.  Thanks for the help!  And more ideas?

---

### Post by moopere on 2005-06-04
[QUOTE=sb73542]I don't mind the performance much, it's definitely fast enough with KDE 3.4, at least by my standards, which aren't very high.  :-)  But this stability problem is absolutely ridiculous, makes Windows ME look stable by comparison.  I dug through the /var/log/ messages immediately after another subsequent crash, and can't find any lucid error messages.  This time the crash dropped me to a console, but I still lost everything I was doing.  Thanks for the help!  And more ideas?[/QUOTE]


I'm running KDE 3.4 on a 64MB P166 here, so its not memory - 128MB is heaps for KDE 3.4...more is always better of course...more megahertz, more ram, more disk, etc etc etc.

Anyway, I'm running a K6/2 300Mhz on another box here, 128MB EDO, Cirrus 4MB VGA, 40G IDE, a couple of SCSI cards, ISA non PnP SB16, blah blah - no problems at all.  

I'm willing to bet its the driver for the onboard SIS video.  For the longest time SIS did not support either Xfree or Xorg (though someone did a good job of trying to reverse engineer one).  I have a suspicion that that might have changed recently, but the driver is doubtless immature.    Anyway, to prove or disprove the theory, try reconfiguring X to use vesa (or even VGA if you have to) instead of your current driver.

Its gonna be slow, and generally aweful,  however if the crashing stops then you've found your problem.

By the way, if you are serious about almost all linux distro's crashing,  as well as nightly crashes under Windows, you might be facing the grim reality of a foobar motherboard or somesuch.

Cheers,
Craig

---

### Post by bailout on 2005-06-04
It could be faulty memory. Run memtest86 and see if you get any errors.

---

### Post by funduk on 2005-06-04
[QUOTE=bailout]It could be faulty memory. Run memtest86 and see if you get any errors.[/QUOTE]
 He just said that he has run memtest though.

But you might still have bad memory, in my experience memtest doesn't do jack. Run something more robust like GoldMemory or even that new microsoft memory tester (comes as iso and you boot up off the cd), they both work well. Never trust only 1 memory testing app!

---

### Post by sb73542 on 2005-06-08
Thanks for the help!  Good suggestions re: the memory test, but even before running more tests I'm pretty sure that hardware is not the problem.  Why would Windows and virtually every other Linux distro be more stable on the same hardware?  I also suspect that the SiS video driver is at fault for the crashes in all Linux distros I've tried, but why does Kubuntu crash so much more than others?  I have checked the xorg.conf driver options of Kubuntu with the XF86Config-4 settings provided by MEPIS (which is more stable), and they appear to be the same.  Xorg vs. XF86 does not seem to make a difference either.

Unfortunately, VESA support with SiS6326 is almost non-existent.  I have used it (by force) with DSL, which gives me 640x480 resolution with about eight ( 8 ) colors.  Unusable.  But then again, it never crashed..... :-)

 Any more ideas on what to check?  Thanks a lot for your help!

---

### Post by dejitarob on 2005-06-08
Try KDE 3.4.1, it contains various crash fixes.
[http://ubuntuforums.org/showpost.php?p=194076&postcount=10](http://ubuntuforums.org/showpost.php?p=194076&postcount=10)

---

### Post by sb73542 on 2005-06-08
[QUOTE=dejitarob]Try KDE 3.4.1, it contains various crash fixes.
[http://ubuntuforums.org/showpost.php?p=194076&postcount=10](http://ubuntuforums.org/showpost.php?p=194076&postcount=10)[/QUOTE]
 Thanks!  How can I differentiate a KDE crash from an X server crash?

---

### Post by zAo on 2005-06-09
[QUOTE=sb73542]Thanks!  How can I differentiate a KDE crash from an X server crash?[/QUOTE]
I stopped using Kubuntu for the same problem. I ran it on a AMD 2100+, 1GB RAM, ATI 9600 Pro 128MB, 320GB disk. When I use Gnome, there are no crashes. 
I checked every logfile after a crash; none gave me info.

---

### Post by sb73542 on 2005-06-09
Huh, maybe its been KDE all this time.  Although it seems to me that I've had a small number of crashes when using Icewm under Vector Linux.    When KDE crashes, can it bring down X with it?  I'm positive that my X server is crashing on Ubuntu, because my monitor looses the signal somtimes permanently, or sometimes until I reset it.  I thought that if KDE is crashing, it would just quietly quit working, or possibly bring up the KDE crash handler.  I have noticed in most distros that parts of KDE will rather frequently crash such as kicker, kwin, and kdeskop.

---

### Post by moopere on 2005-06-09
[QUOTE=sb73542]Thanks for the help!  Good suggestions re: the memory test, but even before running more tests I'm pretty sure that hardware is not the problem.  Why would Windows and virtually every other Linux distro be more stable on the same hardware?  I also suspect that the SiS video driver is at fault for the crashes in all Linux distros I've tried, but why does Kubuntu crash so much more than others?  I have checked the xorg.conf driver options of Kubuntu with the XF86Config-4 settings provided by MEPIS (which is more stable), and they appear to be the same.  Xorg vs. XF86 does not seem to make a difference either.

Unfortunately, VESA support with SiS6326 is almost non-existent.  I have used it (by force) with DSL, which gives me 640x480 resolution with about eight ( 8 ) colors.  Unusable.  But then again, it never crashed..... :-)

 Any more ideas on what to check?  Thanks a lot for your help![/QUOTE]


I have had every sort of pain using onboard SIS video....even under Windows.

You have already found your answer I suspect...from your post above "But then again, it never crashed..."

If its not crashing in VGA/VESA, then its either the hardware is faulty or the driver is glitching on you.

I'd suggest marginal hardware.  I found WinNT4 crashed constantly using onboard SIS video until I slowed the RAM speed down in the BIOS (uses shared RAM right?)

Its not the RAM thats bad, its something funny with the video/chipset/motherboard.  Never ever, on any SIS based board did checking the memory with a memory 'checker' program find an error - but under load, using Win2K/NT4 or Linux it would explode every time.

You could try to get another VGA card, or, probably close to the same price, get a decent 2nd hand (maybe even new) motherboard to put your CPU and Memory in.

I wouldn't bother for too long trying to find out why it crashes a bit under Windows, a bit more under Linux's and a bit more still under Ubuntu....if its crashing then there is something wrong and I'd suggest that the big variation in test software you are using (different linux's and Wins) are telling you that you have a hardware fault.

Cheers,
Craig

---

### Post by sb73542 on 2005-06-09
Yup, that makes sense moopere, thanks.  I have an IBM Thinkpad that I use every day which is currently running Hoary w/ XFCE.  But I liked Kubuntu so much (aside from the crashing) that I'd like to use it on my laptop.  I use the other desktop computer in question as a testbed, and I was sort of concerned that Kubuntu might be a total disaster on most systems.  How stable is it for you guys?  How about individual KDE components crashing?  In other words, can one get work done on Kubuntu?  Thanks for the help again.

---

### Post by ltmon on 2005-06-09
I'm running Kubuntu on nice (i.e. high quality, not-overclocked, not latest-greatest) hardware and have only ever seen the occasional crash from Kaffeine (which doesn't bring anything else down) and Enemy Territory (which hangs X, but can be recovered from by killing the ET pid).

So from my experience, there are no stability issues with Kubuntu :)

L.

---

### Post by meldroc on 2005-06-10
[QUOTE=sb73542]Thanks!  How can I differentiate a KDE crash from an X server crash?[/QUOTE]
 I've found that when something KDE-related crashes, it doesn't usually bring down the whole X server, though it is possible.  Usually, if something KDE-related does crash, it just brings down one app, or if it's something important like kicker or the window manager, it'll crash, then immediately restart itself.  Worst case, it'll cause X to reset, dumping you either at your console or the kdm login screen.

I'm thinking it's a low-level issue, maybe with X drivers.  Though KDE may be aggravating it.  KDE pushes your typical X server a little harder than more lightweight environments like xfce, so it may cause conditions that cause X to crash more often.  Or it could be hardware related.  You've already run memtest, maybe you have a flaky video card.

---

