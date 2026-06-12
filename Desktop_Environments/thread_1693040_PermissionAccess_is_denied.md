---
title: "Permission:Access is denied"
date: 2011-02-22
forum: Desktop Environments
---

### Post by ujjal on 2011-02-22
I am using ubuntu 10.10. when I am using Codeblocks IDE it says that, permission :access is denied. When I try to run e .cpp code it occures. I think permission is denied on my HDD. How to make all of my HDD permitted when in Ubuntu....

---

### Post by 3Miro on 2011-02-22
> **ujjal said:**
> I am using ubuntu 10.10. when I am using Codeblocks IDE it says that, permission :access is denied. When I try to run e .cpp code it occures. I think permission is denied on my HDD. How to make all of my HDD permitted when in Ubuntu....

You do not want to make "all of your HDD permitted". Permissions are a very important part of Linux security.

Where are the files for code::blocks? You should have files in /home/your_username/mkae_some_folder

---

### Post by ujjal on 2011-02-22
Well ,I have noticed that.I was finding it is possible or not.I got your points.thanks you...

---

### Post by deconstrained on 2011-02-22
Maybe your system is not configured to allow for attachment of debuggers.
[quote=/etc/sysctl.d/10-ptrace.conf]```
# The PTRACE system is used for debugging.  With it, a single user process
# can attach to any other dumpable process owned by the same user.  In the
# case of malicious software, it is possible to use PTRACE to access
# credentials that exist in memory (re-using existing SSH connections,
# extracting GPG agent information, etc).
#
# A PTRACE scope of "0" is the more permissive mode.  A scope of "1" limits
# PTRACE only to direct child processes (e.g. "gdb name-of-program" and
# "strace -f name-of-program" work, but gdb's "attach" and "strace -fp $PID"
# do not).  The PTRACE scope is ignored when a user has CAP_SYS_PTRACE, so
# "sudo strace -fp $PID" will work as before.  For more details see:
# https://wiki.ubuntu.com/SecurityTeam/Roadmap/KernelHardening#ptrace
#
# For applications launching crash handlers that need PTRACE, exceptions can
# be registered by the debugee by declaring in the segfault handler
# specifically which process will be using PTRACE on the debugee:
#   prctl(PR_SET_PTRACER, debugger_pid, 0, 0, 0);
#
# In general, PTRACE is not needed for the average running Ubuntu system.
# To that end, the default is to set the PTRACE scope to "1".  This value
# may not be appropriate for developers or servers with only admin accounts.
kernel.yama.ptrace_scope = 0

```[/quote]

Try this:
```
sudo echo 1 > /proc/sys/kernel/yama/ptrace_scope
```

---

### Post by asmoore82 on 2011-02-22
> **deconstrained said:**
> Try this:
```
sudo echo 1 > /proc/sys/kernel/yama/ptrace_scope
```

I can't comment on the fix, just the method: this won't work &#8212;
`sudo` elevates privileges of commands but not shell redirection.

For example:
```
**sudo wc /etc/shadow**
  43   43 1304 /etc/shadow
**sudo wc < /etc/shadow**
[COLOR="Red"]bash: /etc/shadow: Permission denied[/COLOR]
```

If this is indeed the right fix, then the right method is:
```
echo 1 | sudo tee /proc/sys/kernel/yama/ptrace_scope
```

---

