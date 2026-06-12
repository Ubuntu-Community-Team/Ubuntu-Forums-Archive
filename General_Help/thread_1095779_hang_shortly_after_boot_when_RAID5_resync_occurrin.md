---
title: "hang shortly after boot when RAID5 resync occurring"
date: 2009-03-14
forum: General Help
---

### Post by jeyno on 2009-03-14
I have Ubuntu 8.04 64-bit on a dual Xeon machine.  The machine has 3 SATA disks configured with RAID.  A RAID1 md0 for /boot - I also have md1 and md2 as RAID5 for data and swap.

This configuration has been up and running without problems for more than 6 months.

I'm now having trouble at startup - the server boots and allows me to login - after about 3-6 minutes the server hangs.

Immediately after login

cat /proc/mdstat

shows that a resync of md2 is in progress.  This gets to about 2-3% of its progress before the system just stops and hangs.  Then all bets are off - the system hangs and a hard reset is the only way out.

I am running kernel 2.6.24-22-generic #1 SMP with boot options irqpoll and acpi=off added from recommendations given here

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/17207](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/17207)

and here

[http://ubuntuforums.org/showthread.php?t=892657&page=2](http://ubuntuforums.org/showthread.php?t=892657&page=2)

I'm now rather stuck and will greatly appreciate some expert help!

---

### Post by jeyno on 2009-03-14
I have tried booting from the Ubuntu 8.04 desktop live CD to attempt recovery from a system where the / filesystem did not depend upon the md2 under resync.

installed mdadm and then entered

mdadm --assemble /dev/md2 /dev/sda3 /dev/sdb3 /dev/sdc3

this assembled the md2 device which

watch cat /proc/mdstat

revealed when into resync.  after 20 mins or so, at 8.2% complete the server froze.  No mouse movement, no ability to ctrl-alt-F1 to a console.  Dead as.

---

### Post by jeyno on 2009-03-15
I'm back to basics now.  just running tests on the disks, whilst booted from the LiveCD.

The disks are all Seagate Barracuda ES.2 ST31000340NS 1TB 7200 32MB.

Using smartctl all three disks show 'PASSED' but I notice they have a 'code 190' temperature event recorded 'in the past'.  Maybe they became too hot because I had them stacked in a 5-in-3 SATA backplane caddy.  They're not dead yet however because the system starts up from them with the RAID array accessible until Ubuntu freezes.

Now an interesting event - running 'badblocks' on all 3 disks concurrently resulted in the same system lockup.  At this time, mdadm was not even installed (remember this is a liveCD boot).  So this rules out the software RAID factor.

---

### Post by jeyno on 2009-03-17
I believe mine was an overheating issue.  See an alternative thread here.

[http://groups.google.com/group/alt.comp.periphs.mainboard.tyan/browse_thread/thread/2de7f9f12a9aa8e7/03839c65766f4907?lnk=gst&q=s5397#03839c65766f4907](http://groups.google.com/group/alt.comp.periphs.mainboard.tyan/browse_thread/thread/2de7f9f12a9aa8e7/03839c65766f4907?lnk=gst&q=s5397#03839c65766f4907)

---

