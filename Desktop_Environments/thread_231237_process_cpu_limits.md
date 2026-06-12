---
title: "process cpu limits?"
date: 2006-08-07
forum: Desktop Environments
---

### Post by kreso on 2006-08-07
I'd like to run long tasks like compiling an app, or encoding video, but I'm not in a hurry and I would like to prevent overheating.

thusly, I'd like to set a limit to a specific process, limiting the max amount of cpu time it uses (not by setting low priority :)


I have cpu freq scaling so my cpu is cool most of the time, however, when I run such long processes, it really heats up..

---

### Post by h00s on 2006-08-07
Try this:
[http://marlon80.interfree.it/cpulimit/index.html](http://marlon80.interfree.it/cpulimit/index.html)
and
[http://www.ubuntuforums.org/showthread.php?t=157133](http://www.ubuntuforums.org/showthread.php?t=157133)

Pozdrav!

---

### Post by kreso on 2006-08-07
I've tried this but I cant get it to work:

# cpulimit make 40
 Error: You must specify a target process

$ cpulimit -e make -l 40
 Warning: no target process found. Waiting for it...

---

### Post by h00s on 2006-08-07
Try something like this:
$./cpulimit gedit 55

---

