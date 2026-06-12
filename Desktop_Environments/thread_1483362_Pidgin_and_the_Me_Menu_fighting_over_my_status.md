---
title: "Pidgin and the Me Menu fighting over my status"
date: 2010-05-14
forum: Desktop Environments
---

### Post by kendricbeachey on 2010-05-14
I have to use pidgin at work to be able to interface with our MS Office chat system.  (At least the pidgin plugin is the only method I've found to do this.)

This worked OK until the upgrade to Lucid, at which point the Me Menu and pidgin started somehow fighting over my status.  Every couple of minutes I find I'm set to "Do Not Disturb", no matter how many times I change it to "Available", and no matter whether I do it via pidgin or the Me Menu.

Has anyone else seen this behavior or found a way around it?  Thanks...

---

### Post by AlanPorter on 2011-03-29
It's happening to me, too.

Like you, I am using pidgin-sipe so I could connect to my office's MS Office Communicator.

I was not sure if this was a pidgin thing or a pidgin-sipe thing or perhaps some setting on our MS Communicator server.

I can't find a pattern in the status changes... I was fine all morning, and now it's changed back to "do not disturb" twice while I composed this message.

Alan


```

alan@chutney:~$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"
alan@chutney:~$ dpkg -l | grep pidgin
ii  pidgin            1:2.7.3-1ubuntu3.2
ii  pidgin-data       1:2.7.3-1ubuntu3.2
ii  pidgin-libnotify  0.14-4ubuntu1
ii  pidgin-sipe       1.9.0-1ubuntu1
alan@chutney:~$

```

---

### Post by AlanPorter on 2011-03-29
Oooh, I wonder if the helpful hand of Microsoft is setting it to DND because I have a meeting on my calendar.  That would be very clever, in an annoying Microsoft kind of way.

Normally, if I am actually *in* a meeting, I would never notice the DND.  But I just happened to come back early from a short meeting just now, and I see I am repeatedly put into DND.  My scheduled meetings for the day end in a little while... I will monitor it and see if that's what's causing the switch.

Share and enjoy! (Go stick your head in a pig) [1]

Alan



[1] [http://en.wikipedia.org/wiki/Technology_in_The_Hitchhiker%27s_Guide_to_the_Galaxy#Sirius_Cybernetics_Corporation](http://en.wikipedia.org/wiki/Technology_in_The_Hitchhiker%27s_Guide_to_the_Galaxy#Sirius_Cybernetics_Corporation)

---

### Post by AlanPorter on 2011-03-29
Guess what happened right after my Outlook meetings and appointments were over?  Yup, my status changed itself back from DND to "available".

I think we found the culprit -- it's Outlook's calendar.

Alan

---

