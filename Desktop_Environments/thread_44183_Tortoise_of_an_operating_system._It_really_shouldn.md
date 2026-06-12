---
title: "Tortoise of an operating system. It really shouldn't be."
date: 2005-06-24
forum: Desktop Environments
---

### Post by kylenewton on 2005-06-24
No offense to hardcore Kubuntu users. I know how Kubuntu should run. Read on.

I've recently installed Kubuntu (last night) at home and am not very impressed with the speed it's capable of on my computer. I've had Kubuntu set up on my work computer (a Dell) for the last month and am quite happy with it.

However, after installing it on my home computer I'm taking a huge performance hit. Here's my hard-ware setup.

AMD Duron 750MHz cpu.
~15gb hard drive for Kubuntu with 14.7 Gb ext3 and 654 Gb swap. This hard drive is a slave on the first ide cable, with a 120Gb hard drive with WinXP as master
I'm behind a wireless router, connected directly to it via a LAN cable.
Lite-On 16x CD-Burner set up as master on the second ide cable.
256MB SD-Ram.

I hear my 15Gb Kubuntu hard drive *click* a lot. I haven't heard my 120GB hard drive do that.

The default installation took from 5pm yesterday up until around 11:30pm last night. Longest install I've ever experienced. I rebooted from the command line and the installation finished by setting up the Kubuntu GUI.

Now when I restart, from the time restart begins with "starting ubuntu" to the time I see a graphical login screen it takes [edited: 30 minutes (I timed it this time)]. To start Firefox it takes ~3 minutes the first time it loads. All the applications are like that. They take forever.

KSim tells me at the moment I have 252M total memory with 16M free. And 636M total swap, 636M free.

The kernal it automatically picked for me on installation was the 386 version. I installed the 686 kernel through Kynaptic and rebooted. Again, a long load time after choosing 686 at GRUB. And even now there's no increase in speed.

I couldn't possibly need the AMD 64 installer, could I? This AMD Duron is 6 years old already.

I appreciate any and all help. Thanks.

---

### Post by intangible on 2005-06-24
I know it's obligatory, but does hdparm show dma on for that drive?  (**hdparm /dev/hdb**)

---

### Post by wdso on 2005-06-24
If you feel your computer isn't able to handle Ubuntu, have you tried Damn Small Linux?
Boot with the option "toram", then you see what I mean ;)

On the other hand, I think there is something seriously wrong with your system: Is DMA activated? BIOS problems? Have you installed Windows or another Linux distribution? Is there a process which eats all you cpu time (check with top, then pressing 'P' in a konsole)

---

### Post by az on 2005-06-24
What is consuming the most cpu power when you run
sudo top
from a terminal?

Also, no this is not normal.  It should take about a minute to boot and about ten seconds for firefox to pop up with your hardware.

---

### Post by elvis on 2005-06-24
[QUOTE=kylenewton]Kubuntu

256MB SD-Ram.[/QUOTE]

KDE is extremely bloated.  If you want to run a nice WM on 128-256MB, try XFCE4 instead.  KDE users should be looking to 512MB RAM minimum if they want a decent desktop experience.

From memory XFCE4 is not currently in the Ubuntu dists, so you'll need to point to a Debain mirror to install it (someone correct me if I am wrong).  I build a number of lightweight kiosk style terminals for my clients on machines as low-end as Celeron 600 with 128MB of RAM, and they run fine.  

If I'm building KDE workstations for my higher-end clients, then all systems ship with a bare minimum of 512MB RAM.  1-2GB for people doing more intensive 2D and 3D graphics and the like.

As for your hard disk "ticking" - this is a worry.  If the ticking is random and irregular, it could just be a noisey drive, which is fine.  If however it is very regular, then you might have a drive head that is out of alignment, in which case the drive could be near death.

Use tools like the Ultimate Boot CD (free of cost, but not 100% libre) to run diagnostics on your hard drives to make sure all is well:

