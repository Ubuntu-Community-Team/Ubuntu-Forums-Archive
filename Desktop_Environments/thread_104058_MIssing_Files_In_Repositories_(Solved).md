---
title: "MIssing Files In Repositories (Solved)"
date: 2005-12-15
forum: Desktop Environments
---

### Post by dragonfyre13 on 2005-12-15
I already solved this, for any of you good samaritans out there. Perhaps you could comment if you had the same problem, what you did to fix it, what caused it, etc.

Basically, every time I loaded up synaptic, or used apt-get, I couldn't find half the files that were in the repos. I found this out when I tried to load gDesklets. The data files were there, but the actual application wasn't. I ended up compiling it from source, (nearly putting my fist throught the screen a few times) and then I went on my merry way. I figured that the Repo was down, and searched the forums for a notice to that effect. Nothing. Then, I figured that it was a problem with the proxy. (I'd had trouble before)

I manually configured apt-get for a proxy server, and removed the proxy in synaptic, which didn't fix the problem. I had installed easy ubuntu, easy breezy, and automatix, had a few problems, but all in all it worked out.

I was going through the repos the other day, looking for an updated radeon driver, and, lo and behold, nothing was there for radeon. No drivers, applications, nothing.

I disabled the universe, and multiverse repos, and everything other than the already installed files dissapeared! GAHHH!

----------SOLUTION----------

GUI SOLUTION (No Terminal)

I went into Synaptic-->Settings-->Repositories, and removed (select repo group, and click remove)  ALL repositories. Then, I left the repositories window, (OK button) and let it reload the repos. For good measure, I clicked the reload button up at the top left. 

Go to Synaptic-->Settings-->Repositories, and click add. When it asks you what to add, select the repos you would like, and click ok. Click OK again, on the repository window, and then let it reload. Click reload for good measure.

YAY! They are all back!

----------WHY?---------

I would assume that this happened because of one of the three configuration tools. (Easy breezy, Automatix, or Easy Ubuntu) but I don't know which one, or whether it was a combination of multiple. Those are the only files that I installed that mess with my repo configuration. I hope to be able to track this down, when I have a bit more time.

---

