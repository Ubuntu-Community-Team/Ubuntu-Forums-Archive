---
title: "Installing Civilization: Call to Power (linux version)"
date: 2008-02-07
forum: Gaming &amp; Leisure
---

### Post by Incompetnce on 2008-02-07
I cannot install civilization:call to power. I bought it from tuxgames, but it appears that lokigames no longer has any kind of support available so I don't know how to fix this problem. I can't get the isntaller to work. When I click install I get a popup that says this:
setup/printlibc: 3: function: not found
setup/printarch: 3: function: not found

Does anyone know how to fix this? Or could anyone talk me through just extracting the tarballs directly into a directory via the terminal. (because I can't seem to browse the disc. when I click browse it opens up soundjuicer...)

---

### Post by fs3rp4 on 2008-02-07
> **Incompetnce said:**
> I cannot install civilization:call to power. I bought it from tuxgames, but it appears that lokigames no longer has any kind of support available so I don't know how to fix this problem. I can't get the isntaller to work. When I click install I get a popup that says this:
setup/printlibc: 3: function: not found
setup/printarch: 3: function: not found

Does anyone know how to fix this? Or could anyone talk me through just extracting the tarballs directly into a directory via the terminal. (because I can't seem to browse the disc. when I click browse it opens up soundjuicer...)

You will have a hard time. Lokigames design this game to kernel 2.4 and a lot of things change since there. 

Start from here: [http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu:en-US:official&hs=rCp&sa=X&oi=spell&resnum=0&ct=result&cd=1&q=loki+game+export&spell=1](http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu:en-US:official&hs=rCp&sa=X&oi=spell&resnum=0&ct=result&cd=1&q=loki+game+export&spell=1)

---

### Post by compiledkernel on 2008-02-07
in my experience most of the Loki games installs (I have Kohan, Alpha Cent, and Tribes2) are very difficult to get running on newer equipment/Distros. the updates provided by Loki games (they live out on tuxgames now) , dont install well if at all. Its pretty much a lost cause IMO.

---

### Post by fs3rp4 on 2008-02-07
> **compiledkernel said:**
> in my experience most of the Loki games installs (I have Kohan, Alpha Cent, and Tribes2) are very difficult to get running on newer equipment/Distros. the updates provided by Loki games (they live out on tuxgames now) , dont install well if at all. Its pretty much a lost cause IMO.

I agree. Windows version under wine is more compatible...

---

### Post by Incompetnce on 2008-02-07
Well that sucks. I think it's dishonest to keep selling them if they do not install without a lot of effort. hardly helping the cause if they are selling games for linux which are as hard to fix as using wine...

im going to send an angry email to tuxgames...

thanks for the help dudes!

---

### Post by fs3rp4 on 2008-02-07
> **Incompetnce said:**
> Well that sucks. I think it's dishonest to keep selling them if they do not install without a lot of effort. hardly helping the cause if they are selling games for linux which are as hard to fix as using wine...

im going to send an angry email to tuxgames...

thanks for the help dudes!

I'm sorry, but did they still sell this product these days? I don't believe! This game was from 1999...

Well try their forum: [http://happypenguin.org/forums/](http://happypenguin.org/forums/)

---

### Post by englebert on 2009-01-19
From the README on the CD:

Expert Installation:
1.  From within a directory with 400MB free space, untar CivCTP.tar.gz,
found on the mounted CD.  It will extract into a subdirectory named "CivCTP".

2.  To install the game videos onto your local hard drive, copy the 
contents of the directory [Your Mounted CD]/runtime" to the CivCTP directory.

Then install the update here: [http://lokifiles.tuxgames.com/updates/civctp/civctp-1.2a-english-unified-x86.run](http://lokifiles.tuxgames.com/updates/civctp/civctp-1.2a-english-unified-x86.run)

Then you should be able to play it.

---

### Post by theCoder on 2009-08-07
Just an additional note, it is very likely that the patch will not run either, due to changes to tail in GNU&#347; coreutils.

You will get the following error:
Verifying archive integrity...tail: cannot open `+6' for reading: No such file or directory

Documented in this thread: [http://osdir.com/ml/bug-coreutils-gnu/2009-05/msg00068.html]("http://osdir.com/ml/bug-coreutils-gnu/2009-05/msg00068.html")

Just execute the patch like this:
chmod 755 civctp-1.2a-english-unified-x86.run
and then:
_POSIX2_VERSION=199209 ./civctp-1.2a-english-unified-x86.run

Will install without a hitch.

---

### Post by Crunchy the Headcrab on 2009-08-07
I hope you get it to work.  Call to Power is my favorite Civilization game.  Lots of future tech that rocks including beef vats which guarantee a food supplus in the city but cause massive pollution, and the gaia controller that removes ALL pollution worldwide thus making it a non issue.  Space stations and drop pods are excellent as well.   :popcorn:

---

### Post by fs3rp4 on 2009-08-07
You really are awakening the dead...

---

### Post by Crunchy the Headcrab on 2009-08-07
Wow.  You're right.  The only thing I noticed was that the person that posted before me was only like an hour earlier.  :lolflag:

---

### Post by teddybairs1 on 2012-05-19
Just an update to this thread, I ran this with the patch following very similar steps to the above (unpack, copy, and then run patch) up through Ubuntu 10.10. I haven't tried it with the newer 3.x Linux kernel yet, but I intend to try with 12.04 so we'll see how it goes. Once I applied the patch, it ran flawlessly.

---

### Post by teddybairs1 on 2012-05-19
Ok, it installs fine under 12.04 if you follow the instructions from this thread -http://ubuntuforums.org/showthread.php?t=170287

FYI I'm running an x64.

---

### Post by mateo14 on 2012-05-22
> **teddybairs1 said:**
> Ok, it installs fine under 12.04 if you follow the instructions from this thread -http://ubuntuforums.org/showthread.php?t=170287

FYI I'm running an x64.

This is new installer for linux version of Civilization: Call to Power:

[http://liflg.org/?catid=7&gameid=91](http://liflg.org/?catid=7&gameid=91)

---

