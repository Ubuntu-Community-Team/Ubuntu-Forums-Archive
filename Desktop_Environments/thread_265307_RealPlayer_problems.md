---
title: "RealPlayer problems"
date: 2006-09-25
forum: Desktop Environments
---

### Post by fritz_monroe on 2006-09-25
RealPlayer has stopped working for me.  It used to work just fine, that was a little more than a month ago.  XMMS works fine.  VLC works fine.  However, RealPlayer doesn't play any sound.  It appears to be playing, but no sound at all.

edit: I'm running 6.06 and Gnome.  I've found that if using 2.6.15-25-386, RealPlayer works just fine.  But when launching into 2.6.15-26-386 or 2.6.15-27-386, RealPlayer doesn't work.  I do have the system tell me when updates are available.  I usually upgrade all the time.

Any suggestions?

Thanks

F_M

---

### Post by stevieb on 2006-09-25
I found that if a process called "esd" is running, sound  doesn't work for realplayer.  here's how to fix this:
```
foo@bar$ ps aux|grep esd
steve     4717  0.0  0.1   5936  1004 ?        SL   Sep24   0:00 /usr/bin/esd -nobeeps
steve    15261  0.0  0.1   2880   812 pts/0    S+   22:10   0:00 grep esd
foo@bar$ kill 4717

```

the process #15261 doesn't need to be killed; that's just showing up as a repeat of the original "grep" command.

this is a case-by-case fix- something you have to do every time it happens; there's something posted somewhere about making this a permanent fix, but i can't find it again, and it didn't work for me anyway.

there could be several things that trigger this; one i found was previewing audio files by moving the cursor over the file icon.  this can be turned off in the file manager window.

hope this works for you; let us know either way!
-steve

---

### Post by fritz_monroe on 2006-09-26
I was all set to kill esd to get it working and I didn't need to do it.  I booted into 2.6.15-27-386 and it played just fine.  I guess I could set the shortcut up to automatically stop the esd app.

I can string together a bunch of commands, right?  I'm having problems finding how to ignore the ps and I don't recall how to select just the 2nd field.  I can do the following to push together the fields to they are all seperated by a single space.  But how to do the rest?

```
ps -ef |grep /usr/bin/esd |tr -s ' '
```

---

