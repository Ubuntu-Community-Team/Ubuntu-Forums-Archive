---
title: "Going from Unity 14.04 to Cinnamon generates error msg."
date: 2015-11-15
forum: Desktop Environments
---

### Post by cmmichael on 2015-11-15
Unity dash crapped out on me, so I installed Cinnamon - all seems to be working except I get an error message when I start up.
Selected lines from the message:

Executable Path
   /usr/bin/unity-greeter
Problem Type
   Crash
Architecture
   i386
Distro
   Ubuntu 14.04
ProcCmdline
   /usr/bin/unity-greeter
ProcCwd
   /var/lib/lightdm
ProcEnviron
   PATH=(custom, no user)
   XDG_RUNTIME_DIR=<set>
   LANG=en_US.UTF.8
   SHELL+/bin/false
Signal
   6
Uname
   Linux 3.13.0-68-generic i686
UnreportableReason
   This problem report is damaged and cannot be processed.

   EOFError('Compressed file ended before the end-of-stream marker was reached')

---

### Post by ian-weisser on 2015-11-17
Look in /var/crash for a corresponding crash file to that report. Delete the crash file (or move it out of that directory). Restart.
Does the same error message recur?

---

