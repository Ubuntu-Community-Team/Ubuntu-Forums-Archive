---
title: "Slow beagle search"
date: 2005-10-14
forum: Desktop Environments
---

### Post by josdebruijn on 2005-10-14
Hello,

I'm experiencing some problems with the beagle searches.
Most of the searches I do with the best tool take between 40 and 70 seconds. Actually, I already see the result after a few seconds, but there seems to be some processing in the back which hangs the best tool and which drains the CPU (CPU usage of the beagled mono process is maximal during that period).

These timeouts mostly occur with searches of more than 100 results.

The beagle terminal output looks something like:

Rendering
Done Rendering: 1.30s   [here the search results as shown]
Rendering
Done Rendering: 67.05s

My beagle index information:

Index information:

Name: EvolutionDataServer
Count: 1444

Name: Mail
Count: 42426

Name: KMail
Count: 0

Name: Files
Count: 21879

Name: GaimLog
Count: 1

Name: IndexingService
Count: 0

Name: Tomboy
Count: 2

Name: Blam
Count: 0

Name: Liferea
Count: 0

Name: Akregator
Count: 0

Name: Kopete
Count: 0

Name: Google
Count: -1

Name: NetworkedBeagle
Count: -1


Does anybody have a clue what's going on here?


Best, Jos

---

