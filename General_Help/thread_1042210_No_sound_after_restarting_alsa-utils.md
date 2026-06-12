---
title: "No sound after restarting alsa-utils"
date: 2009-01-17
forum: General Help
---

### Post by computer_freak on 2009-01-17
I am currently running 8.10 intrepid ibex and I had a problem where even though sound was muted, I could still hear my music from the computer. My friend who runs a ubuntu server and helps me with Ubuntu told me to run this command, and then the one after it:
 sudo /etc/init.d/alsa-utils stop
 sudo /etc/init.d/alsa-utils start
My sound completely died after that. I could still change volume levels, but no matter what, I could not get any sound. Its not the source, because i have tried youtube, mp3, banshee, and others, and none of them work. 
My sound card is still visible to my computer too.  I have tried restarting(9 times so far) and nothing new happens. Does anyone know what happened/what to do? Thanks

---

### Post by yoyoned on 2009-01-17
use alsa-mixer to make sure all the levels are up and nothing is muted

---

### Post by computer_freak on 2009-01-17
I just tried that and everything was at full volume, nothing muted at all.
Also, maybe unrelated:
The buttons on the front of my computer(hp pavillion zv6000) cause segfaults when pushed, and sometimes kernel panics. Could these have anything to do with it?

---

### Post by computer_freak on 2009-01-17
I don't know what i did, but now the sound card is working again.

---

