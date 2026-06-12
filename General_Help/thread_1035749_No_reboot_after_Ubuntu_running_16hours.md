---
title: "No reboot after Ubuntu running 16hours"
date: 2009-01-10
forum: General Help
---

### Post by msfisher on 2009-01-10
First off, let me say that unless someone here tells me otherwise, I'm not blaming Ubuntu for what has happened.  However, both times have been after running Ubuntu overnight.  Please be aware that I'm seeing a lot of things here, some of which may have nothing at all to do with the problem.  Plus, I'm coming here because I've gotten lots of positive help here before.

My system:
MSI K8N Neo v1.0
AMD Sempron initially 2600+, then 3000+
DVD+R/RW
2x512 meg memory
hda 80gig initially Western Digital, formatted to Win98 with three partitions, now  Maxtor
hdb 80gig (WD), with one FAT32 partition and three Ext3 partitions, Ubuntu on the first

For clarity, let's call the first hda WD1 and the new one Max

I have noticed that the two drives seem to run hot, especially the Ubuntu one.

The lead-in is just as I said – Ubuntu running overnight.

Symptoms:  Flatly, will not reboot.  When rebooting from Ubuntu, I get a black screen for an indefinite period – the first time I waited, ~5min, second ~2.  Will not reboot from hard reboot but sometimes from power-off.  Sometimes I can get the BIOS splash screen and POST, but the system halts when the drive array is being detected.  If I can get the splash screen, I can get into setup but I can't reboot after.  My boot order is CD/floppy/hda.  It won't reach the boot-from-CD check.  Other times, it won't even get to this point.  If I go into setup, everything looks OK, including processor temp (between 35 and 40 C).  

The first time, I tried several things.  I took the HD's to a computer with a newer BIOS and tried them.  Initially, they wouldn't boot.  I then tried a rescue/repair from my Ubuntu CD.  That did the trick and I got a report (correct) that my then-hda (WD1) was dying.  I assumed this was part of the problem and ran some diagnostics.  Everything looked OK.  Before anything else, I tried a different mobo (found to be totally dead) then put the MSI back in with the faster processor.  After reassembling everything, including the HD's the system booted.  

I then did a clone job from WD1 (SMART reported 0% healthy) to the Maxtor (SMART reported 96% – the same utilities reported hdb at 100%, but without temperature support.  Odd, since it is the same make & model as WD1, just newer).  It booted OK.  For a week, things were OK.  Some nights I turned it off, some I left it on running Win98.  Notably, with Win98 running, hdb will shut down.  I think it is set to stay up under Ubuntu – that is, sleep mode has the monitor off but hdb on when Ubuntu us running while with Wiin98 hdb powers down.  I added a second case fan to help with cooling.

Last night, I left Ubuntu/hdb running and this morning, the same thing happened.  Ubuntu seemed to run fine except there was no sound.  To recover the sound, I rebooted – same as before.  Black screen, no reboot or boot only as far as setup

One oddity – both times, before the crash, I had the BIOS set such that just pressing the power button briefly shut off the system.  Now, I have to hold it for five to ten seconds.  Also, when I power up, the HD light comes on for 1-2min then goes off.  I get no signal to the monitor.  Disconnecting the hard drives, either individually or both, doesn't change things, nor does disconnecting the DVD.

What the heck is going on?  Is it a heating problem on hdb?  Then why doesn't it boot at all to hda or the mobo?  Why does an Ubuntu rescue fix the boot problem?  Why did changing processors help?  Is it a mobo problem?  If so, then why did disassembling/reassembling the board work?

ANY answers – even additional questions will be of huge help.

---

### Post by msfisher on 2009-01-10
The plot thickens -- or simplifies.  I let the system sit for about two hours while I ran some errands and wonder of wonders, it booted.  Perfect.

So, just a heating problem?  If so, what?  hda, hdb, processor, northbridge?

---

### Post by abn91c on 2009-01-10
you may be having some kind of imminent hardware failure soon. Maybe your RAM or video card? Try replacing the CMOS battery for a new one and check the insulation compound of the CPU

---

### Post by msfisher on 2009-01-10
Thanks abn91.  I've been considering that possibility.  Since I just replaced the processor and am using an "official" AMD fan AND the problem initially occurred with a different processor, I doubt heat transfer is the problem, though you have reminded me to be sure that there's a good coating on the CPU.  

As for other hardware, except for something on the mobo, I'm not sure.  RAM is pretty new, so is video. Just in case, though I've been looking for a good replacement socket 754 AAGP mobo.  Since they're older, they're hard to find unless I only want to use eBay.  I know, get a "newfangled" one, but I don't want to waste memory, video and processor.

---

### Post by abn91c on 2009-01-10
shop here for bargains instead of ebay [http://www.geeks.com](http://www.geeks.com)
they have a socket 754 mobo for $47.99

---

### Post by msfisher on 2009-01-10
It's looking more and more like this is a hard drive overheat problem.  With the case open, I ran a couple of additional drive monitoring utilities and found that my c: drive (Maxtor) was running too warm.  Since the second drive, a WD apparently doesn't support reporting temperature, the fact that it was hot to the touch suggested it must be too warm as well.  A quick Google turned up that in at least some circumstances hard drive overheating can result in lockups.  Sounds like it's time to get a new case with more separation between the drives (these two are only a few mm apart) plus cooling directly on the drives...and maybe a couple of hard drive coolers as well.  I should also probably set Ubuntu to sleep both drives.

---

