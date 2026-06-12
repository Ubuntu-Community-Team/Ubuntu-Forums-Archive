---
title: "Help playing DVDs"
date: 2006-08-09
forum: Desktop Environments
---

### Post by Thiago Tomei on 2006-08-09
Hello to all

First, let me assure you that I have searched the forums thoroughly, and I also tried my luck in Google. Nothing I found solved my problem, so here I am.

I can't play DVDs in Ubuntu, no matter what I do. When I try Movie Player:

Totem was not able to play this disc.
Failed to mount /dev/hda

GXine:

The xine engine failed to start.
No input plugin was found.
Maybe the file does not exist or cannot be accessed, or there is an error in the URL.
Read error from:
/dev/dvd

VLC just hangs on me.

The relevant entry in my /etc/fstab:
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

And I have also this link:
$ file /dev/dvd
/dev/dvd: symbolic link to `hda'

I'm running Ubuntu 6.06 (Dapper Drake), 64-bit version:
Linux ******** 2.6.15-26-amd64-generic #1 SMP PREEMPT Thu Aug 3 02:52:35 UTC 2006 x86_64 GNU/Linux

And the drive works for mounting normal CDs, listening to audio CDs AND for burning CDs. Also, I have tried the "install libraries" stuff suggested in other FAQs. Nothing seems to work. I'm rather sure, however, that this is not the "encrypted DVD" problem, for I'm trying to play an anime DVD bought from a fansubber, and those kinds of DVDs are usually burned in a desktop computer. By the way, the DVD itself is in mint condition, and I managed to watch it in my friend's laptop (running some flavor of Slackware Linux).

Thanks in advance
Thiago

---

### Post by computergroove on 2006-08-10
Im guessing burnt out dvd laser eye. A dvd drive has differnet components that read cd's and dvd's and write to cd's and dvd's. I have run into several drives (which I repair for a living) which played cd's fine but dvd's would not read. Try your dvd drive on someone elses computer and see if you can get a dvd to play on another machine. Then you'll know if its ubuntu or your drive.

---

### Post by Thiago Tomei on 2006-08-12
Hmmm... ok, I'm updating the status.

I tested with some other DVDs. The drive is fine actually. Played my Nightwish - End of Innocence DVD fine, but couldn't play my old Final Fantasy  VII - Advent Children. I'm guessing the problem would be with BURNED DVDs, them? Does anybody know if there's any difference, playing-wise, between a burned DVD and a commercial one?

---

