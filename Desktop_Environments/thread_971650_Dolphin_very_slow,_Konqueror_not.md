---
title: "Dolphin very slow, Konqueror not"
date: 2008-11-05
forum: Desktop Environments
---

### Post by jacksaff on 2008-11-05
As the title says, on Intrepid I am finding dolphin very slow but Konqueror (which uses the same code for file browsing) to be very fast. The program often takes a couple of seconds to load a directory where konqi does it instantly. Seems the dolphin is doing some loops somewhere.

Anyone got any idea just how I can find out what is slowing down dolphin so I can look into finding/filing a bug? I get nothing running dolphin from a terminal and, as it doesn't crash (just runs slow) I get no crash reports either.

---

### Post by jacksaff on 2008-11-07
Seems all problems were due to having nepomuk running. For some reason it slows dolphin down to the point it is unusable.

---

### Post by Marsolin on 2008-11-07
I had the exact same issue and had to disable Nepomuk.  The problem didn't exist for me in hardy. I really like the idea of Nepomuk, but until we get some better front end tools for searching it seems rather useless.

---

### Post by bldyman on 2008-11-09
yeah I have the same problem..but  liked nepomuk!

---

### Post by Sathors on 2010-10-23
Same problem here, disabling Nepomuk solved everything, my desktop is now as snappy as it used to.

---

### Post by BryanFRitt on 2011-07-06
Same situation in K/Ubuntu 11.04 64 bit, Dolphin is incredibly slow... 
I noticed that every time I start Dolphin the network activity goes up.
Why would Dolphin be trying to access the internet? 
Could it be the remote afs(Andew File System)?
Could this be what's slowing it down?
Dolphin's slow when not going through afs too.
Could it be some plugin or something? or even a virus?
No previews, and no preview pain to slow it down.
Nepomuk isn't running.
This slowdown/internet access doesn't happen with Konqueror.
Dolphin seams to speed up if left open for a while.

---

### Post by Sathors on 2011-07-07
Are you sure that you disabled Akonadi as well as nepomuk ?

I remember that it wasn't that plain to do, because there was different elements which needed to be deactivated.

Apart from that it may be remote files, but I don't know how you could test without it ...

---

