---
title: "KDM what is 'Failsafe' mode?"
date: 2008-05-25
forum: Desktop Environments
---

### Post by r1chard on 2008-05-25
I have an interesting problem which follows from a system hang, where I had to do a hard reset, when I start my KDE session from KDE, the screen goes blank, then I am returned to the log in prompt. If I start in failsafe mode, I can 'startkde' and get the system up, minus some things (at least, I have noticed special keyboard keys no longer work). The problem occurs with both a new user set up after the initial crash for testing, and for my normal user account.

Anyway... at the moment I've got a few bits of information I am trying to piece together to debug... so my question...

What is **failsafe mode**, and why would starting KDE from the failsafe mode console using **startkde** from that mode would yield a different result to starting KDE directly from KDM?

If I can work out the difference between the two KDM session start-ups, I figure I am on my way to working out what causes the problem where the directly started KDE session fails.

Thanks
Richard

---

### Post by r1chard on 2008-05-25
OK... all solved... 

~/.xsession-errors held the clue.

I was then able to remove items one at a time from the /etc/X11/Xsession.d directory until I the KDE session started correctly.

I had to remove the file /etc/X11/Xsession.d/98vboxadd-xclient - I had actually removed VirtualBox during troubleshooting, though this file remained. I'll probably need to add that back again, and work out why it causes the issue, but for everything else is back in order.

Cheers
Richard

---

