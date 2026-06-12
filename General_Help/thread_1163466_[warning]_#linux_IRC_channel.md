---
title: "[warning] #linux IRC channel"
date: 2009-05-18
forum: General Help
---

### Post by lenswipe on 2009-05-18
just a warning people that i was in #linux on irc.freenode.net and i was instructed by tsukasa_ to run a command that chmodded / to 777 recursive, im not going to post the actual command here incase somenoe decides to actually run it, but those of you experienced with file permissions will know exactly the command i mean.

So its just a side note that if this guy tells you to do something you should check it out first...

-Lenswipe

---

### Post by albinootje on 2009-05-18
> **lenswipe said:**
> chmodded / to 777 recursive


Sometimes people recommend things without really knowing what they are talking about.

Imho every "chmod 777" should be frowned upon.

Sometimes it is used by software installations like CMS-es or blog software, but usually temporarily, only during the installation.

/var/tmp and /tmp have 1777 as permissions by default on a Linux system, and I don't think there's anything else which should have a 777 in the permissions set.. (or did I miss something ?)

---

### Post by lenswipe on 2009-05-21
no that sounds pretty much it..

People who know very little on the topic shouldn't give out advice on said topic...

What i know about LDAP could be written on the back of a postage stamp, which means that i don't go into the LDAP channel and tell the people in there to run stupid commands that hose your system >=[

Anyway rant over...

There are some parts of a phpbb install i belive that need 777 permissions all the time (yes cache folder im looking at you).

Regards
-lenswipe

---

