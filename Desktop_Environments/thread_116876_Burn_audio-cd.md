---
title: "Burn audio-cd?"
date: 2006-01-13
forum: Desktop Environments
---

### Post by Edho on 2006-01-13
I am new to Ubuntu... and music-manipulation.

With Sound-Juicer i can choose tracks from a audio-cd and extrackt them to my harddisk.
Then they are play-able with Rhytmbox..nice.

But if i burn them to a blanc-cd (RW) with Serpentine ,they are not play-able with a cd-audioplayer or even not with Rhytmbox.

What i do wrong?
What is the best program, in Ubuntu to solve this problem?

Advice please.

Thank You.

---

### Post by Zelut on 2006-01-13
I've actually never tried Serpentine so I'm not sure if I could offer advice on that.  I've always used gnomebaker (should also be in your Sound & Video).  It is fairly simple.  Drag & Drop files you want into the bottom section, make sure it is on the 'audio CD' tab (vs data cd) and give it a try.  I haven't had any issues with it so far...

[if gnomebaker isn't installed you can install it using: **sudo apt-get install gnomebaker** or find it under **Add Applications** in the Sound & Video section

---

### Post by PuNGS on 2006-01-13
I use gnomebaker too, and it works perfectly. Give it a try.

---

### Post by kingsidy on 2006-01-13
i have used serpentine to burn regular cds. and it does work. maybe you are missing codecs or something like that.

---

### Post by Edho on 2006-01-13
Step forward!

Installed Gnomebaker.
Burnd songs on the RW disk.
They are now play-able on my computer.

But not on a regular (radio)cd-player...tested on 2 different devices.

Can't figure out why Serpentine not worked.


Thanks for the tip.

But i like to play my compilations on a ordinary player, outside of my computer.

Do some-one see the problem?


But thanks again.

---

### Post by Zelut on 2006-01-13
I suppose it could be an issue of codecs.  I might suggest trying installing the gstreamer codecs if you haven't already.  You can find steps below (note: a few will mention not found, this is ok as the guide is getting older)

[Install Codecs]("http://www.ubuntuguide.org/#codecs")

---

### Post by Fixxxer on 2006-01-14
[QUOTE=Edho]Step forward!

Installed Gnomebaker.
Burnd songs on the RW disk.
They are now play-able on my computer.

But not on a regular (radio)cd-player...tested on 2 different devices.

Can't figure out why Serpentine not worked.


Thanks for the tip.

But i like to play my compilations on a ordinary player, outside of my computer.

Do some-one see the problem?


But thanks again.[/QUOTE]

The problem is that you used a RW disk. Not all cd players are able to read RW disks. Try burning an audio disk using a cd-r with Gnomebaker and tell me if it works.

---

### Post by Edho on 2006-01-15
Will try write once cd's.

Next week to the shop.:p

---

