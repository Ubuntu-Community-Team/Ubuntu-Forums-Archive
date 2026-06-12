---
title: "Azureus problem"
date: 2005-10-14
forum: Desktop Environments
---

### Post by krusk on 2005-10-14
I used "hoary-backports" repositories from [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories) in my new 5.10 install to get azureus. It installs fine.

Problem number one is that azureus seems to use an other java-client then suns, which i is installed, and that one seems to run poorly. It gives me a 99% cpuload everytime I do something with the program. I would preferly choose azureus to run with Suns java client, so is it a way to change this?

The bigger problem is that the torrents i manage to open in azureus, never starts to download. It finds seeds and peers and the tracker status is "OK (dht:)", but no downloading starts. (All the necessery ports are open)

I really dont like the other bittorrent clients on linux, so it would be nice if anyone could help me out :rolleyes: thanks!

---

### Post by SmokingGun on 2005-10-14
I just this minute posted the exact same thing!  I guess it's not just me then...

EDIT:  OK, i got it working.  I wasn't using Suns Java 1.5 by default.  Enter "sudo update-alternatives --config java"  in a terminal and select Sun's Java.  Restart Azureus and all should be fine.

---

### Post by Nevershine on 2005-10-14
Thanks!!! I had the same problem and I have just fixed with your solution.

---

### Post by gnumerouno on 2005-11-06
Thanks a million SmokingGun :KS

---

### Post by strawman on 2005-11-08
thanks for that knowledge!:D now azureus loads a lot quicker and i can actually use it - thanks again.

---

### Post by UCW181 on 2005-11-10
Hey! Azureus is working fine again! thanks SmokingGun!

---

