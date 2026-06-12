---
title: "Thunderbird mailer fails to exit"
date: 2012-08-08
forum: Desktop Environments
---

### Post by wcorey on 2012-08-08
Ubuntu 12.04. It isn't all the time but it did just started to happen within the last couple of days. Sometimes it shuts down normally and others it hangs and if/when it does terminate the process is still running. After killing the process the symlink lock file is gone but not the .parentlock file needs to be manually removed. This is also Thunderbird 14 that was automatically upgraded in a periodic update push from Ubuntu.  In both cases it is Ubuntu Desktop 64bit. I say both cases because this is occuring on two machines, one desktop one laptap. They share a common NFS profile automounted. Clearly I can only be logged on from a single location at a time and this has worked beautifully for probably over a year now.

This could be related to a lockd issue which is the only smoking gun I've seen related to this issue.

---

