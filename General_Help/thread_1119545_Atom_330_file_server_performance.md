---
title: "Atom 330 file server performance"
date: 2009-04-08
forum: General Help
---

### Post by mdurkin on 2009-04-08
Hi All,
I recently picked up the new(ish) intel atom 330 based board to use as a file server. It is connected to my gigabit switch, jumbo frames not supported unfortunately. I have 2G ram. OS installed on a CF card, with storage on 4x1TB samsung drives in a software raid 5 array.
I've installed ubuntu normal edition as I'll occasionally use GNOME (happens to be jaunty beta but I don't really think that should matter in this case).
I've now discovered that samba doesn't multi thread. When transferring files I max out at about 35-40MB/s either read or write, with samba using just one core (2 hyperthreading cores appear as 4 cores to the OS). I'd like to know if there are ways of improving file transfer speeds, either using samba or something else. My main clients are windoze PCs.
I also tried iscsitarget, as I believe it is able to multi-thread, but it has very similar performance to samba (which I found surprising).
Suggestions on how to speed things up much appreciated.
I might install something like freenas just to see what performance an alternate solution can get from the same hardware, but I really want to use ubuntu longer term as I have other packages I need to run on there (squid, apache...)

Thanks,
Matt

---

