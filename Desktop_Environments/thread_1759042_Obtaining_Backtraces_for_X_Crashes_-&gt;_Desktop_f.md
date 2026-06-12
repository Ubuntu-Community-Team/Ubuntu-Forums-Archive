---
title: "Obtaining Backtraces for X Crashes -&gt; Desktop freezes"
date: 2011-05-15
forum: Desktop Environments
---

### Post by cccc on 2011-05-15
hi

I try to do these steps according to:

[https://wiki.ubuntu.com/X/Backtracing](https://wiki.ubuntu.com/X/Backtracing)

and after ```

$ pgrep Xorg
5320
$ sudo gdb /usr/bin/Xorg 2>&1 | tee gdb-Xorg.txt
GNU gdb (Ubuntu/Linaro 7.2-1ubuntu11) 7.2
Copyright (C) 2010 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "i686-linux-gnu".
For bug reporting instructions, please see:
<http://www.gnu.org/software/gdb/bugs/>...
Reading symbols from /usr/bin/Xorg...Reading symbols from /usr/lib/debug/usr/bin/Xorg...done.
done.
(gdb) attach 5320
```the Gnome Desktop is freezing completely.

---

### Post by cccc on 2011-05-17
Knows someone what's wrong and howto solve this problem?

---

### Post by BenginM on 2013-04-13
Hi CC , nothing wrong there , you'll need to continue with steps as mentioned in the above link , in your case as the DE and [COLOR=#333333][FONT=Ubuntu Beta]X server is locked up you need to stop it with Ctrl+C , then in (gdb)  type " [/FONT][/COLOR][COLOR=#333333]backtrace full " .


[/COLOR]

---

### Post by overdrank on 2013-04-13
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/misc.php?do=showrules")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

