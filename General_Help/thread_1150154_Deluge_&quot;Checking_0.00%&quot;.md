---
title: "Deluge &quot;Checking 0.00%&quot;"
date: 2009-05-05
forum: General Help
---

### Post by FlashGordon2000 on 2009-05-05
I am on Ubuntu 8.10, and this is Deluge 1.16

Deluge doesnt want to check the files of torrents that have either finished downloading or are still downloading. This only occurs to torrents that are located on my internal drive, and the few on the external drive stay active.


Screenshot located here: [http://imgur.com/2cbB.png](http://imgur.com/2cbB.png)

---

### Post by mb_webguy on 2009-05-06
What version of Deluge are you using?  The one in the repos, or the one from the Deluge website (or PPA)?

---

### Post by FlashGordon2000 on 2009-05-06
>  and this is Deluge 1.16 

> **mb_webguy said:**
> What version of Deluge are you using?  The one in the repos, or the one from the Deluge website (or PPA)?
Deluge 1.16, and I got it from getdeb

---

### Post by katakaio on 2010-07-16
Ditto - same problem in 1.2.2 in Lucid from the repos. Any thoughts?

---

### Post by haafmaad on 2010-09-27
In my case starting deluge as root solves the problem.

try sudo deluge in the terminal.

Thanks

---

### Post by haafmaad on 2010-09-27
In my case starting deluge as root solves the prob.

try **sudo deluge** in the terminal

Thanks

---

### Post by mlg7 on 2011-10-30
Workaround:

1. pause, exit, run again, restart torrents
(not sure if this is of use, but I did that first)
2. remove one of the torrents and add it again. This torrent will work.
3. exit and run again
4. force recheck of the 0.00% torrents. This is where you see that the other torrents work too.

At least, this worked for me. Once.

deluge: 1.3.3
libtorrent: 0.15.7.0

---

### Post by oldos2er on 2011-10-30
Closed. Please do not bump old threads.

---

