---
title: "Amarok error: Malformed URL."
date: 2009-04-27
forum: General Help
---

### Post by grutza on 2009-04-27
Yeah so this is probably already asked somewhere and I'm no good at looking on forums but oh well hopefully I don't get in trouble.

I have upgraded to Ubuntu 9.04 and installed Amarok (the newest one I believe) and the first day I had it installed I was able to transfer my music (Local Collection) to my ipod (/media/ALEX'S IPOD) and it brings up the error window saying "Malformed URL.". So I click "Cancel" and I can't seem to get it to transfer songs to my Ipod. I saw somewhere to type in terminal (I typed it under root) "mtp-detect" and the only thing that came up was 

"# mtp-detect
libmtp version: 0.3.0

Listing raw device(s)
   No raw devices found."

So I'm pretty much stuck as where to go from here.

---

### Post by kooldino on 2010-05-15
I have this exact same issue using a 4th gen nano.

---

### Post by kooldino on 2010-06-04
If you open it with gtkpod, it will notify you that a directory structure is missing.  Allow it to create it, and then close gtkpod.  Amarok should allow file transfers now.

---

