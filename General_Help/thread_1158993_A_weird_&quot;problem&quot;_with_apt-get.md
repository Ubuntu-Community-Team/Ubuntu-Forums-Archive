---
title: "A weird &quot;problem&quot; with apt-get"
date: 2009-05-14
forum: General Help
---

### Post by Onizuka89 on 2009-05-14
Tried searching for a similar problem on the forum but didn't find anything.

The "problem" started a few weeks ago with the update manager, after it had downloaded the sources and was going to read them so it could tell me which new updates was available if there were any, and after that it used about 50 sec to actually start reading it.

Later I found out that I could save myself some time from that, by go into the Terminal and type "sudo apt-get update" and then open the update manger and take it from there, but now, it seems like the apt-get commands are acting up over getting the sources :(  it used to minutes to finish and a heck of a long time to start downloading the sources, and I have tried a couple of times on the Norwegian server and once on the main server, but the "problem" won't go away. Anyone know how to fix this?

As for the system I am running Ubuntu 9.04.

---

### Post by whoop on 2009-05-14
Looks like you have problems connecting to the repository. Did you try "select the best server" in "software sources"?

---

### Post by Onizuka89 on 2009-05-14
Nope, but I tried it now and it seems to work excellent ^^
thanks a lot ^^
It made me worry a lot since it seemed like such a bad problem, you really brightened my day ^^

---

