---
title: "Timezone resets on reboots"
date: 2008-12-22
forum: General Help
---

### Post by tescott on 2008-12-22
I'm encountering a weird problem where my timezone resets after I reboot and connect to my network.  I'm running Ubuntu 8.10 off of a pendrive (with persistent data enabled). Here are the steps / symptoms I'm seeing:

1) Set up the timezone, etc. and see the correct date/time reported on the toolbar. My timezone is "America/North_Dakota/Center". I've used "sudo dpkg-reconfigure tzdata" to set my timezone, and have confirmed that "/etc/timezone" matches my setting. Doing a 'diff -s /etc/localtime /usr/share/zoneinfo/`cat /etc/timezone`' indicates no difference (as expected).

I've also edited /etc/default/rcS so that "UTC=no".  I'm doing this because I'm running WinXP off of the internal HDD.

2) Reboot.  The date/time on the panel bar is correct until I enable my wireless connection.  I presume this is heading out and grabbing time from a timeserver or some such.

3) After my wireless connection is up in running, the date/time on the panel bar now reads +0600 hours local time (e.g. local time = 12PM CST, panel bar time = 6PM) On the command-line 'date' similarly reads UTC instead of CST.

4) Go to System > Administration > Time And Date

5) "Time Zone" now is blank. In step 1) above, I had set it to America/North_Dakota/Center". /etc/timezone is still correct. However, 'diff -s /etc/localtime /usr/share/zoneinfo/`cat /etc/timezone`' now indicates a difference - this is unexpected. Doing a 'diff -s /etc/localtime /usr/share/zoneinfo/UTC' shows an identical match.

Why is /etc/localtime getting updated?  If I can prevent this from happening, I think that will solve my problem.

Thanks.

---

### Post by tescott on 2008-12-22
I've done a little bit of investigation and know that at step 2) (after reboot), the /etc/localtime file is already changed.  The timestamp verifies that it must be during the boot-up.  This is well before I enable my network connection.

Anyone have any ideas what might be updating this?  I'm not familiar enough with the boot process on Ubuntu to understand what's going on, otherwise I'd dig into it myself.  

Thanks.

---

### Post by tescott on 2008-12-22
Okay, I believe I've found the cause of my problem, but don't know how to correct it.  This script is updating /etc/localtime with the UTC version:

/rofs/usr/share/initramfs-tools/scripts/casper-bottom/02timezone

However, because it is in /rofs, I can't modify it.  If I try to ```
sudo gedit 02timezone
``` I get an error stating that I am trying to modify a read-only file system.

Looking at /etc/mtab, I see that /rofs is defined as:

/dev/loop0 /rofs squashfs ro,noatime 0 0

I'm not sure what "/dev/loop" is.  I could try to change that "ro" to "rw" since this is a USB stick that is indeed writeable.  I'm just not sure if I'll end up hosing myself in the long run.

Any tips?

---

### Post by nlz on 2008-12-22
wow, you really got into it. I faced the same problem and then corrected the problem by saying I was in another time zone until it corresponded correcly. Now ubuntu thinks i live in the azores. Nice idea...

---

### Post by migloo on 2009-03-16
I suggest you edit /usr/sbin/ntpdate-debian to add this toward the beginning:

> /etc/localtime cat /usr/share/zoneinfo/`cat /etc/timezone`
logger 'ntpdate-debian: rebuilt /etc/localtime from /etc/timezone'

---

