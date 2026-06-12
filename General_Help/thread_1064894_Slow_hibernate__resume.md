---
title: "Slow hibernate / resume"
date: 2009-02-09
forum: General Help
---

### Post by Aaron44126 on 2009-02-09
Disclaimer:  I don't use "Suspend" because it does not work reliably on my machine.  Hibernate works... except for this.

Anyone know of a way to make hibernate faster?  The machine takes about 5 minutes to shut down and then about 5 minutes to boot to a usable state when using hibernate.  It is at least twice as fast to just shut the machine down and boot it from scratch.  But then, I don't get to keep my running applications.

I don't really mind the slow shutdown, it's the slow resume that kills me.  While it's resuming, there is just a blinking cursor and lots of disk activity.  It eventually pops back to the locked desktop and I can move the mouse around, but it is another minute or so of just a lot of disk activity before I can unlock the desktop and do anything.  And even for the first minute or so after I am using the machine, the disk is going crazy, as if it is still paging stuff back in.

I know it can be faster because...
 - Windows on the same machine restores from hibernate into a perfectly usable state in about 1 minute.
 - I tried using uswsusp and it's also much, much faster (1-1.5 minutes).  But I don't want to just use that because it fails to hibernate every now and then, seemingly randomly, and I lose my running stuff.

So, I was wondering if anyone knew of an easy way to speed this up (using Ubuntu's default pm-utils and not uswsusp).  I know that speed in this area is a major focus for Ubuntu 9.04 so I am hopeful that at least then I will see this problem resolved.

Thanks for any insights!

---

### Post by LowSky on 2009-02-09
what applications are you running when you are using hibernate?

---

### Post by Aaron44126 on 2009-02-09
My typical application space includes something like...

 - Thunderbird
 - Firefox
 - Gedit (several)
 - MonoDevelop (several)
 - Terminal (several)
 - Rhythmbox
 - F-spot
 - NX client
 - OpenOffice (maybe)

Yeah, it seems like a lot.  I rely on hibernate because I often leave applications running for a long time, spread out across several workspaces.  It's a lot of applications but none of them are particularly disk intensive, and I don't see a lot of disk activity when I am just using the machine regularly.

---

### Post by gardkenn on 2009-02-11
I have the same problem and I first thought it was the applications I was running. So I tested and found out that I can start the computer then immediately hibernate it and the result is the same. It can take anywhere between 5 to 10 minutes waiting for the system to come back on line. 

This really is the pits too. I love linux, but in the past few months I am finding myself increasingly mobile and there is so many times I just want to shut the dang lid and come back later to a full desktop.

---

### Post by mozg on 2009-02-12
Hi

I am having similar issues with slow resuming. I don't get this as slow as you guys - about 3-4 minutes or so. However, what I tend to find is that a big part of of that time, the computer sits there without doing any visible activity. Over a minute, it sits with a blank screen without any hard disk activity. Once the hard disk activity starts, it takes about a minute to get the login prompt and another 10-30 seconds for laptop to become properly responsive when I can start entering my password. I am using T61p Thinkpad with 4Gb of ram; 7.2k rpm hard disk.

Andrei

---

### Post by mozg on 2009-02-12
Actually, just did a few tests with the following results:

To hibername: 58 seconds
To resume: 3m 55 seconds

out of which, just over a minute laptop was doing nothing visible (no activity on HD, even the screen backlight was off.

2minutes and 20 seconds after the boot, the X came on and I could move the mouse. From that point on, the HD activity was on (about minute and a half) until the login screen appeared.

Andrei

---

### Post by bryncoles on 2009-02-13
i notice this too. there must be a way to speed up resume from hibernation?

---

### Post by vi3dr0 on 2009-04-20
I've got exactly the same problem as *mozg* - Thinkpad t61p, 4 gigs of RAM, 7,2k rpm - when resuming there is nothing happening for over a minute - blank screen, no hdd activity. 

:popcorn:

---

### Post by Aaron44126 on 2009-04-20
I know in my first post, I specified that I did not want to use uswsusp.  However, I tried it again and it seems to be working very reliably now (and faster than Ubuntu's default pm-utils).  I think the problem that caused intermittent failures with it before was actually the video card driver...  I recommend, if you have an NVIDIA card, you use a later 180.xx version of the driver.  You can either get this from NVIDIA's web site, or manually download and install the nvidia-glx-180 package and dependencies from *jaunty*'s repositories (the one in the intrepid repositories is a beta version and I had other problems with it).


Here's my solution to this problem.

First, install uswsusp.  (sudo apt-get install uswsusp)
The version in Intrepid is pretty old, but it might work for you.  It's been updated in Jaunty (I'm using the RC at the moment).  Works fine for me in both.

After you install uswsusp, you need to tell Ubuntu to use it as the default hibernate mechanism.  To do this, open /etc/pm/config.d/00sleep_module in your favorite text editor, uncomment the bottom line, and set it to uswsusp.

SLEEP_MODULE="uswsusp"

Now try hibernating and resuming and see if it is any faster for you!

[Edit]
Note:  In intrepid, sometimes the system would fail to power off after the RAM image was written to disk while hibernating.  After forcing a power off (by holding down the power button), it would still boot up and resume fine.  This hasn't happened to me so far in jaunty...

---

### Post by morpheus01 on 2009-05-17
Good to hear your issue has been resolved Aaron. 

I'd just like to add my name to the above list of posters that have the slow hibernate/resume issues. Not sure if I should post here, but I didn&#8217;t find anywhere else after some quick searches.

Ubuntu
Start from Shutdown
     1 minute 25 seconds
Start From Hibernate
     1 minute 25 seconds

Windows
Start From Shutdown (I don't have many apps running at boot up)
     1 minute 10 seconds
Start From Hibernate
     20 seconds

Pity about this as it makes Ubuntu unfeasible for bunch of users with Windows partitions. It's just not worth rebooting and shutting down to look up something quickly... I don't have a lot of performance coding experience but where would we need to look for a fix for this?

---

### Post by JohnnyRogers on 2009-06-18
> **Aaron44126 said:**
> Here's my solution to this problem.

First, install uswsusp.  (sudo apt-get install uswsusp)
The version in Intrepid is pretty old, but it might work for you.  It's been updated in Jaunty (I'm using the RC at the moment).  Works fine for me in both.

After you install uswsusp, you need to tell Ubuntu to use it as the default hibernate mechanism.  To do this, open /etc/pm/config.d/00sleep_module in your favorite text editor, uncomment the bottom line, and set it to uswsusp.

SLEEP_MODULE="uswsusp"

Now try hibernating and resuming and see if it is any faster for you!



This worked perfectly for me, and instead of waiting over a minute to wake up from suspend (making a shutdown/reboot faster) it comes up in just a few seconds. Thanks!:D

---

### Post by davearter on 2009-07-15
Installing uswsusp and tweaking the SLEEP_MODULE line worked for me on my Dell Precision M4400. Hibernate takes about a minute, resume about the same. Thanks!

---

### Post by ManDay on 2009-09-13
I've come across the same problem, although I've far more acceptable times as-is. Going into Hibernate takes a pair and a split seconds but bringing it back online takes about 50 seconds - which is barely anything compared to your times, but still a lot considering my normal boot time, which is about 50 seconds, too. Mind, however, that this is on a very very slim installation with absolutly none but X11 and the most essential programs/daemons running.

I'll try your solution now, wonder though what causes the problem.

---

### Post by ManDay on 2009-09-13
I've followed your instructions to install uswsusp and could enable it properly. While the time to suspend to disk **increased** from a few (three to five) seconds to 15 seconds, the time to resume remains **unchanged**.

Upon resume, the uswsusp module passes from 0% through 100% in a few seconds but as it finishes and operation should resume, I get a black screen with a blinking cursor for the remaining time of the 48 seconds.

I therefore assume that this is not providing any solution - at least not to me - and you too could get better results.

Please help :confused:

---

### Post by ManDay on 2009-09-13
I've measured the following times, taken from initialization of kinit to arriving on the desktop:

**Coldstart**
42s

**Kernel module**
Many programs: 17s / 51s
No programs: 10s/50s

**USWSusp module**
Many programs: 17s/10 + 36s
No programs: 11s/4 + 39s

The sum for the USWSusp module indicates the time taken to load the memory from disk + the time spent on the said black screen.

---

### Post by ManDay on 2009-09-14
I managed to speed it up to a decent few seconds. Going troug dmesg I noticed the major gap (in the black screen) being just before an USB related line.


[  397... ] ...
[color=red][b][  397... ] PM: Basic memory bitmaps freed
[  430... ] usb 1-5: reset high speed USB device using ehci_hcd and address 3[/b][/color]
[  430... ]

Unplugging the only USB-device I was using at that moment, being my mouse, the gap vanished and there was no more error. However, having found the cause, I still don't know how to solve it. Please help.

---

### Post by seamles on 2009-09-15
Is there a less invasive way to fix this problem?

---

### Post by bilderbuchi on 2009-11-04
i'd be interested in a less invasive solution, too.

---

### Post by Quake on 2009-12-18
Sorry to resurrect this thread but... but THANK YOU AARON! uswsusp is wonderful, it now takes a couple of second to resume Linux from hibernation rather than minutes.

THANK YOU! This should be a sticky.

---

### Post by nortexoid on 2010-06-25
> **Aaron44126 said:**
> 
Here's my solution to this problem.

First, install uswsusp.  (sudo apt-get install uswsusp)
The version in Intrepid is pretty old, but it might work for you.  It's been updated in Jaunty (I'm using the RC at the moment).  Works fine for me in both.

After you install uswsusp, you need to tell Ubuntu to use it as the default hibernate mechanism.  To do this, open /etc/pm/config.d/00sleep_module in your favorite text editor, uncomment the bottom line, and set it to uswsusp.

SLEEP_MODULE="uswsusp"


The folder /etc/pm/config.d/ is empty in my Kubuntu 10.04 install. Is it possible to paste the contents of yours here and then for me to use that?

---

### Post by fatmcgav on 2010-07-04
What can i say... Thanks a bucket for this suggestion... 

Has cut my resume time from circa 5mins to circa 30seconds... Finally i can use my laptop again :) 

