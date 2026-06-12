---
title: "apt-get downloads stopping/freezing"
date: 2009-06-17
forum: General Help
---

### Post by TaylorHall on 2009-06-17
Whenever I try to do an apt-get install something or an apt-get upgrade, the downloads for the required components stops after about 100-300KB of data have been downloaded.

Regular wget works fine, and also downloading things from Firefox also works fine, but for some reason any downloads through the apt-get slow down and stop.

If you cancel the apt-get and restart it, the download will pick up where it left off and then download another 100-300KB and then stop again.  Also, if you leave it running, it will eventually download the package because it will eventually fail and restart itself.  Of course, at this rate it takes about 16 hours to download 20MB.  Not exactly useful.

One idea I had was that it could be a case of creating too many connections and messing up my router.  If that is the case, is there a way to limit number of connections apt-get can use?

Info:
- Linksys Wireless-G router,            Firmware v1.00.1,
- Mythbuntu  (Ubuntu 8.10)

Thanks in advance,
Taylor

---

### Post by inigomontoya on 2009-06-17
Have you tried a different mirror?

---

### Post by TaylorHall on 2009-06-17
how do you set that?

---

### Post by TaylorHall on 2009-06-17
okay, so I figured out how to change the mirror.  I changed it first to another http mirror, but it also did the same thing.  Then, I changed it to an ftp mirror, and it works fine now.  So, it's fixed in a way, but I'd still like to know why the http mirrors do not work?

---

