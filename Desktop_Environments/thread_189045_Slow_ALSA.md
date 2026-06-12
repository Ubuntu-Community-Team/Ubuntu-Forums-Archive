---
title: "Slow ALSA?"
date: 2006-06-04
forum: Desktop Environments
---

### Post by DrBair on 2006-06-04
I've noticed in past, especially in multimedia applications, that ALSA output always seems slower than OSS output.  

Today I installed JACK and started playing around with that, and I started getting xruns (lag over 9ms) like crazy on my very well equipped desktop.  Out of curiosity, I tried changing JACKs backend to OSS and jackd has been running for about 10 minutes now without a single xrun. 

Now it was my assumption that ALSA has OSS support in it, so OSS applications essentially talk to ALSA. Why is it that ALSA is so slow?

---

### Post by JoWilly on 2006-06-04
Dunno. Have you tried filing bug reports on this ?

---

