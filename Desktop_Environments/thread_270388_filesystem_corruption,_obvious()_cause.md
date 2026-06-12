---
title: "filesystem corruption, obvious(?) cause"
date: 2006-10-03
forum: Desktop Environments
---

### Post by sreid on 2006-10-03
I've been getting filesystem corruption requiring manual fsck; minutes ago I had to recover a bunch of .gconf folders out of /lost+found. This is quite distressing, but I think I know the source of the problem...

I'm using ext3 with the default settings. I think what is happening is that I am having the occasional unclean shutdown, then when the system reboots it doesn't bother to fsck, it just replays the journal. Which is all well and good, except for this innocuous-looking line in dmesg:

hda: cache flushes not supported

So I guess the journal is not getting properly flushed, so unclean shutdowns cause corruption even with a journaled fs. I could accept that (I think it's unavoidable when the disk cache can't be flushed), except for the fact that it ought to be performing an fsck when it comes back up, but isn't. So the system continues to run with a corrupt FS, only performing an fsck when the mount count is reached.

Is there some way to force fsck when coming back up after an unclean shutdown, even with a journaled fs? And shouldn't that be the default when the hardware sucks?

---

### Post by sreid on 2006-10-03
I may have answered my own question. I've used "hdparm -W 0 /dev/hda" (and equivalent in /etc/hdparm.conf) to completely disable the drive's write caching. Hopefully that will work.

---

### Post by daverave999 on 2007-01-31
Did it work?

---

