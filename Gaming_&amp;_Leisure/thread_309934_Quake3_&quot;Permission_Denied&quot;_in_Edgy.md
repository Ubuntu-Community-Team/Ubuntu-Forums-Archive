---
title: "Quake3 &quot;Permission Denied&quot; in Edgy"
date: 2006-11-30
forum: Gaming &amp; Leisure
---

### Post by fragmental on 2006-11-30
I'm running Ubuntu Edgy and I recently installed Quake3.  I tried the ioquake3 binaries from the installer at ioquake3.org, I tried some ioquake3 binaries that someone else compiled, I compiled my own ioquake3 binaries from svn, and I also tried the original quake3 binaries from ID software.  All of them say "Permission denied" when I try to run the binaries from the console.  If I run a script it says something like "bash: ./quake3: /bin/sh: bad interpreter: Permission denied". 

I set all the files in the quake3 directories to be owned by the user and I made sure all the binaries were executable.  I really don't get this.  Could it have something to do with SE Linux or something?  Planet Penguin Racer runs fine.

Baffled:confused:

---

### Post by zgornel on 2006-11-30
Go into the Quake3 dir and write: sudo chown -hR ./* <your user>. This makes you owner off all the files. maybe some permissions were wrong ...

---

### Post by fragmental on 2006-11-30
From my post above: "I set all the files in the quake3 directories to be owned by the user and I made sure all the binaries were executable." 

I figured out what the problem was.  The partition that I had the game on wasn't able to execute files.  I had to add "exec" to the options in fstab.  I'm not completely sure why but it could be because I had "users" in the options. I had to add "exec" AFTER "users".

---

