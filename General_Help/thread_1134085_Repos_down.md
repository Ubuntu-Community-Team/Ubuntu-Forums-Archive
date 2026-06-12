---
title: "Repos down?"
date: 2009-04-23
forum: General Help
---

### Post by Haise on 2009-04-23
I can't hit any of the archive.ubuntu.com repos, and I can only get a few of the localized ones.

Is anyone else having this problem?  I've been waiting for the release quite eagerly, but...

---

### Post by stwschool on 2009-04-23
Yeah looks like the servers are taking a hammering. I'm on Jaunty from the release candidate and loving it btw, it's very clean and stable.

---

### Post by lewtwo on 2009-04-23
Same problem here .... I wonder if the repos are over run by people trying to upgrade to 9.x ..... H'mmmm I am thinking I might want to wait a while now (maybe a a month or so).

---

### Post by dt_ on 2009-04-23
Same problem here. Glad to hear it's not something only on my end.. hopefully they fix it soon :)

---

### Post by paradigm2 on 2009-04-23
> **lewtwo said:**
> Same problem here .... I wonder if the repos are over run by people trying to upgrade to 9.x ..... H'mmmm I am thinking I might want to wait a while now (maybe a a month or so).

It is probably just being pounded now. Apparently this was almost expected.  If you can you will probably be better off waiting a day or two at least, yes.

---

### Post by LowSky on 2009-04-23
if you can try to do you upgrading or whatever you need the repos for, around 3-4am Eastern Standard time, that way the US is off to sleep and not downloading as much.

Or switch your sources to use an other list of servers

---

### Post by paradigm2 on 2009-04-23
I'm noticing that even if you can get through, speeds are usually no more than 20 kB/s.  Usually it is at least five times faster.  It might indeed be a good time to wait.

In thinking about this, perhaps this shows that we need to come up with a better integrated p2p type solution for holding repositories.

In brainstorming, we already have keys and hashes to protect against file alteration.  We could use a more distributed system having a core of main servers merely keep track of who has the most recent versions and proper hashes.  The server could then refer the client to another distributed server 
(actually provide a list - much like a bt tracker) for the actual download.  It sounds a lot like bit torrent because it pretty much is, but in a more modified form to accommodate the repository system.

Perhaps this is something to bring up in the brainstorm section.  I know we already have iso's available over bit torrent but it would be nice if there were a way to integrate it with the package managers so that we could also get our updates over distributed p2p (bit torrent) shares too.
It would take a lot of load off of those servers...

---

### Post by Jimmynemo2 on 2009-04-23
Glad I found this thread. I guess that explains why my update manager keeps hanging on the update servers.

Whew, and I was afraid it was me.

---

### Post by zak89 on 2009-04-24
Does anyone know where to find a list of mirrors for the Ubuntu Jaunty repos? I need to install Kate for my work and I can't get through.

---

