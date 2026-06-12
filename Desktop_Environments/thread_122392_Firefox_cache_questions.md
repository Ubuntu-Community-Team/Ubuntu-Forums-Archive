---
title: "Firefox cache questions"
date: 2006-01-27
forum: Desktop Environments
---

### Post by mattack on 2006-01-27
For reasons of my own, I'd like to know exactly how the cache works. I'm using FF 1.0.7 on Breezy
My FF cache is set to use up to 50000 KB of disk space and I haven't emptied it in weeks. I use FF every day, sometimes for several hours. However my ~/.mozilla/firefox/default.alx/Cache folder is only 18 MB (that's 18432 KB) and the oldest file is 4 days old. 
I repeat, I did not clear any cache, cookies, history, saved form info, etc...
Would any other program that access the web (such as downloading CD covers in amaroK) clear the FF cache?
When the cache is full, how does it decide what to delete?
What is stored in the ~/.mozilla/firefox/default.alx/Cache folder besides images and html?
Where are cookies stored?
Any insite you could provide would be appreciated.
Thanks

---

### Post by jrib on 2006-01-28
about:cache in the firefox url bar may be helpful to you

I don't know the specifics of how firefox chooses what to delete, although I would assume it deletes the data that hasn't been accessed in the longest time.

Cookies are in ~/.mozilla/firefox/*.default/cookies.txt I believe.

---

