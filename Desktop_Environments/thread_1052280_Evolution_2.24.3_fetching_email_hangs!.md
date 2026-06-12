---
title: "Evolution 2.24.3 fetching email hangs!"
date: 2009-01-27
forum: Desktop Environments
---

### Post by bhoth on 2009-01-27
Hi All,

I have been running Ubuntu 8.10 with Evolution 2.24.2 for the last two weeks then my hard drive crashed yesterday around lunchtime. Luckily, I had made a complete backup of my data and email (using the backup option in Evolution)the morning before the crash.

I went and bought a new hard drive, did a new install on the new hard drive. I restored the Evolution backup, looks like the package has been updated to 2.24.3. Now about half the time, when it does an email fetch, it basically hangs. I have to force it to close.

Any ideas?  I tried to search on issues with 2.24.3 but I could not really find anything.

Thanks

---

### Post by exploder on 2009-01-27
I installed all of the 2.24.3 Evolution packages from the proposed repo and have had no problems. Try enabling the proposed repo to see if all of the Evolution related packages are at the 2.24.3 version.

---

### Post by r m h on 2009-02-20
I'm running 2.24.3 and have had to turn off automatic checking for email.  Evolution continues to hang when sending/receiving.

I have 7 POP accounts that I check.  Even when manually checking for new mail/sending mail, Evolution will hang about every 16th to 20th time I click the send/receive button.  

I kill all Evolution processes and restart Evolution; it will work for another ~20 send/receives, then hang.

Very frustrating that this bug still exists, and is exacerbated if I turn on automatic checking for mail (that ~20th check happens more frequently).

Any assistance I can provide with help debugging this?

Thanks

---

### Post by brimlar on 2009-03-12
Forgive me if this is a bit too sledgehammer-ish, but I fixed this issue on my laptop by renaming the .evolution folder in my home directory to something else ("EvolutionBackup" for instance) and then re-launching Evolution.

It worked fine upon next start.

---

### Post by cptr13 on 2009-03-15
Do you have the RSS plugin installed?  It always hangs like that for me when I have the rss installed.  If I remove it, it works fine again.

---

