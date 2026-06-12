---
title: "What is the best program for iPods on Ubuntu 8.10?"
date: 2009-03-13
forum: General Help
---

### Post by Jammanuser on 2009-03-13
Same question as above. :) What is the best program for using iPods in Ubuntu 8.10?

Thanks in advance.

-Jam man

:guitar:

---

### Post by Xero Xenith on 2009-03-13
You have many options, but I'd personally recommend Banshee or Rhythmbox. They both work fine with mine, but the former has basic support for video while the latter has none.

---

### Post by Jammanuser on 2009-03-13
Thanks :) I would like to hear others' opinions as well, and personal preference

---

### Post by mb_webguy on 2009-03-13
Purely for managing files on your iPod, you can't really do any better than gtkpod.

Just yesterday, one of my mother's coworkers bought an iPod Nano and asked me to load it with music from her CD collection.  I used Sound Juicer to rip the CDs, Album Cover Art Downloader to add the album covers to the mp3s, and gtkpod to load the mp3s onto the iPod.  You can install all of these from the repos with the command "sudo apt-get install gtkpod albumart sound-juicer".

gtkpod also supports the transfer of photos and videos, unlike some of the other applications.  I've ripped a couple of my sister-in-law's DVDs to mp4s using Handbrake to put them on her iPod using gtkpod.

Amarok, Rhythmbox, and Banshee should all play music on an iPod without any problem.

---

### Post by Jammanuser on 2009-03-13
> **mb_webguy said:**
> **Purely for managing files on your iPod, you can't really do any better than gtkpod.**

Just yesterday, one of my mother's coworkers bought an iPod Nano and asked me to load it with music from her CD collection.  I used Sound Juicer to rip the CDs, Album Cover Art Downloader to add the album covers to the mp3s, and gtkpod to load the mp3s onto the iPod.  You can install all of these from the repos with the command "sudo apt-get install gtkpod albumart sound-juicer".

**gtkpod also supports the transfer of photos and videos, unlike some of the other applications.**  I've ripped a couple of my sister-in-law's DVDs to mp4s using Handbrake to put them on her iPod using gtkpod.

Amarok, Rhythmbox, and Banshee should all play music on an iPod without any problem.

Thanks. :) Yes, that is more of what I'm looking for than anything else. ;) I just want the best program for managing files for my iPod (i.e. easily transferring all of my music and videos, etc. from my computer) in Ubuntu. Of course, the ability to also listen to music (and perhaps watch movies) on my iPod from the same program would also be nice. :) Basically, what I'm looking for is the Ubuntu equivalent to iTunes.

Cheers.

-Jam man

:guitar:

---

### Post by Xero Xenith on 2009-03-14
AFAIK you can't get better than gtkpod for pure iPod features, but its GUI is very unfriendly compared to other players. It just about matches iTunes for features, not usability; if you can get used to it, you're flying :)

---

### Post by Jammanuser on 2009-03-14
Alright, well I'll give gtkpod a try then. :) If I decide I like it, then I'll go with it. If I decide I don't due to an unfriendly userface, then I'll just try something else.

Cheers.

-Jam man

:guitar:

---

### Post by Jammanuser on 2009-03-14
> **mb_webguy said:**
>   You can install all of these from the repos with the command "sudo apt-get install gtkpod albumart sound-juicer".


Ok, I ran that command, and got the following message:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
**E: Couldn't find package albumart**

and then it stopped. For some reason, it can't find the package called "albumart". Any idea on how to fix this problem?

-Jam man

:guitar:

EDIT: I just installed gtkpod and soundjuicer separately, but I'm still unable to install albumart.
I tried "sudo apt-get install albumart" by itself, but got the same message. I would like to install that program too, but have no idea on how to get around this problem. Please help. Thanks.

---

### Post by mb_webguy on 2009-03-14
Ah... sorry about that.  I saw the package in Synaptic and forgot I installed it from a deb.  You can get the Album Cover Art Downloader [here]("http://www.unrealvoodoo.org/hiteck/projects/albumart/").  Just click the button on the right that says "Debian Linux Download".

---

### Post by Jammanuser on 2009-03-15
Thanks, that worked :)

-Jam man

:guitar:

---

### Post by blaker1994 on 2009-03-15
Hey, i cant get gtkpod this is what i get,
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gtkpod

---

### Post by abn91c on 2009-03-15
Amarok 2.0 works well with my 5th Gen IPOD 30 gig video

---

### Post by blaker1994 on 2009-03-15
does it allow to add pictures? or videos? i cant find one that does.

---

### Post by LiamWilson on 2009-03-15
No. But you can find gtkpod in add/remove. (Applications->Add/Remove) just search for it.

---

### Post by dragos240 on 2009-03-15
I always used gtkpod, worked brilliantly.

---

### Post by white3454 on 2009-03-15
I prefer Amarok as my primary player and ipod manager.  However I have also used Songbird in the past (they've made some major improvements lately) and never had an issue with my 1st gen Nano.

---

### Post by blaker1994 on 2009-03-15
i downloaded GTKpod, but my music wont sync to the ipod:(,it is in mp3 format, any help please? btw, i have gen 4 ipod nano (just got at walmart :P)

---

