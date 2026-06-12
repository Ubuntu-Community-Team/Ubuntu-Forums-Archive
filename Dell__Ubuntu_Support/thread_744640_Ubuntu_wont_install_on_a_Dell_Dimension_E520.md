---
title: "Ubuntu wont install on a Dell Dimension E520"
date: 2008-04-03
forum: Dell  Ubuntu Support
---

### Post by BoilingFrogs on 2008-04-03
My computer is a Dell Dimension E520 (Intel duoCore @2.8) that i bought about a year ago. For some reason Ubuntu refuses to install on it. I'm new here so I initially posted about this in another sub-forum. I just saw this one and thought it might yield better results.I'm sorry if thats a breach in forum etiquette, but i posted it 2 days ago and just before i came to type this i gave it a shameless bump in an attempt to revive a so far dying thread. So if you want a more detailed description then here is my first post about it:

[http://ubuntuforums.org/showthread.php?t=742573]("http://ubuntuforums.org/showthread.php?t=742573")


so, here's the deal:

I noticed that a single setting in the bios affects whether i can install xp or not. The setting for &#8216;SATA Operation&#8217; and the options are &#8216;RAID on&#8217; or &#8216;RAID Autodetect/ ATA&#8217;.

When it is set to 'RAID on" only Vista will install... everything else thinks there isn't a hard drive or it is corrupt. So far i have tested various xp's, Mandrake 10, OSx86 and Ubuntu 7.10.

When it is set to "RAID Autodetect/ ATA" then windows xp can install, but not anything else (including Ubuntu 7.10)

When Ubuntu tries to install, it spits out a bunch of errors like this:

&#8220;Buffer I/O error on device sr0 logical block 306443&#8221;
&#8220;SQASHSHFS error: unable to read cache block&#8221;

Then it loads the installation gui. The installation goes fine from there, until it gets to the Partition Tool, when it locks up at 6% and finally says it can't write to the hard drive.



So does anybody have any idea what's going on here and how to fix it? I desperately want to install Ubuntu.

---

