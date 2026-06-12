---
title: "Commands to Rescue a Full Disk"
date: 2006-01-25
forum: Desktop Environments
---

### Post by squidward on 2006-01-25
I had the "lasted less than 10 seconds login" error.  Tried another username, same result.  Tried fail safe and terminal, no joy.

Loaded a [rescue CD]("http://www.sysresccd.org/"), found that the disk was full.  I haven't done anything else yet.

Not surprised there.  I installed Oracle about 2 weeks ago, and I bet dimes to donuts there is a runaway log file that ate up the disk.  Ya think?

Assuming the problem is some run-away log, what are the Linux commands one would enter from grub or the rescue CD command line to:

1.  search for the biggest files
2.  free the space they are consuming

My command line Linux work is Freshman level.  But getting better...

Any other advice, if you think I'm going to wrong way would be appreciated.  I'll check this post tonight.

---

### Post by dcstar on 2006-01-25
[QUOTE=squidward]I had the "lasted less than 10 seconds login" error.  Tried another username, same result.  Tried fail safe and terminal, no joy.

Loaded a [rescue CD]("http://www.sysresccd.org/"), found that the disk was full.  I haven't done anything else yet.

Not surprised there.  I installed Oracle about 2 weeks ago, and I bet dimes to donuts there is a runaway log file that ate up the disk.  Ya think?

Assuming the problem is some run-away log, what are the Linux commands one would enter from grub or the rescue CD command line to:

1.  search for the biggest files
2.  free the space they are consuming

My command line Linux work is Freshman level.  But getting better...

Any other advice, if you think I'm going to wrong way would be appreciated.  I'll check this post tonight.[/QUOTE]
Clean out all of /tmp and selected /var/log files, that should help to start with.

---

### Post by heimo on 2006-01-25
See this thread for lots of information about using shell:
[http://www.ubuntuforums.org/showthread.php?t=73885](http://www.ubuntuforums.org/showthread.php?t=73885)

You could use find with correct flags to find largest files, but if you suspect log files, personally I'd just mount the disk and check log file sizes under /var/log directory. Hopefully my quick reply helps at least a bit. :)

---

### Post by heimo on 2006-01-25
[quote=dcstar]Clean out all of /tmp and selected***** /var/log files, that should help to start with.[/quote] 
Holy goodness. Personally I'd never do that - but of course your mileage may vary. :) (nothing personal) log files are valuable and may reveal the original cause for the filling disks - just deleting log files will probably make it happen again. Move those files to another disk / usb stick, if possible - or at least check them before removing. :) (I believe dcstar agrees and just wrote the advice in a hurry. [-o<)

:p

EDIT: *****) Oh... I was the one in hurry. I thought you were suggesting to remove whole /var/log. Anyway, check any log files before truncating / removing. Especially if it's a production machine.

---

### Post by dcstar on 2006-01-25
[QUOTE=heimo]Holy goodness. Personally I'd never do that - but of course your mileage may vary. :) (nothing personal) log files are valuable and may reveal the original cause for the filling disks - just deleting log files will probably make it happen again. Move those files to another disk / usb stick, if possible - or at least check them before removing. :) (I believe dcstar agrees and just wrote the advice in a hurry. [-o<)

:p[/QUOTE]
Log files are data, data that most users either don't know about or don't care about as useful information.

If people don't have log rotation enabled, they can end up with megabytes of useless log files filling up their disks.

I have seen mission critical Unix systems die because of redundant log files, and it is hard to justify their existence in that circumstance for whatever "academic" reasons.

If you don't use 'em, get rid of 'em (especially if you have no disk space).

---

