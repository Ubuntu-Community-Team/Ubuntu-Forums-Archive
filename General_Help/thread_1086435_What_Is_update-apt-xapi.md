---
title: "What Is update-apt-xapi?"
date: 2009-03-04
forum: General Help
---

### Post by klausner on 2009-03-04
What Is update-apt-xapi, why/how does it start itself? Seems to kick off and consume 100% of the CPU. There is no manual page for it. I assume it is something to do with the apt database.

---

### Post by mb_webguy on 2009-03-04
You're probably seeing a truncated "update-apt-xapian-index".  It rebuilds the index of packages used to list packages and applications in Add/Remove Applications and Synaptic.

I don't know exactly why it would be running in the background unless you're running a package manager.  Since Update Manager runs in the background, I suppose it could be calling update-apt-xapian-index...

---

### Post by unc0nn3ct3d on 2010-04-23
just noticed the exact same thing here.. Not running synaptic at all, just playing some frets on fire, firefox is open, amsn, thunderbird, and tweetdeck.  Suddenly system just started to lag like a mofo and I noticed that update-apt-xapi was just destroying one of my cores..

By the time I found it had calmed down but it is a bit unnerving to have a process just start on its own like that and decide to prioritize itself.  Pretty sure that's the reason I burnt all of my microsoft those many years ago

---

### Post by Eiríkr on 2010-05-15
I've got to ask, **who thought this was a good idea???**  Sheesh.  I'm with you, unc0nn3ct3d, this kind of hamfisted tomfoolery is exactly why I hate Microsoft, and it irks me to no end to find that here in Linux Land.  If this process is supposed to be some background maintenance routine, then it should be very nice indeed and get out of the way of anything the user is trying to do, like watch a video or listen to music or play a game or...  I've had [font=courier]update-apt-xapi[/font] very obtrusively screw up all of these, pegging one of my cores at 100% and causing anything else I'm trying to do to run dog slow.

[thread=1062688]This thread[/thread] offers one possible way to kill this beast without breaking anything (simply [font=courier]chmod[/font]ding the executable to be non-executable).  I'll poke around some more on the Forum and see if anyone has any other advice.

Cheers,

-- Eiríkr

----------
UPDATE:

Found useful info over on Launchpad.  Wrote up a post and explanation of the fix [post=9304431]here[/post].  Hope it helps!

---

### Post by Sepero on 2010-05-31
[http://ohioloco.ubuntuforums.org/showthread.php?p=6935368](http://ohioloco.ubuntuforums.org/showthread.php?p=6935368)

---

