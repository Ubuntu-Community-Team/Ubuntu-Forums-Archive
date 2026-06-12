---
title: "VMWare Workstation on 7.04"
date: 2007-04-27
forum: Desktop Environments
---

### Post by merlinus on 2007-04-27
Will this work?  The vm site does not list feisty, and says that support for 6.10 is untested.

I only need it to run one windows app that wine cannot handle.

Thanks.

-merlin

---

### Post by steve0921 on 2007-04-27
I have an installation of VMware server which worked on edgy. A quick look at getting that to work and an internet search when it didn't was a little enlightening.

Apparently it is difficult in feisty to get modules to compile on the newer kernel. It looks possible though (I'll know better in a bit).

---

### Post by steve0921 on 2007-04-27
Hmm,

It was actually a lot easier than expected. Somebody has made some patched module code that worked immediately for me. Try looking at [this guide]("http://icanthack.com/?p=53").

While it discusses vmware server, I am assuming that (unless you just want to install that) for workstation the new code trick is otherwise the same.

---

### Post by lw5 on 2007-04-27
I'm running VMware Server here as well. It needs a patch for Feisty which is also described [_here_](http://ubuntuforums.org/showthread.php?p=2384779#post2384779)

---

### Post by ravenon on 2007-04-27
Just an FYI, I have Vmware Workstation 6.0 RC running on Feisty 64bit without a hitch. I think 6.0 is due out as a release in May.

---

