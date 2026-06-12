---
title: "Issue: can't mount CD-R discs"
date: 2008-12-13
forum: General Help
---

### Post by spaceScout on 2008-12-13
Running Ibex, uname -a gives Linux alvin 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686 GNU/Linux.

When I put in a burned CD-ROM, whether it be a duplicate of a "real" CD-ROM or created for holding data files, it will not mount.  However if I put in a movie DVD, a burned DVD (e.g., Fedora 10 from iso image), or a commercially-created CD-ROM (I imagine "pressed", not burned), it mounts okay.

Indications of badness:

Pop-up window, title "Unable to mount <name-of-CD-ROM-volume>".  Text: "DBus error ord.freedesktop.DBus.Error.NoReply: Did not receive a reply.  Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken."  This window shows up twice.

/var/log/messages (for machine "alvin"):
Dec 13 11:47:49 alvin kernel: [  737.776007] sr 5:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Dec 13 11:47:49 alvin kernel: [  737.776017] sr 5:0:0:0: [sr0] Sense Key : Medium Error [current] 
Dec 13 11:47:49 alvin kernel: [  737.776022] sr 5:0:0:0: [sr0] Add. Sense: CIRC unrecovered error
D

Displays this a total of 10 times, 7 second between each of the above three lines.

This has started only within the last couple weeks or so, seeing as I don't use CD-ROMs very often.

Any hints on what's bad?

---

### Post by |{urse on 2008-12-13
[https://bugs.launchpad.net/ubuntu/+bug/295795]("https://bugs.launchpad.net/ubuntu/+bug/295795")

I've seen this bug a bit, let me make a wild guess.. you burned the offending Cd-r with Brasero? Try this

get one of your blank cds

sudo apt-get install k3b

k3b

now use k3b to burn something and see if it will mount after the process is finished.

---

### Post by spaceScout on 2008-12-13
> **|{urse said:**
> [https://bugs.launchpad.net/ubuntu/+bug/295795]("https://bugs.launchpad.net/ubuntu/+bug/295795")

I've seen this bug a bit, let me make a wild guess.. you burned the offending Cd-r with Brasero? ...

Actually no.  These are a few CDs that were burned by other people who I'm 98% sure run Windows boxes.  If it matters, they're ISO 9660 Rockridge format.

I was able to read all these CD-ROMs on the same hardware when I booted into Windows XP SP2, and on a Macintosh.  I've also figured out that any CDs burned by a Macintosh are also readable by Ibex.

---

