---
title: "Evolution w/spamassassin does not work"
date: 2006-10-04
forum: Desktop Environments
---

### Post by fdisque on 2006-10-04
I have switched from Fedora Core to Ubuntu and like it except for the fact that the spam filtering in Evolution does not work.  One post said to enable spamassassin and another said to disable it and let Evolution call it.  Neither setting worked.  I also saw that you should install bogofilter, which I did, but still no luck.  I know that this can work because I was using it in Fedora for a few years and it works great.  ](*,) I am running 6.06.1.

---

### Post by fdisque on 2006-10-05
Found the answer for me in a development discussion:

[http://www.ubuntuforums.org/showthread.php?t=131782&highlight=spamassassin+evolution+bogofilter](http://www.ubuntuforums.org/showthread.php?t=131782&highlight=spamassassin+evolution+bogofilter)

In short, uncheck bogofilter in Edit-> Plugins in Evolution.

Now spamassassin is the resource-sucking, spam-destroying program that I have grown to love.:p  I still don't have an explanation for why it didn't work before I installed bogofilter, but problem solved.

---

