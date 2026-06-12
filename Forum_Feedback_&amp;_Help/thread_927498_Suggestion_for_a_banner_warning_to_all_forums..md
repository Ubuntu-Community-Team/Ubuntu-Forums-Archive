---
title: "Suggestion for a banner warning to all forums."
date: 2008-09-23
forum: Forum Feedback &amp; Help
---

### Post by Scruffynerf on 2008-09-23
'Afternoon.

I've a suggestion that perhaps there be a warning on all forums to not use Intrepid Ibex if the user has an Intel ethernet. 

Apparently, there is a bug in the kernel (specifically module e1000e) that maps the firmware memory as writable, and fills it with garbage to the extent that the NIC / cards cannot be enumerated by the BIOS. Intel's own repair software is sometimes successful in repairing on desktops, but not on laptops.

Originally found at Ars Technica ( [http://episteme.arstechnica.com/eve/forums/a/tpc/f/96509133/m/283000364931]("http://episteme.arstechnica.com/eve/forums/a/tpc/f/96509133/m/283000364931"))
With bug reports being present at:
Kernel Bugzilla: [http://bugzilla.kernel.org/show_bug.cgi?id=11382](http://bugzilla.kernel.org/show_bug.cgi?id=11382)
RHEL Bugzilla: [https://bugzilla.redhat.com/show_bug.cgi?id=459202](https://bugzilla.redhat.com/show_bug.cgi?id=459202)
Launchpad: [https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/263555](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/263555)
Suse Bugzilla:[https://bugzilla.novell.com/show_bug.cgi?id=425480](https://bugzilla.novell.com/show_bug.cgi?id=425480)

What is especially worrying is that from the Ubuntu launchpad, it would seem that the devs are more concerned about pushing back the Intrepid Live date rather than breaking user's hardware.

I thought that it might be an idea to warn the community of this issue? Apologies if this post is in the wrong place.

Edit: What's with the icon? I didn't select that?

---

### Post by eentonig on 2008-09-23
It's alpha software, people should be considered as being aware that using it might break stuff. 

Furthermore, people should be smart enough to read about the known issues prior to installing it.

Yes a warning and blacklisting the e1000 driver should be done, but revoking an alpha because of a (serious) bug just doesn't  seem the answer to me, because it blocks you from finding other issues that might bite people when the official release gets out.

---

### Post by sloggerkhan on 2008-09-23
blacklisting the driver for now seems to make a lot more sense than pulling the whole cd.

---

### Post by Scruffynerf on 2008-09-23
Fair enough, however I would have thought that an OS bug corrupting firmware requiring a return to manufacturer would have warranted something significant? Ubuntu is targeted as a user-friendly distro, and often marketed as a good one for new users. 

Generally (IMHO) most people think that Alphas have a good chance at breaking (itself), not so much expecting permanently trashed hardware.

---

### Post by Joeb454 on 2008-09-23
> **Scruffynerf said:**
> 
Edit: What's with the icon? I didn't select that?

What icon ;)

I've recently downgraded to hardy on my laptop, so I guess I'm ok for now :)

---

### Post by eentonig on 2008-09-23
It's not the OS. Suse suffers from the same issue according to slashdot.

---

### Post by hyper_ch on 2008-09-23
kernel 2.6.27 is the problem according to one article I read.

---

### Post by Scruffynerf on 2008-09-23
Mandriva has issued a warning.

[http://blog.mandriva.com/2008/09/23/urgent-notification-major-bug-in-all-mandriva-linux-2009-pre-releases/](http://blog.mandriva.com/2008/09/23/urgent-notification-major-bug-in-all-mandriva-linux-2009-pre-releases/)

Also, one of the Intel guys has a system for getting a snapshot of your eeprom:
[http://bugzilla.kernel.org/show_bug.cgi?id=11382#c17](http://bugzilla.kernel.org/show_bug.cgi?id=11382#c17)

Edit:

Also, the Ubuntu website itself has plastered a warning.
[http://cdimage.ubuntu.com/releases/intrepid/alpha-6/](http://cdimage.ubuntu.com/releases/intrepid/alpha-6/)

Could we please distribute this warning? As a community service even?

---

### Post by schauerlich on 2008-09-23
> **Scruffynerf said:**
> Could we please distribute this warning? As a community service even?

[http://ubuntuforums.org/showthread.php?t=927943](http://ubuntuforums.org/showthread.php?t=927943)

---

### Post by Scruffynerf on 2008-09-24
:oops:

---

### Post by hyper_ch on 2008-09-24
well, the post by jdong was done after the TO started this thread here :) good thinking Scruffynerf.

---

