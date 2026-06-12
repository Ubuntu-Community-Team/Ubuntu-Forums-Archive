---
title: "Help? Breezy Daylight Savings problem"
date: 2007-03-08
forum: Desktop Environments
---

### Post by Blueshell on 2007-03-08
I'm having trouble getting my Breezy box to cope with the changes to US Daylight Saving time.  I installed it about 18 months ago and compiled a whole bunch of kernel-dependent stuff that will certainly break if the machine is upgraded via the normal mechanisms, so I've been leaving it un-updated since then rather than risk repeated breakages every time the kernel gets revved, etc, and yes, it's inside a firewall.  (Sometime it'll become Dapper or Edgy, but not this month.)

But now I have to change its handling of US DST, and I'm having problems.  I tried grabbing the new files from [ftp://elsie.nci.nih.gov/pub/](ftp://elsie.nci.nih.gov/pub/), unpacked tzdata into a temp directory, and ran "zic -D TEST northamerica" to get the data.  That creates things like "America/New_York" instead of the "US/Eastern" that Breezy uses, but no matter---I hope.

I then tried changing the /etc/localtime symlink (which used to point to /usr/share/zoneinfo/US/Eastern) to point to my test file (e.g., /path/to/TEST/America/New_York), essentially pointing to that definition instead of US/Eastern (but I left /etc/timezone still containing "US/Eastern" because I'm trying to make as few changes as possible).  Note that I have -not- bashed the contents of /usr/share/zoneinfo in any way; all I did was repoint the localtime symlink to point at what I hope is the appropriate file in my test directory.  I know the symlink actually points somewhere valid, if I visit /etc/localtime in Emacs, I get a buffer of binary data that looks like a timezone file.

Unfortunately, this:
  zdump -v -c 2008 'US/Eastern' | grep 2007
still returns this:
US/Eastern  Sun Apr  1 06:59:59 2007 UTC = Sun Apr  1 01:59:59 2007 EST isdst=0 gmtoff=-18000
US/Eastern  Sun Apr  1 07:00:00 2007 UTC = Sun Apr  1 03:00:00 2007 EDT isdst=1 gmtoff=-14400
US/Eastern  Sun Oct 28 05:59:59 2007 UTC = Sun Oct 28 01:59:59 2007 EDT isdst=1 gmtoff=-14400
US/Eastern  Sun Oct 28 06:00:00 2007 UTC = Sun Oct 28 01:00:00 2007 EST isdst=0 gmtoff=-18000

...and does running zdump with 'America/New_York'.  It -should- return dates of March 11 and Nov 4.

I tried rebooting with that configuration; no difference.

Help?  I do NOT want to have to completely update the machine!  Is there some way to get libc to actually -look- at these timezone files, or have I missed a step somewhere?

Thanks!

---

