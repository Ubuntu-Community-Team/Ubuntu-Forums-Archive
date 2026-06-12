---
title: "System crawls when running archive manager"
date: 2009-05-01
forum: General Help
---

### Post by AdamGott on 2009-05-01
This problem has been ongoing since I installed Ubuntu (7.something).  Every time I do a batch de-compress to the same directoy in which the files reside the other applications running on my computer are nearly unusable.  The worst culprit is FIREFOX as it stays 'grayed out' for almost the entire extract operation.

I have an AMD64 4600+ with 6 gigabytes of RAM so I don't think it is my computer.  I have a couple of applets running to watch CPU usage and sometimes one of them maxes out but not very often.

Any suggestions?  Maybe some kind of setting to make archive manager run with a lower priority?

---

### Post by AdamGott on 2009-10-23
I switched from "unrar" to "unrar-free" and it seems to have helped a little but if I am unraring a large group of files my web browser (firefox) becomes inactive (greys out) for time periods during the unrar process.  

Any suggestions?

---

### Post by alphaniner on 2009-10-23
Do you have the same performance hit if you use the terminal to extract?

If using a different module made a difference, maybe try yet another one: p7zip-full + p7zip-rar.

Check your logs right after an extraction to look for possible problems.

Sorry, that's all I got.

---

### Post by AdamGott on 2009-10-30
Thanks for the help.  It seems that this problem has been somewhat alleviated with 9.10 (although I now have a new set of problems!).  I don't know what it was and I could never seem to trace it down but I can now use firefox (and do other things) at the same time I am extracting files.

---

