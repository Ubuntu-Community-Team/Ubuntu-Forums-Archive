---
title: "Stress Test"
date: 2009-04-27
forum: General Help
---

### Post by Iosys on 2009-04-27
When building systems, I've always used programs such as HLoad and Sandra to stress test at least the CPU, GPU and RAM over a 24 hour period before shipping.  I'm recently moving away from M$ and I've been happily using Ubuntu (Jaunty now) so far.  However, I'm was wondering if there are any catch-all apps in Linux (particularly for Ubuntu/Gnome) that will serve the purposes of the aforementioned Windows-based apps?  I've found tidbits of information in various spots but no solid answers so far, so figured it might be quicker just to post here.  If this has been covered ad nauseum, forgive me!

---

### Post by Iosys on 2009-04-27
bump!

---

### Post by mb_webguy on 2009-04-27
Please wait 12-24 hours before bumping your own post.  Trust me, even if your post drops down to page 10 or so, it will still be seen.  I start on page 15 every time I come to the forums and work my way forward.

Anyway, in regards to your post, there are a number of Linux commands that can do some of the same things as those programs.  "top" and "free" can show current system resource use.  "cat /proc/cpuinfo" and "cat /proc/meminfo" will show you info about your CPU and memory.  "hdparm -tT /dev/*xxx*" can be used to test a hard drive.  I could keep going, but I think you get the idea.

If you want an application that brings all of these into one place, then you might want to look at the [Phoronix Test Suite]("apt://phoronix-test-suite"), which is in the repositories.

---

### Post by Wiebelhaus on 2009-04-27
```
Sudo apt-get install hardinfo
```

This has some CPU Stress tests like blowfish. You have to create a shortcut for it which kinda gay but it takes like 5 seconds , in the "command line" section just type the name of the application in this case it would be "hardinfo" and all the other info you can type whatever you want. 

See I already have it installed but you get the point.

---

### Post by mb_webguy on 2009-04-27
hardinfo isn't as full-featured as Phoronix Test Suite, but it's pretty good for simple benchmarking of hardware.  One thing about it, though, at least on Jaunty...  It looks for zlib in /lib instead of /usr/lib, which throws an error on the CPU ZLib benchmark.  The easy fix is to create a symlink in /lib.```
sudo ln -s /lib/libz.so.1 /usr/lib/libz.so.1
```

---

### Post by Cope57 on 2009-04-27
[LIST]
[*][hdparm]("http://sourceforge.net/projects/hdparm/").

[*][Bonnie++]("http://www.coker.com.au/bonnie%2B%2B/").

[*][IOzone]("http://www.iozone.org/").

[*][Dbench]("http://freshmeat.net/projects/dbench/?topic_id=836%2C138").

[*][Bonnie]("http://www.textuality.com/bonnie/").

[*][IO Bench]("http://manpages.ubuntu.com/manpages/intrepid/man1/tiotest.1.html").

[*][Nhfsstone]("http://nfs.sourceforge.net/").
[/LIST]
Xmark, x11perf, and x11perfcomp, tools for benchmarking graphical operations under the X Window System, are available in [x11-apps]("http://packages.ubuntu.com/search?searchon=names&keywords=x11-apps").

I am sure there are more benchmarking utilities, I just have not Googled any...

---

### Post by Iosys on 2009-04-27
Hey thanks guys!  I'll definitely check out Phoronix, looks like what I need!  Also I'll make sure to wait when it comes to bumping - I didn't realize how busy these forums actually get.  Thanks for the replies!

---

