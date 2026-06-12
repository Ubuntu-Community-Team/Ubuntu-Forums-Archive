---
title: "Can I change date/time format for dmesg?"
date: 2006-07-10
forum: Desktop Environments
---

### Post by jonrkc on 2006-07-10
Since installing Dapper, my output from dmesg looks like this:

```

[17179592.760000] it87: Found IT8705F chip at 0x290, revision 3
[17179592.800000] it87-isa 9191-0290: Detected broken BIOS defaults, disabling PWM interface
[17179592.936000] Adding 1124508k swap on /dev/hda5.  Priority:-1 extents:1 across:1124508k
[17179593.100000] NET: Registered protocol family 17
[17179593.172000] EXT3 FS on hda1, internal journal
[17179593.532000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com

```
It used to show the date and time in human-readable format, instead of the number of seconds since the beginning of time, or whatever the reference point is on that format.

I have tried to find how to change an option so that I can read the time and date of the actions again, but the man pages don't seem to give that information.

Can somebody tell me how to get the date and time readable again?

Thanks in advance!

---

