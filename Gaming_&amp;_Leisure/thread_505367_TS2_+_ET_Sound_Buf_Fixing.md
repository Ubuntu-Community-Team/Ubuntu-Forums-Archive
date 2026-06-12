---
title: "TS2 + ET Sound Buf Fixing"
date: 2007-07-20
forum: Gaming &amp; Leisure
---

### Post by Jonathan93 on 2007-07-20
Hello :)


I'm New too Ubuntu and i don't know how to fix this sound bug i want to run ET (Enemy Territory)
and TS2 at the same time and hear both sounds, Ive tried too google around but dident find anything i understood, I'm 13 so... i would like if some some could tell me how too do in a easy way ;)




Thanks in advance Jonathan!

---

### Post by AthlonMDK on 2007-07-24
this solved it for me:

Open a console (dos screen)

type:
*sudo -s -H*
it will ask for the root password.
then go to the et map for example:
*cd /usr/local/games/enemy-territory/*
the type:
*echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0c/oss*
then type to get out of root terminal, playing the game might not be wise:
*exit*
now to play the game as user
*./et *

this ought to do it

---

### Post by Jonathan93 on 2007-07-25
Well is it some way to get this in to a short cut? and wen i launch in this way i dont got the files ive dowloaded b4 :(

---

