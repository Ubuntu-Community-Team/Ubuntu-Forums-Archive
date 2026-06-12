---
title: "Burning CDs in Brasero (Jaunty) - Error"
date: 2009-04-28
forum: General Help
---

### Post by daggerx on 2009-04-28
Burning CDs in Brasero (Jaunty) and after the CD is done it gives me an error message (error while burning). This happens after every cd I burn and so far i've burned 3. The hash matches the ubuntu hash (was burning the desktop CD). Any Suggestions? Please help and thanks in advance.

---

### Post by freonchill on 2009-04-28
does the disc work?

i had problems in 8.10 on brasero, ended up using imgburn via wine.
figured it was just the POS drive the dell put in the laptop...

---

### Post by daggerx on 2009-04-28
Yeah, I believe it will work. When I put the disc back in the drive, it was ready to go with the package install etc...its just weird seeing that. I just hope there is an update that is coming soon to fix that....if it needs fixing...

---

### Post by timcredible on 2009-04-28
try k3b instead.

---

### Post by freonchill on 2009-04-28
timcredible:

can you use k3b in gnome?

---

### Post by Fr33d0m on 2009-06-07
Well I've tried multiple CD's and multiple ISO's  All error out and are unusable.

---

### Post by ActiveFrost on 2009-06-07
Try *GnomeBaker CD/DVD Writer* ! After having problems with Brasero ( CD's were incompatible with Windows based machines ), this one works pretty well ( easy interface, lots of stuff .. what else do we need ? :D ).

---

### Post by alexlittle on 2009-06-17
I've also had this problem with Jaunty and Brasero. All worked fine on Heron, but now whatever I try to burn fails - have tried all sorts data cd, data dvd, iso, vcd etc, but get same message. The checksum finishes, then after the drive starts spinning for writing a general 'error occured' message appears. I'd be very pleased if this was fixed! Or if someone can point me to how to sort it out.

Alex

---

### Post by VMC on 2009-06-17
> **daggerx said:**
> Burning CDs in Brasero (Jaunty) and after the CD is done it gives me an error message (error while burning). This happens after every cd I burn and so far i've burned 3. The hash matches the ubuntu hash (was burning the desktop CD). Any Suggestions? Please help and thanks in advance.

I've had similar problems. Something to do with the way it checks sums. Brasero has a log file. Can you output that? Also, next time run Brasero through a Terminal and then see what output is on the Terminal.

---

### Post by kraymore on 2009-06-22
running brasero from a terminal and writing an iso gives:

I/O warning : failed to load external entity "/home/bobcat/.config/brasero/brasero.session"

the error while burning, some files may be corrupted by disc log is attached to this post.

---

### Post by StOlEnDeStInY on 2009-06-23
Maybe you shouldreport your bug here:

[https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/373591](https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/373591)

---

