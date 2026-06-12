---
title: "Scheduled startup?"
date: 2006-07-02
forum: Desktop Environments
---

### Post by realityisterror on 2006-07-02
I'm looking for a way to boot up a computer everyday at a given time.

It's fairly simple to shutdown with a cron command or whatnot, but I can't seem to find any way to do this.
I'm only assuming that it is possible as you can easily do this in Mac OS X, which is based of Unix. If I knew the commands OS X issued, I might be able to figure it out.


Any ideas?
Thanks

---

### Post by arizonagroovejet on 2006-07-02
> I'm only assuming that it is possible as you can easily do this in Mac OS X, which is based of Unix

Flawed logic I think. Just because it is possible in Mac OS X does not mean it is possible in Linux. Mac OS X is built on a different Kernel and runs on different hardware (the new Intel Macs are not entirely regular x86 hardware like you'd get from Dell or wherever.)
I'm pretty sure the ability to boot up at a certain time is a feature of the hardware that Mac OS X runs on, not a feature of Mac OS X itself.  Mac OS X just gives you a way to control the settings. Think about it, when you turn the machine off the OS is not loaded. There has to be a chip somewhere in the machine to remember the setting and issue the power up command.
Such a thing may be possible if you are running Linux on Apple hardware but other than I don't think so. In the years I've been using Linux I've never seen any references to scheduling boot up times.
Of course is someone can prove me wrong...

---

### Post by Anduu on 2006-07-02
Check to see if your BIOS can do it...Mine has settings for starting up and shutting down at certain times...never tested em as my PC is up 24/7

---

### Post by realityisterror on 2006-07-03
Thanks guys :)

My BIOS had settings to boot at a certain time, and I just setup a cron job to shutdown as well.

Much appreciated.

---

