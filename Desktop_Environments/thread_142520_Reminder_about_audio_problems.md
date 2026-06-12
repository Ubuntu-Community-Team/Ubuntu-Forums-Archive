---
title: "Reminder about audio problems"
date: 2006-03-10
forum: Desktop Environments
---

### Post by JDavid5381 on 2006-03-10
Hey, I know most of ya'll already know what about to say, but for others like me who are new to learning about Operating systems, and particularly Ubuntu (Linux) then this might be of help.

I recently thought something was seriously wrong with my audio devices and my soundcards because none of my CD's or Mp3's were playing that had been playing fine before. I would get an error alert saying "Playback error, could not open resource for writing" I had no idea what it meant and posted numerous threads to the desktop forum for advice on how to fix it. I even contemplated re-installing Ubuntu.

Now here's the part where I feel awful like a pesky moron.  I was telling my friend about it who has Ubuntu as well and he gave me the answer to my problem in one simple question: "did you try re-booting?" Well I took his advice and tried it and there I had the answer to my problem, everything working fine again.  So if anyone ever has a similar problem with their audio devices remember before you post about it, try rebooting first.  Sometimes the simplest solutions go right over our heads, or mine at least.

Peace out,
James

---

### Post by IYY on 2006-03-10
This is indeed a problem, and it should be fixed. But for now, there are easier ways to manage than a reboot:

Run **top**, and look for a process that is stealing the soundcard. Something like sox, esd, or even xmms or beep. Then kill it. It should help.

---

