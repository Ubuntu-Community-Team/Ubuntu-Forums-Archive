---
title: "Gaim shutting down"
date: 2006-07-20
forum: Desktop Environments
---

### Post by lonrot on 2006-07-20
I have just installed a fresh version of Ubuntu 6.06 x86 and eveytime I start the program and I log into my account the program closes. I don't even have the chance to write something :-k 

I already tried to reinstall it and no change so far.
Version: 1:1.5.0 + 1:1.5.1cvs20

---

### Post by krismatth3 on 2006-07-20
Can you try starting gaim from a terminal? Applications->Accessories->Terminal, type "gaim" and press enter. Does it print out any error messages?

---

### Post by lonrot on 2006-07-22
Nope, It opens correctly and suddenly shuts down, even the terminal does the same. :-?

---

### Post by norwyn on 2006-08-04
I've got the same problem.
Have you filed a bug in launchpad?

---

### Post by hansheng on 2006-08-04
do you use msn? coz I hv the same problem before. 
when i using Gaim2.0.0beta3, work fine.

---

### Post by dubbreak on 2006-08-04
I'm having the same problem: [http://ubuntuforums.org/showthread.php?t=224824](http://ubuntuforums.org/showthread.php?t=224824)
No responses to my thread though :P.

Anyhow to re-itterate, when launch in a console this is what I get:
```
dubbreak@lapbuntu:~$ gaim
Creating link /home/dubbreak/.kde/socket-lapbuntu.
can't create mcop directory
```

---

### Post by guga1981 on 2006-08-05
I have the same pb!

The error message is:

```
guga@ubuntu:~$ gaim
Gaim has segfaulted and attempted to dump a core file.
This is a bug in the software and has happened through
no fault of your own.

It is possible that this bug is already fixed in CVS.
If you can reproduce the crash, please notify the gaim
maintainers by reporting a bug at
http://gaim.sourceforge.net/bug.php

Please make sure to specify what you were doing at the time,
and post the backtrace from the core file. If you do not know
how to get the backtrace, please get instructions at
http://gaim.sourceforge.net/gdb.php. If you need further
assistance, please IM either SeanEgn or LSchiere and
they can help you.
Abandon
```

Strange... but i remember having the same pb a couple of months ago. I can't remeber how I fixed it!


Guillaume

---

### Post by aceracer24 on 2006-08-05
```
david@AceRacer:~$ gaim

(gaim:8153): Pango-WARNING **: Error loading GPOS table 4097

```

problems too :( Gaim is running and i see the window start to draw but then it stops, but gaim is still running.....

---

### Post by dubbreak on 2006-08-05
For me it won't crash until I open a window to message a contact, as son as I type send it goes splat.

---

### Post by Nemesis Teufel on 2006-08-06
I have the same problem, when I log, wait a few seconds and inmediatly shut down.(I dont touch anything)

---

### Post by Nemesis Teufel on 2006-08-06
I know the problem!!!!!1one:-D 

omehow the gaim preferences got corrupted

go to Home and unhide(Ctrl+H) the folders.

then rename .gaim as .gaimbackup or delete

relaunch gaim and chat with your friends 8)

---

### Post by ragnar_123 on 2006-08-07
nope, i tried, but i did not work, same thing happened again..:/

---

### Post by dubbreak on 2006-08-11
It worked for all of one day for me (forcing gaim to make a new prefs folder). Anyone have any other ideas? My solution for now is to use kopete, but I'd prefer to use gaim (it has all my OTR settings etc).

---

### Post by antw on 2006-08-12
What worked for me was to delete any computers you have in your contact list. There was one there to help with homework etc. I had to go onto a windows machine to allow me to get on long enough to delete it.

Went straight back to my linux machine and it worked.

Good luck

---

### Post by lonrot on 2006-08-13
> **antw said:**
> What worked for me was to delete any computers you have in your contact list. There was one there to help with homework etc. I had to go onto a windows machine to allow me to get on long enough to delete it.

Went straight back to my linux machine and it worked.

Good luck

Excellent, it worked perfectly for me, I would never realiazed that was the problem. Thanks a lot. I had the computer bot Encarta, and I just deleted it and voilla GAIM working like a charm. =D> 

For the better I hope upcoming GAIM versions will come with this bug solved.

---

### Post by iLLucionist on 2006-08-13
I had exactly the same. It occurred when I blocked someone, I had to delete a file called something like ~/.gaim/blocklist.xml or something like that. After that everything went perfectly fine. :)

Could that be the issue?

---

### Post by dubbreak on 2006-08-16
Hmm I have no one blocked, but deleting blocklist has allowed it to work (for now :P ). Thnx.

---

### Post by repins on 2006-08-16
i am also having the same problem with my msn account on gaim, but if i use my wifes account, its fine...the different thing about our accounts besides the obvious (account names) is that mine has more contacts in it.

---

### Post by dubbreak on 2006-08-17
ARGGG!!!! So deleting the blocklist worked for all of one day. I might just do a complete reinstall of gaim (making sure I delete all my settings as well). I'll have to re-add a bunch of OTR fingerprints, but this is driving me nuts (especially the fact that there aren't any decent error messages generated).

Speaking of which I'll run it with -d (debug). Haha, no crash when I run it that way (if I run it without it crashes pretty quickly).Maybe it's race condition (only thing I can think of that printing debug messages would make a diff)?

---

### Post by Leonivek on 2006-08-17
I had the same problem.  I have a quick fix: use Kopete!  :wink:   I never liked Gaim... but that's my opinion.  :lol:

---

### Post by dubbreak on 2006-08-18
I have been using kopete (mentioned earlier in thread) but that is a poor solution.

---

### Post by kno712 on 2006-08-18
I edited the blakclist xml file in the .gaim directory, deleted the encarta boot, and it worked out for me.... for the moment being...

Do not forget to delete the same entry in hotmail (go to [www.hotmail.com](www.hotmail.com) and edit your contact list) or gaim will try to update itself with this boot the next time you try to launch it.

---

### Post by Junosix on 2006-08-18
I found that manually creating the directory it grumbles about does the trick.  For instance on mine it was trying to create "/home/junosix/.kde/socket-junosix", so I created that directory and it worked.

---

### Post by tomdkat on 2006-08-18
The [Gaim homepage](http://gaim.sourceforge.net/) has a news item about Gaim crashes, mainly on Windows, when connecting to a MSN account.  I don't know if this is exclusively a Windows issue or not.  

fyi...

Peace...

---

### Post by dubbreak on 2006-08-18
> **Junosix said:**
> I found that manually creating the directory it grumbles about does the trick.  For instance on mine it was trying to create "/home/junosix/.kde/socket-junosix", so I created that directory and it worked.

Good call. That seems like the most likely solution judging by the error I had. Hmm but it isn't crashing right now... go figure.

---

