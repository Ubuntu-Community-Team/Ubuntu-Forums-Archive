---
title: "quick synergy not working, workspace issue? or?"
date: 2011-05-21
forum: Desktop Environments
---

### Post by Berto Miguel on 2011-05-21
I am running Ubuntu 11.04 on two machines; older dell desktop and an acer laptop. I have loaded quick synergy on both but can't get it to work. I have followed the install guides using proper server/client names in appropriate boxes etc. Removed and re-installed and still no luck. One question does multiple work spaces which seems to be a default setting interfere with quick synergy? Maybe there is an easy explanation to this problem but I haven't found one so far and have been searching the net for a couple of days. Some ideas would be appreciated. Thanks.

**Still searching for a solution, re-installed synergy. Could the problem be in identifying location of synergy files?**

---

### Post by Twicks on 2011-07-03
I'm having the same issue trying with one laptop running 11.04 and one desktop running #!.

---

### Post by Cas07 on 2011-09-25
I just installed Quick Synergy on Natty and Oneiric machines, initially with no joy and no feedback as to the problem. However running the program from the terminal will spew out a lot of info about the synergy connection and in my case I had the following error:

```
Error: a client with name "....." is not in the map
```

From this error I found on the Synergy [troubleshooting guide]("http://synergy2.sourceforge.net/trouble.html#problem6") that using an IP address in Quicksynergy on the server (Share tab) was the issue and switching to client hostname fixed this.

Hope this might help.

---

