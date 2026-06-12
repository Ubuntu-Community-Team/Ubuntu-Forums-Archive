---
title: "Prevent GCALDaemon from sending out meeting accepts, high memory consumption"
date: 2009-02-13
forum: General Help
---

### Post by casanostra on 2009-02-13
Hi all,

Just installed gcaldaemon from [binwiederhier]("http://blog.philippheckel.com/2008/09/30/gcaldaemon-deb-package-for-ubuntu-kubuntu") excellent debs - it seems like they're going to be included in Jaunty, so I thought this would be the way to do it. I can't recommed this enough.

I face two problems, though, which I suspect are both particular to gcaldaemon in general.

1) First time I executed the sync-only-once script just to see how it worked. The script ran for several minutes before I noticed meeting accepts piling up in both my Gmail inbox and my work mail (Exchange). A few minutes later, coworkers started to complain that I was accepting meetings they had invited me to months ago. Oops.

I have been syncing my google calendar with my exchange calendar, which I access with Evolution and the exchange connector. I set it up using [this]("http://gisak.vsb.cz/gportal/index.php?option=com_content&view=article&id=947:%20&catid=232:interoperabilita") guide (in Czech, unfortunately). I guess gcaldaemon perceived the synchronized exchange meeting requests as new, and sent out answers to all of them. Strangely, all were answered with "tentatively accepted".

I don't want to risk running gcaldaemon before I'm sure it won't do this again. But how do I disable automatic replies to meeting requests?

2) At 100-200 mb even when not syncing, the daemon's memory usage seems out of proportion. I keep reading everywhere that it is supposed to have a much smaller footprint, as in 10-20 mb. Can anyone confirm this?

---

