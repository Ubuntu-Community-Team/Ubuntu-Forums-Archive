---
title: "System Beeps on Startup and Shutdown"
date: 2005-09-18
forum: Desktop Environments
---

### Post by vibestriton on 2005-09-18
I am getting system beeps on startup and shutdown with my Dell Latitude D600 Laptop and that's a very bad thing, considering I have to use this laptop in a quiet classroom setting. Is there a way to disable the beeps?

All my hardware seems to be working fine.  The startup beep occurs a half second before the login screen appears and the beep on shutdown happens when the PCMCIA message is displayed.  This has happened with both 5.04 and 5.10.  (I'm a linux newbie.)

---

### Post by triviab0y on 2005-10-17
Its probably the PCMCIA (PC Card) drivers loading. They tend to beep in most OSs. Haven't tested it myself but you could try editing /etc/rc.d/rc.pcmcia

and adding

CARDMGR_OPTS="-q"

As I say this is *untested*, so make sure you backup!

---

### Post by loon on 2005-10-17
this happened to me at one point....

for a quick fix, I was able to turn of PC volume through 'alsamixer' (at command prompt)


hope this is a quick fix for you.

---

### Post by vibestriton on 2005-10-19
Thanks for the replies... I will be sure to try those suggestions the next time I install Ubuntu.  However, I just uninstalled PCMCIA because I didn't really require it and that worked fine.

Thanks.

---

### Post by adamonduty on 2006-01-03
I also had the same problem. My Dell Inspiron 600m almost always beeps on startup and shutdown at least with all debian-based distributions I've tried. I was able to get it to stop by adding the CARDMGR_OPTS="-q" line to the /etc/default/pcmcia file. 

No more funny looks when my laptop beeps in class! :D

---

### Post by vibestriton on 2006-01-04
hehe.  Thanks folks.  Yeah, the -q thing worked too.  :)

---

