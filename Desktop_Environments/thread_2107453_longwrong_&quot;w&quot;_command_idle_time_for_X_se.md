---
title: "long/wrong &quot;w&quot; command idle time for X sessions"
date: 2013-01-21
forum: Desktop Environments
---

### Post by devurandom77 on 2013-01-21
Figured I'll ask here before doing a bug report...

**Symptom:** "w" reports indefinitely increasing idle time for X users since last boot (idle times for text console logins are normal).

**Cause:** atime on /dev/tty7 that X is on is not getting bumped.

**Suspected cuplrit:** Xorg

**Config:** 12.04.1 w/ slim display manager and fvwm window manager via traditional Xsession setup.

I first noticed some problems after upgrading to 12.04 from 8.04 when idle times would intermittently not update (and hence continue to grow).  I had originally faulted console-kit, as I seem to recall restarting console-kit-daemon fixed the issue, as would a reboot.  Things appeared to work normally for months on end, though admittedly the only thing that would cause me to notice would be an idle time longer than 6 hours.

Now though, after installing updates the other day, the idle times reported by "w" continue to grow and never get reset.  Even after logging out and logging back in, the new login session will show idle times longer than the session was logged in (even as reported by "w").  I tried reverting package versions back, but now I can't reproduce a "working" setup that properly updates idle times.

The following appear to be working:
[LIST]
[*]ConsoleKit SystemIdleHint and ActiveSession update correctly.
[*]X idle time reported by XScreenSaverQueryInfo() is correct.
[*]Idle times reported on regular text consoles and /dev/pts/* are correct.
[/LIST]

On normal ttys, inode times are updated by the kernel on read() and write() calls.  As best I can tell, older versions of Xorg kbd driver would actually read() the tty for input (I verified on an old 8.04 box I have), hence updating the access time on the /dev/tty? inode that the X server is displaying on.  Now, however, Xorg appears to get its input via /dev/input/event* and then subsequently does a TCFLSH on the /dev/tty? device, which does not update atime or mtime as nothing was ever read or written.  For what it's worth, nothing else appears to be accessing the tty device, not even consolekit.

Given that back-reving my updates hasn't reproduced a working setup, I'm wondering if this is more nuanced (e.g. how the X core keyboard driver picks its input, leaving some of this up to chance and/or device enumeration order).


**Questions:**

coreutils still relies on the tty inode times to report idle information and this (may) be required by POSIX, so am I correct in assuming that tty inode times should be updated for X sessions?

Should the X server be responsible for bumping the times on the tty inode, in which case this is an Xorg bug?

Should TCFLSH result in a time bump (I doubt it), in which case this is a kernel bug?

Is this something that X needs a helper for (e.g. consolekit, or some other darned new piece of code)?

What are other people seeing reported by "w" for the X login session running other configs/versions?  If the idle time is updating correctly, what is updating it (kernel auditing/lsof/strace/inotify can help you find out)?


I haven't tried or looked at newer releases or the latest stock X, but I also haven't found anything searching the interwebs...

---

### Post by morrcahn on 2013-11-25
I don't have as in-depth a report as devurandom77, but I'm experiencing the same issue. Idle time continues to grow, seemingly resetting when idle time is around 6 days. Of course, the idle time is not correct, so the issue...? Yet to be determined. It's hard to use w to kick off users when its idle times are so far off. Running 12.04.

---

