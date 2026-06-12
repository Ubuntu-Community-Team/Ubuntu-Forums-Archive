---
title: "Black screen/mouse after logging in"
date: 2009-09-22
forum: Desktop Environments
---

### Post by quixentric on 2009-09-22
Hello,

I randomly started having a problem after logging in to a machine in one of our labs at my university. After logging in, the screen goes black and the mouse appears, but nothing happens. I can change to alternate terminals using Ctrl+Alt+F#, and after looking through some forum threads, I restarted gdm on the local machine and was able to login successfully and get to my desktop. This is obviously one fix, but I do not want to have to do this every time. auth.log doesn't tell me much, the statements its outputting are the same for the successful and failed logins. It is not computer specific, as it happens in all of the computers in the lab, and no other users appear to have the same problem. 

I have run through the situation hundreds of times in my mind, and I cannot think of anything I was doing beforehand to cause this. I figure it can't be an issue with an update, since that would affect multiple users or multiple users on one machine, so I'm wondering if somehow a configuration file of mine got screwed up somewhere along the line. Any help would be greatly appreciated, I can post relevant log files if needed.

In case it's relevant, the machines are running Ubuntu 9.04, kernel version is 2.6.28-14, and the server specs are the same. It's an NIS server using NFS.

Thanks.

---

### Post by quixentric on 2009-09-23
*nudge*

If I can't find a solution in the next couple of days, I'll simply just create a new account. I'd like to avoid that, however.

---

