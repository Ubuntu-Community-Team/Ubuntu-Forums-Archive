---
title: "Sudden random drastic slow down (near freeze)"
date: 2006-09-26
forum: Desktop Environments
---

### Post by Thruston on 2006-09-26
Does any one recognize my symptoms please?  

HW: Newish IBM PC A50 Pentium 4 desktop, 512MB, lots of disk, ADSL, etc

Ubuntu: fresh Dapper install 6.06, updated & upgraded to lastest everything.  ntpd enabled.

At random, my system (very nearly) stops.  At least once a day, it slows down to an unusable state. Some times when the screensaver is on, other times just in the middle of normal work. Gnome becomes completely unusable.

However some things go on working.  For example rhythmbox goes on playing music, and Alt-Ctrl-1 gives me a console (after a long pause).  

When I get the text console up it performs nearly normally, except that some things run very slowly.  For example the system beep lasts for 10 seconds instead of 0.5 seconds, and man pages take ages to format.  

And the clock has slowed down by a factor of about 10.  "hwclock" gives (approximately) the right time, but "date" is some way behind.  Neither "top" nor "vmstat" show anything unusual.  Nothing in any log.  Killing X makes no difference.

Restarting clears the problem. Any clues? Any suggestions for what to investigate?

Thanks Toby

---

### Post by whizbaby on 2006-09-26
Sounds like a hardware problem to me (doesn't have to be). Most common issues are RAM modules and HDs. Perform a memory check (memtest86, can be chosen in grub at startup) and get the *testdisk* package (e.g. synaptic) and check your drive **only after backing up important data**. Anyway, how old is your HD?

---

### Post by Thruston on 2006-09-26
I agree it *sounds* like a hw problem, but I don't think it is.  
Both memory cards and both HDs are quite new, and I don't fiddle with them.  memtest shows nothing (although I haven't left it running for days...).  I'll think about testdisk.

My current theory is that it ntpd that is at fault, so I have turned it off.

Something similar happened once under my old Gentoo distro on the same hw shortly after a large slug of upgrades, so I agree it *could* be hw, but I suspect some common level of system software.  I await edgy with interest to see if my bug goes away.

Any one else seen anything similar?  T.

---

### Post by whizbaby on 2006-09-26
If RAM and HDs really are okay (even new stuff can be broken) I would look around your graphics hw next (what is it?).

---

### Post by dkarner on 2006-09-26
I have the exact same problem.

I am also running an ThinkCentre A50 series system.  I installed a LAMP server distro.  Perhaps the problem could be specific to the BIOS on the systems, though I am running at the current version BIOS for the system 2CKT22A.

The hwclock command always reports the correct time.

In my case though the date command is not way behind, but actually has stopped moving forward at some point and simply loops through a small periods of seconds over and over.


I.E..

Mon Sep 25 23:29:26 EDT 2006
root@rockingk:/var/log# date
Mon Sep 25 23:29:27 EDT 2006
root@rockingk:/var/log# date
Mon Sep 25 23:29:28 EDT 2006
root@rockingk:/var/log# date
Mon Sep 25 23:29:29 EDT 2006
root@rockingk:/var/log# date
Mon Sep 25 23:29:25 EDT 2006
root@rockingk:/var/log# date
Mon Sep 25 23:29:26 EDT 2006
root@rockingk:/var/log# date
Mon Sep 25 23:29:27 EDT 2006
root@rockingk:/var/log# date
Mon Sep 25 23:29:28 EDT 2006
root@rockingk:/var/log# date
Mon Sep 25 23:29:29 EDT 2006
root@rockingk:/var/log# hwclock
Tue 26 Sep 2006 04:22:46 PM EDT  -0.759101 seconds

---

### Post by whizbaby on 2006-09-26
Found on another thread:
> 
**Re: IBM Thinkcentre A50: usb HD problems and sistem freeze**
Hi,

Make sure you've booted the box with the "noapic" and "apic=off" kernel command line options; without these you'll find it (the A50) freezes regularly (at least on the newer revisions this is true)


---

### Post by Thruston on 2006-09-26
OK thanks for those pointers.  

Searching on "IBM ThinkCentre A50" shows that this problem is common to many IBM A50s with kernels > 2.6.8  

The main thread appears to be ** Ubuntu hangs/freeze/stalls **

The problem is reported to be solved either by updating the BIOS (but perhaps not), or just disabling the ACPI and the APIC as noted above. There is also a   fix / patch for the kernel, but this has not made it into any upstream change as far as I can tell.

And by the way it should be "acpi=off" and "noapic" I believe.  See the detailed explanation at [http://support.novell.com/techcenter/sdb/en/2002/10/81_acpi.html]("http://support.novell.com/techcenter/sdb/en/2002/10/81_acpi.html")

---

### Post by whizbaby on 2006-09-26
> **Thruston said:**
> And by the way it should be "acpi=off" and "noapic" I believe.
Yeah, that's a typo (I just copy-pasted from the other thread without paying too much attention it seems).

---

### Post by Thruston on 2006-09-27
Upgrading the BIOS to the latest level from IBM has (so far) fixed the problem for my A50.  As noted above, your mileage may vary.  

Uprading the BIOS was a fiddle: IBM supply Windows-only update images.  Fortunately I had my laptop from work handy to unpack and burn the CD image.

I'm waiting until Slug State happens again, before I fiddle with acpi=off.

I note that IBM require "acpi=noirq" as part of the install instructions for Red Hat on their Linux-supported servers.  I might experiment with this too.

Again thanks for tying this thread up with the others on the IBM A50.  Toby

---

### Post by Thruston on 2006-09-29
Well it was better with the new BIOS. It took a lot longer to get into Slug State, but it did after about 36 hours up time. So as noted on the other threads the latest level of BIOS does not fix the problem (perhaps I was just lucky to get 36 hours up time).

Now rebooted with "acpi=off noapic nolapic".  T.

There is of course a right way to do this and a wrong way.
The simple way is just to add the above parms to the end of the default kernel line in "/boot/grub/menu.lst".  This is the wrong way, because the "update-grub" script will overwrite your line whenever the kernel is upgraded.  

The right way is to add the parms to the end of the "defoptions" line near the top of the file, and then run "sudo update-grub" to rebuild your menu.lst.  Note that the "defoptions" line *should* start with a single #.  See "man update-grub".

---

### Post by Thruston on 2006-10-09
One week on and no further problems, so acpi=off is clearly the way to go with an IBM A50 PC.

The only downside is that the OS can no longer switch off the power when I shut down.  You have to turn it off by pressing the button. 

T.

---

### Post by joeqlaw on 2007-01-07
The changes to menu.lst have held up for me so far.  Thanks for the posting. :)

---

### Post by ivotron on 2007-07-04
Thanks a lot for your feedback man!

I have Edgy on a IBM NetVista 8350 and the same changes to the kernel loading parameters worked for me.

---

