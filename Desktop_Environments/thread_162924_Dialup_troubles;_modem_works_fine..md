---
title: "Dialup troubles; modem works fine."
date: 2006-04-19
forum: Desktop Environments
---

### Post by VSFH on 2006-04-19
So my Ubuntu installation finally went all the way through, after resizing one of my harddrives. Data kept intact and everything.

Downloaded all the neccessary stuff with slmodem-breezy to get the modem working, and it works, however, I'm unable to actually get online; it gives me a NO CARRIER signal. Wvdial will report Username: 4 or so times and then say no carrier. I checked over chatscripts and changed it so it would be waiting for name:, but to no avail. pon won't run either; sometimes it comes to word: and then says no carrier. Ideas, anyone?

Apart from that, my installation has gone swimmingly. I was amazed that Ubuntu could resize my partition and leave all of the data intact. It was awesome, worried me for a minute when I selected 36.6 gigs, not realizing that that was used space, not unused space, for the partition.

Just got my other drive working, so here's the error I get, straight from a tail -f syslog

Apr 19 11:22:21 localhost pppd[9768]: pppd 2.4.3 started by admin, uid 
1000
Apr 19 11:22:22 localhost chat[9769]: abort on (BUSY)
Apr 19 11:22:22 localhost chat[9769]: abort on (VOICE)
Apr 19 11:22:22 localhost chat[9769]: abort on (NO CARRIER)
Apr 19 11:22:22 localhost chat[9769]: abort on (NO DIALTONE)
Apr 19 11:22:22 localhost chat[9769]: abort on (NO DIAL TONE)
Apr 19 11:22:22 localhost chat[9769]: send (ATZ^M)
Apr 19 11:22:22 localhost chat[9769]: expect (OK)
Apr 19 11:22:22 localhost chat[9769]: ATZ^M^M
Apr 19 11:22:22 localhost chat[9769]: OK
Apr 19 11:22:22 localhost chat[9769]:  -- got it
Apr 19 11:22:22 localhost chat[9769]: send (ATDT7672882^M)
Apr 19 11:22:22 localhost chat[9769]: expect (CONNECT)
Apr 19 11:22:22 localhost chat[9769]: ^M
Apr 19 11:22:22 localhost chat[9769]: ATDT7672882^M^M
Apr 19 11:23:07 localhost chat[9769]: alarm
Apr 19 11:23:07 localhost chat[9769]: Failed
Apr 19 11:23:07 localhost pppd[9768]: Connect script failed
Apr 19 11:23:39 localhost chat[9793]: abort on (BUSY)
Apr 19 11:23:39 localhost chat[9793]: abort on (VOICE)
Apr 19 11:23:39 localhost chat[9793]: abort on (NO CARRIER)
Apr 19 11:23:39 localhost chat[9793]: abort on (NO DIALTONE)
Apr 19 11:23:39 localhost chat[9793]: abort on (NO DIAL TONE)
Apr 19 11:23:39 localhost chat[9793]: send (ATZ^M)
Apr 19 11:23:40 localhost chat[9793]: expect (OK)
Apr 19 11:23:40 localhost chat[9793]: ATZ^M
Apr 19 11:24:10 localhost chat[9793]: Password: ^M
Apr 19 11:24:12 localhost chat[9793]: % Password:  timeout expired!NO 
CARRIER
Apr 19 11:24:12 localhost chat[9793]:  -- failed
Apr 19 11:24:12 localhost chat[9793]: Failed (NO CARRIER)
Apr 19 11:24:12 localhost pppd[9768]: Connect script failed
Apr 19 11:24:44 localhost chat[9812]: abort on (BUSY)
Apr 19 11:24:44 localhost chat[9812]: abort on (VOICE)
Apr 19 11:24:44 localhost chat[9812]: abort on (NO CARRIER)
Apr 19 11:24:44 localhost chat[9812]: abort on (NO DIALTONE)
Apr 19 11:24:44 localhost chat[9812]: abort on (NO DIAL TONE)
Apr 19 11:24:44 localhost chat[9812]: send (ATZ^M)
Apr 19 11:24:44 localhost chat[9812]: expect (OK)
Apr 19 11:24:44 localhost chat[9812]: ATZ^M^M
Apr 19 11:24:44 localhost chat[9812]: OK
Apr 19 11:24:44 localhost chat[9812]:  -- got it
Apr 19 11:24:44 localhost chat[9812]: send (ATDT7672882^M)
Apr 19 11:24:44 localhost chat[9812]: expect (CONNECT)
Apr 19 11:24:44 localhost chat[9812]: ^M
Apr 19 11:24:44 localhost chat[9812]: ATDT7672882^M^M


Ideas ?

---

### Post by VSFH on 2006-04-19
WOOHOOOOO!

added Stupid Mode = yes and Carrier Check = no and I'm online on my ubuntu side!

admin@ubuntu:~/Desktop$

woohoooooo! Thanks to all of the Ubuntu crew and thanks especially to the forum guys for being awesome. I'm one satisfied Ubuntu guy!:D

---

