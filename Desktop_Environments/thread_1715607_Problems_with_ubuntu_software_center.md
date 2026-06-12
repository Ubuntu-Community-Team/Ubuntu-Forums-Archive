---
title: "Problems with ubuntu software center"
date: 2011-03-27
forum: Desktop Environments
---

### Post by maxmiaggi on 2011-03-27
Hello everyone..

I am new to ubuntu. I recently installed it in my laptop in a separate partition. And since then, whenever I try to download and install any software from the ubuntu software center, it asks for authorization, and then, the following message pops up:

_Requires installation of untrusted packages_
The action would require the installation of packages from not authenticated sources.

And then, when I click OK, it simply cancels the operation.

Im sorry if this is the wrong place to post this, but I am helpless.. I cannot install even a single software in my new ubuntu... :(

---

### Post by wangsuda on 2011-03-27
Did you go to software sources and check on the universe, multiverse, and restricted packages? If you haven't, go to System>Administration>Software Sources and check them. That should solve your problem.

---

### Post by Frogs Hair on 2011-03-27
The software center will ask for authorization prior to installation for you own protection.

---

### Post by Copper Bezel on 2011-03-27
@ wangsuda - Software Sources is launched from the Software Center now, under the Edit menu. There's no separate entry in Administration under, IIRC, 10.04 onwards.

@ Frogs Hair - He's saying that it's coming up for every package, that it's giving him a very specific warning, and that it's cancelling the operation even when he selects "OK". Under normal circumstances, the Center is just going to ask for a password before applying any action. 

Untrusted *sources* happen when you add a PPA without fetching the key, and I've seen the Update Manager refuse to continue for this reason, but reading every package from the ordinary repos as untrusted? That's a little weird. And if the Universe and Multiverse repos weren't checked, their packages wouldn't be showing up in the Software Center at all.

maxmiaggi, try installing something, anything, from the terminal, like, say 

> sudo apt-get install krita

and post your results. Could we also get a screenshot of the error message you get when trying to install a package from the Software Center? Is there a "details" arrow?

---

