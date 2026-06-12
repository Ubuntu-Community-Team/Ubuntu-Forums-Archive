---
title: "Soundcard used by another application"
date: 2006-08-15
forum: Desktop Environments
---

### Post by salem7 on 2006-08-15
At times when i try to play some music, the music player (be it xmms, real player,etc) give an error message noting that there might be something wrong with the card or that its used by some other application. How to overcome this?

---

### Post by tribaal on 2006-08-15
There is currently a bug with "esd". If what you are experiencing is related, a simple "sudo killall esd" in a terminal should get you out of trouble.

Hope this helps!

- trib'

---

### Post by salem7 on 2006-08-15
Your solution worked!! Thank you very much for the quick response. :D

---

### Post by salem7 on 2006-08-15
I'm taking back some of my words!!! Yes it worked but then the error came back again... i kill esd and it says that its dead already :confused: So how?

---

### Post by mdurham on 2006-08-15
Try logging out then logging in again, seems stupid but it works for me. I didn't know about the "killall esd" thing. Thanks for that tribaal.

---

