---
title: "what to do about a bug in &quot;Empire&quot; game"
date: 2009-04-25
forum: Gaming &amp; Leisure
---

### Post by nikclev on 2009-04-25
I've got a problem with a game in Ubuntu, Empire. ("Empire 1.7-3" in the Games and Amusement (universe) repo)

The game is playable, but randomly seg faults. I've played and won games, (and lost:)) that have been trouble free, but most times it'll seg fault. The thing is, if I re-start the game from the save, I can usually play on. (in other words, it seems to be completely random)

The game is OLD, and as it's an unsupported package I don't really want to just fire off a bug report, for a couple of reasons: 

1.) I'm not exactly sure how to file a bug report (in the right manner and place)
2.) Even if I did, it's an unsupported package, so at most the bug report would get referred to an upstream somewhere.
3.) I'm not sure I could even provide much in the way of usefull information, and "It's borken! fix this plox" bug reports are less than useless!

What I'm wondering is this, in general and specifically about the Empire game:

1.) Where do I find info in a package about who maintains it, if it's even maintained?
2.) Where can I find the source code for said package, in case I wanted to break it even further... er, I mean, try to fix it myself?

Thanks guys! I hope I'm posting this in the right place, and if not I apologize!

---

### Post by Vadi on 2009-04-25
It looks like the game itself was on 1.7.3 since Hardy, so chances of it being fixed by the original developers don't look great (although I couldn't find their homepage so I don't know if they are active). 

At any rate, the recommended way to file a bug about something is via the "ubuntu-bug" tool in the terminal. You use it as "ubuntu-bug *package*". This will collect relevant system information, and start the creation of a new bug report aimed at a particular package via a browser.

To see information about a package, visit packages.ubutu.com: [http://packages.ubuntu.com/jaunty/empire](http://packages.ubuntu.com/jaunty/empire)

and the source code is here: [http://de.archive.ubuntu.com/ubuntu/pool/universe/e/empire/empire_1.7.orig.tar.gz](http://de.archive.ubuntu.com/ubuntu/pool/universe/e/empire/empire_1.7.orig.tar.gz)

Let me know if you'll need anything else.

---

