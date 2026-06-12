---
title: "Xara Xtreme not printing!!!!"
date: 2007-02-19
forum: Desktop Environments
---

### Post by kenquad on 2007-02-19
Hi all:

My Dapper box is set up to access a Windows shared printer-an HP 1022-and can print text to it from Gedit.  However, when I try to print anything from Xara Xtreme, carefully selecting the correct printer, the job does not even show up in queue!!  Anybody got any ideas where I should start debugging this?

Thanks a bunch,
Kenquad

---

### Post by thewump on 2007-02-19
Is anything in this thread helpful?

[http://www.talkgraphics.com/showthread.php?t=25450](http://www.talkgraphics.com/showthread.php?t=25450)

If not,  post to that forum.

Best

Keith

---

### Post by kenquad on 2007-02-19
Keith:

Thanks for your help.  I would have posted to the Xara forum, but thought this was more an Ubuntu issue.  Turns out it was a little of both.  Your thread didn't directly answer my question, but it did make me think to try running Xara with a terminal in the background to capture the error, if any.  Lo and behold:
```
no default destination
```
Setting the desired printer as default dissolved the error!  Sounds silly to me, but it worked.

Kenquad

---

