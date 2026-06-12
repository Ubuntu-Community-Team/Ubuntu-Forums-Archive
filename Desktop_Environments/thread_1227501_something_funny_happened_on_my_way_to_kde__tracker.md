---
title: "something funny happened on my way to kde:  tracker stopped working"
date: 2009-07-30
forum: Desktop Environments
---

### Post by w.g.hanna on 2009-07-30
tracker or beagle or whatever its called is a killer app for me - i like the way it searches for words inside a document.  for the longest time, i just ran ordinary ubuntu - then i found a tutorial for kde4 in a magazine and switched.  wow - i never thought i'd say it, but i really do think their rethinking of the desk top experience is worth the learning curve.  i've had a couple pit falls though.  one that sucks:  the search feature doesn't find anything i'm looking for.  it finds some things - but it doesn't seem to be able to look inside the documents.  this is even true when i type "tracker" in the "run command" thing and select tracker.  i can't seem to get indexing started.  it just doesn't seem to work.  

any ideas?

---

### Post by Zorael on 2009-07-30
GNOME probably starts a daemon (trackerd?) that your tracker client (Beagle?) can't connect to now that KDE isn't starting it. If you still have GNOME installed, try booting it up and examine the running processes for anything that looks like a tracker background process. Note its name (and perhaps the command with which it was run, arguments and all), and start it up in your KDE session.

I don't have access to a GNOME installation at the moment so I can't dig up the names.

---

