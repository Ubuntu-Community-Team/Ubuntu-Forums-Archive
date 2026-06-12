---
title: "Please look at my streamripper settings"
date: 2006-07-13
forum: Desktop Environments
---

### Post by lonelypauly on 2006-07-13
i know i totally bollocks'd this up...the terminal opens and rips streams but no files appear in the directory i have setup...help?

here's what i have now:

[IMG]http://i6.photobucket.com/albums/y215/lonelypauly/streamripper.jpg[/IMG]

---

### Post by T700 on 2006-07-13
Try this:

```
x-terminal-emulator -e streamripper %q -d /home/paul/Desktop/StreamripperFiles -r -q
```

Paul

---

### Post by lonelypauly on 2006-07-13
yay! you da man...thank you!

---

### Post by T700 on 2006-07-13
Hey, least I could do for another Paul.  :-)

Paul

---

### Post by Mtnear on 2006-07-23
Thanks T700, I had been looking for this same answer for some time.  Cool.

---