Cheers
Gavin

---

### Post by fishtron on 2010-07-13
> **nortexoid said:**
> The folder /etc/pm/config.d/ is empty

I have only one file in there, called 00sleep_module

This is the file's contents:

```
# The sleep/wake system to use.  Valid values are:
#   kernel    The built-in kernel suspend/resume support.
#             Use this if nothing else is supported on your system.
#   uswsusp   If your system has support for the userspace
#             suspend programs (s2ram/s2disk/s2both), then use this.
#   tuxonice  If your system has support for tuxonice, use this.
#
# The system defaults to "kernel" if this is commented out.
# SLEEP_MODULE="kernel"
SLEEP_MODULE="uswsusp"
```

You might have to install uswsusp first, though.

---

### Post by catalin.hritcu on 2011-02-09
Aaron44126's solution does provide a noticeable improvement in the starting times on my Dell Latitude E6400.

**kernel**:
suspend : 2min39sec
resume: 2min:26sec

**uswsusp**
suspend : 2min13sec (26sec improvement)
resume : 1min32sec (54sec improvement)

*The times are for Ubuntu 11.04 - Natty Narwhal with a ton of applications running, including 100+ Google Chrome tabs, Firefox 4 beta, Skype, Gnome Terminal, Gedit, evince, Okular and Coqide.

---

### Post by jspepinc on 2011-02-16
Thank you the uswsusp package fixed slow resume from hibernation for me. It seemed to be caused by a kernel update (for me 2.6.35-25). Also, on Ubuntu 10.10 I needed to just create the 00sleep_module file.

---

### Post by kovo1533 on 2013-03-11
> **fishtron said:**
> I have only one file in there, called 00sleep_module

This is the file's contents:

```
# The sleep/wake system to use.  Valid values are:
#   kernel    The built-in kernel suspend/resume support.
#             Use this if nothing else is supported on your system.
#   uswsusp   If your system has support for the userspace
#             suspend programs (s2ram/s2disk/s2both), then use this.
#   tuxonice  If your system has support for tuxonice, use this.
#
# The system defaults to "kernel" if this is commented out.
# SLEEP_MODULE="kernel"
SLEEP_MODULE="uswsusp"
```

You might have to install uswsusp first, though.

I have Ubuntu 10.04.4, installed uswsusp and folder was too empty. But if you create this file it will do the work. I must say that this solution helps a lot. Before, the resume takes about minute to show desktop, but for next two or three minutes computer was still unusable and with lot of harddisk activity.

---

