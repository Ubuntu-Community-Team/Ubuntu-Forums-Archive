---
title: "random system freeze - relevant logs?"
date: 2009-01-02
forum: General Help
---

### Post by Ace_NoOne on 2009-01-02
Recently, my system (Intrepid on an HP Compaq 2510p laptop) started to occasionally freeze up entirely, not responding to any keyboard commands (including CTRL+ALT+Backspace or CTRL+ALT+F1), mouse movements etc. - so it's not just X locking up, I think.

This happens mostly when leaving the machine to idle for a while, but it's also happened all of a sudden while in regular use.
FWIW, this happened very frequently when I was at a friend's house, so using his wifi and running on battery. Also, the Caps Lock indicator lights up just before the system freezes.

Generally speaking, where would I start looking for logs that might reveal some details on what might be causing this?

Thanks!

---

### Post by Ace_NoOne on 2009-01-08
This happened again today (at the office this time) - three times in a row*!
I'm getting a bit worried now...

* system freeze, hard reset, froze again after ~5 min., let it cool off for ~5 min., reboot, froze again after ~5 min. - now, after taking it home, it seems to be working fine (uptime is 35 min.)

---

### Post by Ace_NoOne on 2009-01-08
[accidental double-post]

---

### Post by Wayne_V on 2009-01-08
Likely a hardware problem.  You could install lm_sensors and see if it supports monitoring fans & temp on your laptop.   I would install smartmontools and set smartd to monitor your hard drive.  You could also keep a window open tailing your log files to see if anything is shown right  before the freeze:


xterm -geometry 160x20 -e "sudo tail -f /var/log/{dmesg,messages,syslog,*.log}" &

---

### Post by Wayne_V on 2009-01-08
Likely a hardware problem.  You could install lm_sensors and see if it supports monitoring fans & temp on your laptop.   I would install smartmontools and set smartd to monitor your hard drive.  You could also keep a window open tailing your log files to see if anything is shown right  before the freeze:


xterm -geometry 160x20 -e "sudo tail -f /var/log/{dmesg,messages,syslog,*.log}" &

---

### Post by Ace_NoOne on 2009-01-14
Thanks for your response, Wayne_V, and sorry for my late reply - this issue has put me out of commission for a while.

It turns out that it's "only" the wireless connection causing these crashes. Surprisingly, that only happens on certain wifi networks - I haven't been able to determine what might be the cause (e.g. WEP vs. WPA), and am pretty much clueless right now.

My machine's an [HP Compaq 2510p]("http://h10010.www1.hp.com/wwpc/us/en/sm/WF06a/321957-321957-64295-321838-306995-3355633.html") using Intel's GM965 chipset.

I should probably open a new thread on this!? (It's a bit hard to google for these specific symtoms... )

---

### Post by wryun on 2010-05-17
I've just hit the same issue: random freezes with caps lock on after connecting to a 'new' wifi network with a 2510p. Did you narrow down this problem? Anyone have any ideas?

---

### Post by Ace_NoOne on 2010-05-17
> **wryun said:**
> Did you narrow down this problem?
I'm afraid not. IIRC, it just stopped freezing at some point - not sure whether that was related to a distro upgrade or anything like that.

---

### Post by wryun on 2010-05-17
Thanks for that - if it's sorted with newer Ubuntu, probably means I should update my debian lenny kernel to fix the issue.

---

