---
title: "pyscrabble error could not connect to server"
date: 2010-11-05
forum: Gaming &amp; Leisure
---

### Post by Fardin on 2010-11-05
I installed pyscrabble. but when I tried to open the game it said I had to register to a public server and gave me 2 option :
bacasoft.com
pyscrabble.califorest.com
i tried both, but got error could not connect to server
for a person who is not familiar with codes and terminal, could someone explain simply how this could be resolved.
Thanks

---

### Post by Objekt on 2010-11-06
I had the same problem.  I don't think there's anything you (or I) can do about it.  I found a discussion thread on Sourceforge, where the administrator of one of the public Pyscrabble servers (califorest.com) explains why it's down:

[http://sourceforge.net/projects/pyscrabble/forums/forum/471414/topic/3187871]("http://sourceforge.net/projects/pyscrabble/forums/forum/471414/topic/3187871")

Executive summary: Running a Pyscrabble server is something he does in his spare time, so it will take "as long as it takes," maybe early December if we're lucky.

I'm afraid you and I are stuck running our own server if we want to play.  I'm looking into it & who knows, I might end up doing it.  Not sure how well it will work, given my Internet connection (6 Mbit down/2 Mbit up), but I do have an old machine I could possibly dedicate to running the server.

---

### Post by Fardin on 2010-11-06
> **Objekt said:**
> I had the same problem.  I don't think there's anything you (or I) can do about it.  I found a discussion thread on Sourceforge, where the administrator of one of the public Pyscrabble servers (califorest.com) explains why it's down:

[http://sourceforge.net/projects/pyscrabble/forums/forum/471414/topic/3187871](http://sourceforge.net/projects/pyscrabble/forums/forum/471414/topic/3187871)

Executive summary: Running a Pyscrabble server is something he does in his spare time, so it will take "as long as it takes," maybe early December if we're lucky.

I'm afraid you and I are stuck running our own server if we want to play.  I'm looking into it & who knows, I might end up doing it.  Not sure how well it will work, given my Internet connection (6 Mbit down/2 Mbit up), but I do have an old machine I could possibly dedicate to running the server.


Thanks
my ubuntu froze and I may have to reinstall the whole thing, this time I won't bother installing pyscrabble. they should remove it from the list if not available or have a note nearby somewhere!

---

### Post by edbucks on 2010-11-08
Any luck setting up a server? If not I may be able to offer one.

---

### Post by btdrake on 2011-02-14
I'm in the last stages of rebuilding pyscrabble.califorest.com (yes, it does run on my home servers), and I hope to have it up and running tonight.   Instead of using a physical machine, I'm putting it on my VMWare ESXi infrastructure, with backup servers, so it should be much more available and reliable from now on.

Kevin (the author of the program) doesn't have the time to maintain it any more.  I'm a big Scrabble fan myself, so I set up and offered the first version of the Califorest server, and Kevin added it to the list of public servers.  I didn't even realize until I started getting mail about it that Canonical had added it to their distributions; that's kind of cool!

Anyway, I have been super busy, which is why it has taken so long to get this working again.  It's not an excuse, just an explanation.  I apologize for the frustration I'm sure this has caused people.
-- 
Barry

---

### Post by crooks306 on 2011-10-11
You can manually enter this address into the hostname.
```
club-scrabble.info:9999
```

---

