---
title: "edit from terminal doesn't do anything."
date: 2007-07-25
forum: Desktop Environments
---

### Post by xl_cheese on 2007-07-25
When I type:

"gedit filename"

nothing happens.  I can go to the file browser and open with text editor, but if I need sudo permission that is no good.  Plus it's slow having to mouse click.

Any ideas how to fix it?

thanks.

---

### Post by FuturePilot on 2007-07-25
Make sure you put the file path in. Like ```
gedit /file/path/file.txt
```
And if you need root permissions to edit the file just stick "gksudo" in from like so
```
gksudo gedit /file/path/file.txt
```

---

### Post by xl_cheese on 2007-07-25
> **FuturePilot said:**
> Make sure you put the file path in. Like ```
gedit /file/path/file.txt
```
And if you need root permissions to edit the file just stick "gksudo" in from like so
```
gksudo gedit /file/path/file.txt
```

yep, I've been doing that.  It is not a permission issue.  

thanks.

---

### Post by xl_cheese on 2007-07-26
I did some searching and found another with the same problem.  I deleted the /tmp/gedit* file and am now able to open for read, but cannot open as root.  It just hangs when I try to open files via sudo.

hrm.

---

### Post by xl_cheese on 2007-07-26
maybe this is related to  this?
[http://ubuntuforums.org/showthread.php?p=3086801#post3086801](http://ubuntuforums.org/showthread.php?p=3086801#post3086801)

I can't get any games to work on my machine.  

ps -u  show that some of the games are running.  However I don't see them on the screen.

Could this also be the reason that when I restart xserver I can't log back onto my system?

What a load of problems this is becoming.

---

