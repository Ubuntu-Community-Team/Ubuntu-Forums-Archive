---
title: "Cedega leaving uninterruptible wine processes!"
date: 2007-03-22
forum: Gaming &amp; Leisure
---

### Post by MindSpore on 2007-03-22
First of all, I am on Feisty.. however I had the same issue under Edgy.  OK, so here's the deal.  I'm using Cedega to play Guild Wars (which works pretty well).  When I first open Cedega I can run Guild Wars no problem.  However; after I close Guild Wars (doesn't matter if I use the stop button or click on the X), it leaves the wineserver and wine processes and I cannot get rid of them.  I've even tried a kill -9 on the processes and they still persist.  Okay, so while those processes are there Guild Wars won't launch.  So I have to restart to be able to play again.  Hmmmm, and the reason I got Cedega was so I didn't have to reboot to play :P

Let me know any info that you'd want to help diagnose this, I have no idea where to begin.  I have no idea if this is a Cedega issue, Ubuntu issue, some other package issue.  Anyway, please help as this has been plaguing me for quite some time and I was hoping the Feisty upgrade might help.. but nope, so yeah this is frustrating.

---

### Post by psyke83 on 2007-03-22
Did you try "wineserver -k" (as sudo if necessary)?

---

### Post by MindSpore on 2007-03-23
yes, the wine and wineserver processes still persist

---

### Post by MindSpore on 2007-03-24
anyone?  i just want to know where to start to try to troubleshoot this problem.

---

### Post by psyke83 on 2007-03-24
MindSpore,

I don't use cedega here, but "wineserver -k" should kill all wine processes. Perhap cedega has renamed the command or it's in a non-standard directory. Check the output of "dpkg -L cedega" to see all the files installed by cedega, and see if you can find the wineserver.

I downloaded a .deb of cedega 4.3.2 (probably not legal, but I won't be using it) and took a look inside the archive - wineserver is installed to /usr/lib/transgaming_cedega/winex/bin/

So, if your version of cedega uses the same path, then try:

```
sudo /usr/lib/transgaming_cedega/winex/bin/wineserver -k
```

---