[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

---

### Post by kylenewton on 2005-06-24
Thanks for the quick responses (and if they weren't so quick in reality, compared to a 30 minute reboot cycle it was).

[QUOTE=intangible]I know it's obligatory, but does hdparm show dma on for that drive?  (**hdparm /dev/hdb**)[/QUOTE]

> sudo hdparm /dev/hdb

/dev/hdb:
using_dma = 1 (on)

So I'm at a loss. I suppose I should call it quits with my old drive (again, 6 years old) and make room with a partition on my 120Gb drive.

Thanks for the help.

---

### Post by moopere on 2005-06-25
[QUOTE=elvis]KDE is extremely bloated.  If you want to run a nice WM on 128-256MB, try XFCE4 instead.  KDE users should be looking to 512MB RAM minimum if they want a decent desktop experience.[/QUOTE]

I should know better than to jump in on a thread like this, but, here we go:

KDE -is- bloated, I'll agree and you'll see why I agree further down when I have a good old rant (hehe).  Gnome is even further bloated, and slower still than KDE - however, neither need more than 256MB RAM to work really really well.  No doubt a quad Xeon with 4GB RAM and 15K RPM SCSI drives would be even better.

I see so many people nowadays telling newbs that their 256MB <1GB systems are too underspec'd to run Linux....good lord!  Is this true?  No, of course not.  'Fast enough' is too subjective to measure.

Log in to a Gnome session and open gnome-terminal how long does that take?  Now do the same from XFCE4 (open gnome terminal), about the same huh?  Try gnome-terminal under KDE as well...yup, its still about the same.

gnome-terminal is a big bloated piece of rubbish, but its useful for examples like this.

Theres things going on here that I don't understand, and certainly the simple act of running an executable is no type of benchmark, but its the human-machine interface that predominently makes people whinge that a system is 'slow' or 'fast'

If you click on an icon and immediately a window pops up your system is 'fast' - if you get the equivalent of an 'hourglass' from WinXX for a few seconds your system is preceived to be 'slow'.

Something is seriously wrong in GTK land because everything based on the toolkit/library(s) is abysmaly slow.  XFCE4 whilst light compared to KDE/Gnome is nothing near as fast as XFCE3 - really, try it if you can.  XFCE3 was/is lightning quick!

KDE?  Well, testing across several boxen here appears to 'feel' quicker than Gnome and indeed does bench out quicker on the machines I've bothered to test to this level.  However, KDE is not exactly snappy either, and theres no slow bloated GTK crap to blame for this either?  Perhaps Qt is just the same dog under a different name?

I know people will read this and say things like, oh, but KDE/Gnome is doing so much under the hood, blah blah, its giving a nice user experience, blah, its so integrated.....well, rant coming from me about this, lets move forward for now:


[QUOTE=elvis]From memory XFCE4 is not currently in the Ubuntu dists, so you'll need to point to a Debain mirror to install it (someone correct me if I am wrong).  I build a number of lightweight kiosk style terminals for my clients on machines as low-end as Celeron 600 with 128MB of RAM, and they run fine. [/QUOTE]

XFCE4 is available in the 'universe' repository and works very well.

I run KDE3.4 (now 3.4.1) on machines with a lower spec than C600/128MB, its fine.  Takes a few seconds longer to boot, for sure, but after that, listen to streaming media, burn CD's, surf the web, blah blah, no problems at all.

 
[QUOTE=elvis]If I'm building KDE workstations for my higher-end clients, then all systems ship with a bare minimum of 512MB RAM.  1-2GB for people doing more intensive 2D and 3D graphics and the like.[/QUOTE]

Sounds reasonable for a new box going into a business environment where they are likely not wanting to turn it over again for at least 3 years.

I don't spec Windows (XP) boxes for clients differently.  Right now they are a bit overspec, in three years they'll be near end of life.

[Rant Alert, don't read this if you're easily offended by Windows/Linux comparisons hehe]

Now for the rant.   I've been reading posts from a few forums, and this is one of them, that have really started to spring up over the last 6 months or so.  An aweful lot of these posts go along the lines of

"oh, you've only got  P4 1.5GHz, 256MB RAM Nvidia 5700, no you won't be able to run Linux properly with so small system"

(I'm gagging now)

Folks!  Whats going on?  Whilst that statement above is obviously incorrect, its indicative of what folks are telling the underinformed and newbs.

This is going to be a rant because I want those who are old enough to take a few steps backwards and think about when something like....umm.....Windows 95 came out in 1995 (for most of us).

Did Win95 have severe problems right up to and including the day microsoft dropped support?  You bet it did.  But remember how integrated it was compared to all that came before?  Not a bad first effort in PC land (nope, not talking about Macs here).  You could just install and almost run Win95 on a 386sx with 2MB RAM, I've done it!  You could write email, surf the web, do some stuff.  by the time you got to 8MB RAM you were running office 6 or even Office 97 a few years later.

Now, whats the point of the rant?  Surely there must be one?  

Firstly, don't get me wrong, I know the limitations of Win95 (and all the Wins actually), I know Linux as a general rule is far more scalable etc etc, all the blurb we normally hear about in advocacy groups, but we got a serious amount of pretty tight integration on unbelievably low spec'd box's, and thats the point.

How could I run Win95 on a 386sx16 4MB RAM with sound, modem, mouse,  Office6, screensavers, blah blah blah, yet today, I am supposed to not be able to run KDE on a 1GHz box with 256MB RAM and all the fruit?

How could I be running a resource hog like OS/2 server on an 8MB 486DX/100 with 20 workstations hanging off it?

Our expectations of a desktop experience (even a server experience come to think of it) have changed a lot in 10 years, no doubt, but I feel as if we've not really progressed in the ratio of bang versus horsepower.

Am I wrong?  Am I remembering the early Windows & OS/2 days through rose coloured glasses?   Please, someone tell me its all in my head, and we're not on a treadmill of ever slower, ever larger software that really doesn't do much more in terms of basic functionality.

[rant off]

takes deep breath.

:)

Cheers,
Craig

---

### Post by Knome_fan on 2005-06-25
Something is definately terribley wrong and I think you are right to suspect it's the hard drive. A clicking hard drive is in my experience a very sure sign for a hard drive that, how can I put it, has reached the end of its lifecycle, so either getting a new one or partitioning the other drive seem to be your best options.

To sort of confirm that the hard drive is the problem, you could try to run the LiveCD. If this runs a lot faster than your current install, you can be pretty sure that it's the hard drive that is causing the problem.

Finally, thanks to all those people sharing their infinite wisdom on how bloated KDE is, yadda, yadda,...

---

### Post by elvis on 2005-06-25
[QUOTE=moopere]<RANT>[/QUOTE]

The problem is that anyone who runs KDE immediately turns up all of the eye-candy and effects, and then wonders why their swap file gets thrashed on low-memory systems.

Here's a better test for you:

From a clean boot, log into a KDE desktop.  When all is loaded and settled, check your memory usage.

Now, from a clean boot, do the same with XFCE4.

The difference is staggering.

256MB is fine for KDE if you want to check a few emails and browse a forum.  If you start getting into anything heavier than that  - even medium sized OO.o documents and the like, you will soon start to hear the ever present swapdrive thrash.

I run several medium to large networks for my work, and in a few of those networks I've migrated them from Windows systems to LTSP/Thin-client systems running GNU/Linux.  One of them had a pre-existing LTSP box running KDE as the default desktop, and 2GB of RAM on the server.  Once more than 10 users logged in, staff complained about lag and general day-to-day slowdown in common apps.

Only a fortnight ago I migrated them all to XFCE4.  Memory usage per-person dropped considerably.  We're talking a 50% or more reduction here with NO change in daily workflow.  The system that once struggled with 10 concurrent users now takes the full 25 staff without issue.  They where actualy considering running 2 LTSP servers side by side, and now do not have to waste their money.  Now there's evidence "live in the field" if I ever saw it.

I'm super glad you like KDE.  It certainly is a wonderful WM, and one that makes workstation workflow fantastic to use.  But on system specced with low amounts of RAM, or on multi-user setups, it is just far too bloated.  That's not something to take offense to, it just is.  I use GNOME on my home system (AthlonXP 3200+ with 1GB RAM) and I love it.  But you wouldn't see me even considering installing it on my friend's laptop (celeron 400, 196MB RAM).  He's now on XFCE4, and loving it.

XFCE4 is one of the lightweights.  For me it is up there with fluxbox, but maintains the ease of use you want for non-geek users.  Perfect for office workers, IMHO.

As for your comment on systems with 2GB of RAM being good for 3 years - that in it self is subjective.  For our email/document-typing office chums, I'd expect 4-5 years out of that.  For my TV, post-production and 3D clients, they replace systems annually or sooner.  4GB of RAM today will be unusable in 12 months time for these users.  That's just the nature of their trade.

You can't paint the world with a broad brush.  Everyone has different needs out of a system.  KDE doesn't work for everyone, and neither does XFCE4.  But aren't we glad we all use GNU/Linux and are able to choose for ourselves? :)

---

### Post by moopere on 2005-06-25
[QUOTE=elvis]The problem is that anyone who runs KDE immediately turns up all of the eye-candy and effects, and then wonders why their swap file gets thrashed on low-memory systems.[/QUOTE]

Heh.  Yep.  But my rant was really why!, why is this?  

Why is there so little extra functionality (thats apparent to a desktop user) from a machine running Win95 10 years ago?

Yes, there are some pretty big differences between the two systems, under the hood they are quite pronounced, but step back and be 'just a user' for a minute.  What extra's will I get runing KDE on my P4/3GHz 2GB RAM that I pretty much didn't already have running my 486 with 8MB under Win95?  I'm not just talking about eye candy either.

Its a broad broad question that would evoke every sort of flame in the advocacy newsgroups, but I'm a bit serious actually.  My point is not that we should all go backwards in time and run Win95 again, my point is, why, why, why, do systems like KDE and Gnome chew up so much resource for (apparently) so little return to the user?


[QUOTE=elvis]Here's a better test for you:

From a clean boot, log into a KDE desktop.  When all is loaded and settled, check your memory usage.

Now, from a clean boot, do the same with XFCE4.

The difference is staggering.[/QUOTE]

Oh yes, there is no doubt.  "Staggering" really is the right word too!    

My point in comparing KDE/Gnome/XFCE4 by opening gnome-terminal was to show that there is almost no difference in response between the 3 systems.  It takes about the same amount of time to open a gnome-terminal under all.    My suspicion is that this has something to do with the GTK libs because everything under XFCE4 has that little 'lag' that seems to accompany Gnome.  

Do you remember XFCE3?  Man, now that was quick!  I believe that XFCE3 was built gtk free.


[QUOTE=elvis]256MB is fine for KDE if you want to check a few emails and browse a forum.  If you start getting into anything heavier than that  - even medium sized OO.o documents and the like, you will soon start to hear the ever present swapdrive thrash.[/QUOTE]

Well, if a users experience of 'fast enough' is essentially not to use swap at all then you'd need a fair gob more than 512MB to do it unless using XFCE or Icewm or somesuch.

Whilst I certainly would not sell a machine new with less than 512MB, I can't agree that you need this much RAM to have a pretty reasonable desktop experience.  256MB on Celly's <1GHz seem quite happy under either KDE or Gnome to play DVD's, surf the web, write emails, burn CD's, do general Office type work.

The systems use swap, sure they do, but as I say above, systems so big on spec that they never use swap would surely come under the classification of high end, not the minimum required to have a comfortable easy to use desktop experience.

If you're doing heavy CAD/Art or something then fine, I can see the requirement, but these applications are hardly the common desktop.


[snip about running LTSP boxen with KDE]

[QUOTE=elvis]Only a fortnight ago I migrated them all to XFCE4.  Memory usage per-person dropped considerably.  We're talking a 50% or more reduction here with NO change in daily workflow.  The system that once struggled with 10 concurrent users now takes the full 25 staff without issue.  They where actualy considering running 2 LTSP servers side by side, and now do not have to waste their money.  Now there's evidence "live in the field" if I ever saw it.[/QUOTE]

Yep, looks like a sound plan.  Again, I won't argue this.  My point is/was "why", why is KDE/Gnome so incredibly heavy?  

We might find the nub of the answer if you ask your users what, if anything, they miss about the old KDE desktops they used to have.  If they can't think of anything then wow!  That essentially means that users are not gaining much from the huge extra resource sink that is KDE (or Gnome).


[QUOTE=elvis]I'm super glad you like KDE.  It certainly is a wonderful WM, and one that makes workstation workflow fantastic to use.  But on system specced with low amounts of RAM, or on multi-user setups, it is just far too bloated.  That's not something to take offense to, it just is.  I use GNOME on my home system (AthlonXP 3200+ with 1GB RAM) and I love it.  But you wouldn't see me even considering installing it on my friend's laptop (celeron 400, 196MB RAM).  He's now on XFCE4, and loving it.[/QUOTE]

You know, I do prefer KDE over Gnome, but only because I think the KDE folks have just cottoned on to the fact that their system is way to heavy - since about release 3.3 there have been significant speed increases whereas Gnome appears to be getting slower and slower.

However, my original rant still stands - why the huge difference in size, speed between KDE and XFCE?  Is it really because on the pretty icons on the desktop (I'm joking of course).


[QUOTE=elvis]XFCE4 is one of the lightweights.  For me it is up there with fluxbox, but maintains the ease of use you want for non-geek users.  Perfect for office workers, IMHO.[/QUOTE]

Yes.  Its my favourite lightweight because its user friendly in a way that flux, Ice etc etc are not.


[QUOTE=elvis]As for your comment on systems with 2GB of RAM being good for 3 years - that in it self is subjective.  For our email/document-typing office chums, I'd expect 4-5 years out of that.  For my TV, post-production and 3D clients, they replace systems annually or sooner.  4GB of RAM today will be unusable in 12 months time for these users.  That's just the nature of their trade.[/QUOTE]

Yep.  Sure.  I was only talking about the general business user.  They change systems on average every 3 years in Australia.  Some like your CAD/Art users above will continually churn systems over because they have not yet hit the sweet spot in technology (as Office users did more than a decade ago).

[QUOTE=elvis]You can't paint the world with a broad brush.  Everyone has different needs out of a system.  KDE doesn't work for everyone, and neither does XFCE4.  But aren't we glad we all use GNU/Linux and are able to choose for ourselves? :)[/QUOTE]

You betcha :)  My gripe is, and remains, what can I do with KDE/Gnome that I couldn't replicate with Win95 (talking desktop experience here, not server) and why does it take several powers of magnitude greater hardware to do it?

This is not an advocacy question, its based in resource useage and desktop expectation.  I'd love to hear what your users had to say when they came in Monday morning and found KDE replaced with XFCE....any gripes?

Cheers,
Craig

---

### Post by DaveH on 2005-06-25
I agree w/ Knome_fan - a clicking hard drive is not good. I'd make backing up any important data on that drive a priority, because it could die at any time.

Cheers
Dave

---

### Post by virgule on 2005-06-26
"Why is there so little extra functionality (thats apparent to a desktop user) from a machine running Win95 10 years ago?"

Can I say **software patents**?!?!?

::hides himself into flame-proof super bunker::

---

### Post by moopere on 2005-06-26
[QUOTE=virgule]"Why is there so little extra functionality (thats apparent to a desktop user) from a machine running Win95 10 years ago?"

Can I say **software patents**?!?!?

::hides himself into flame-proof super bunker::[/QUOTE]

I don't know what you mean?

Are you suggesting that MS managed to develop something so advanced that even 10 years later the OSS movement cannot replicate it because the original advanced idea (Win95) was/is covered by software patents?

Cheers,
Craig

---

### Post by arjaybe on 2005-06-26
[QUOTE=moopere]I don't know what you mean?

Are you suggesting that MS managed to develop something so advanced that even 10 years later the OSS movement cannot replicate it because the original advanced idea (Win95) was/is covered by software patents?

Cheers,
Craig[/QUOTE]

I don't understand this thread.  Windows 95 is so crude compared to my present desktops that there's little comparison.  I wouldn't use such an old-fashioned technology if someone gave me a computer all set up with it.

---

### Post by virgule on 2005-06-26
Lets stay on topic, hmmmk? :) Even since I jacked this thread this is not my original intention. I introduced the possibility that patents might be holding (Free/OSS?) software developpers behind because they would have to pay royalties to the owner of such patents, defeating the 'Free' part of Linux. WMV3 format and iTune's interface are two exemples I *think* are protected by patents (I really have no clue if they do or dont) and thats why Linux can't seam to be able to use the former properly and can't produce a similiar interface as the later.

Could it be so?

---

### Post by kylenewton on 2005-07-02
An update:

My hard drive was dead, and is officially laid to rest now as it wouldn't progress further than 0% on an fdisk format.

Kubuntu was successfully and easily installed (30 minutes) on my 120Gb hard drive. I'm not complaining about the speed with my 256 SD Ram, though I may look at XFCE some time.

Thanks for the help.

---

### Post by t2kburl on 2005-07-02
a happy ending   \\:D/

---

