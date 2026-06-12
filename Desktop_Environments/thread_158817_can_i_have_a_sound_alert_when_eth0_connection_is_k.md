---
title: "can i have a sound alert when eth0 connection is killed ?"
date: 2006-04-11
forum: Desktop Environments
---

### Post by jamesford on 2006-04-11
i really need some way to be alerted when im not by the computer and my dsl connection is killed, which happens from time to time. is there a way somehow to play a wav file or something when the network is disconnected?

---

### Post by dcstar on 2006-04-11
[QUOTE=jamesford]i really need some way to be alerted when im not by the computer and my dsl connection is killed, which happens from time to time. is there a way somehow to play a wav file or something when the network is disconnected?[/QUOTE]
You should be able to put a script in your /etc/network/if-down.d directory.

---

### Post by jamesford on 2006-04-12
you mean like putting a shellscript that basically says "play /path/file.wav" into that folder?

---

### Post by dcstar on 2006-04-13
[QUOTE=jamesford]you mean like putting a shellscript that basically says "play /path/file.wav" into that folder?[/QUOTE]
I believe so, the man pages should give you more info but someone recently successfully put scripts in the "if-up" directory to manually set routes.

Scripts in these are supposed to be used when the connections either go up or down.

---

