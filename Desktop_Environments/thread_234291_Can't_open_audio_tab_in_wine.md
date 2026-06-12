---
title: "Can't open audio tab in wine"
date: 2006-08-11
forum: Desktop Environments
---

### Post by MikeEnIke on 2006-08-11
I got wine installed 0.9.18 if I'm not mistaken and I even got steam and CS:S installed. My problem is I can't configure the audio one wine.```
mike@mike:~$ winecfg
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
Creating link /home/mike/.kde/socket-mike.
can't create mcop directory
mike@mike:~$

```
Does anyone know what I can do to fix this?

---

### Post by kaffelars on 2006-08-11
I had the same problem, and found the solution here on the forum. Seems like this is a common problem. Can't remember what the solution was though, but just do a quick search :)

---

### Post by MikeEnIke on 2006-08-11
Alright I think I found it after searching the one search term I hadn't tried. Unfortunately, it did not fix my problem with Counter-Strike Source not starting up correctly. Hmm.

---

### Post by littlespy on 2006-08-11
HL2 and source games are a mess with wine.  You should try [cedega]("http://transgaming.org") it has better directx support.

Don't bother paying for it though, it's still not very mature and I havn't had much luck getting games to run properly.  What I ended up doing is just making a small 10gb windows partition and booting into windows to play games; annoying I know, but there is just no such thing as good linux gaming. (unless it's native :))

---

