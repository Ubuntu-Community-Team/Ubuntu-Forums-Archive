---
title: "accessing DAAP shares"
date: 2005-02-10
forum: Desktop Environments
---

### Post by nachobel on 2005-02-10
alright.  So there's lots of articles and what not on serving music shares via DAAP on a linux box, so that you can access them using iTunes on various other computers, but there's hardly anything at all about using a linux box to access various DAAP shares (say, on a campus network).  I've found something called libopendaap, but i don't really know what to do with it, and I was wondering if anyone else has had positive experiences.

---

### Post by Professor Frink on 2005-02-20
I use ourtunes, a java program.  Just download ourtunes right click it hit "open with" and type in java -jar in the box.  This should open it using java (assuming you have it installed) and you should be able to stream/download MP3's from your friends iTunes, and download the MP4's and play them using totem assuming they are unencrypted.
Hope this helps!

---

### Post by daniels on 2005-02-20
Look for 'tunesbrowser' on the same site (crazney.net).

---

### Post by nachobel on 2005-02-20
[QUOTE=Professor Frink]I use ourtunes, a java program.  Just download ourtunes right click it hit "open with" and type in java -jar in the box.  This should open it using java (assuming you have it installed) and you should be able to stream/download MP3's from your friends iTunes, and download the MP4's and play them using totem assuming they are unencrypted.
Hope this helps![/QUOTE]

hey.  how do i install the "java" command?  I installed java-common from apt, but that didn't work.

---

### Post by Professor Frink on 2005-02-21
[QUOTE=nachobel]hey.  how do i install the "java" command?  I installed java-common from apt, but that didn't work.[/QUOTE]

refer to [www.ubuntuguide.org](www.ubuntuguide.org).  They have a nice howto on installing java.

---

### Post by humina on 2005-10-05
[QUOTE=daniels]Look for 'tunesbrowser' on the same site (crazney.net).[/QUOTE]
Is there a package for this so that I don't have to build it from source?

---

### Post by edrex on 2005-10-07
This client (GTK-based) works well for listening to songs on remote daap shares (although it segfaults occasionally. It doesn't provide a mechanism to save files to disk, however. 

As this libopendaap, for which this is a frontend, supports itunes > 4.5, it would probably be a good base from which to build a download client.

---

### Post by chele on 2006-01-03
[http://gridpt1.fe.up.pt/mlopes/blog/index.php/2005/12/24/rhythmbox-092-deb-for-ubuntu-breezy/]("http://gridpt1.fe.up.pt/mlopes/blog/index.php/2005/12/24/rhythmbox-092-deb-for-ubuntu-breezy/")

Rhythmbox 0.9.2 has built-in daap support. See the blog above for a link to a package that Mario Lopes has been kind enough to provide. It is working nicely for me, streaming music shared from my mt-daapd box.

---

