---
title: "weird setup (soundcard)"
date: 2009-03-22
forum: General Help
---

### Post by sandyd on 2009-03-22
ok, heres something interesting
I always wondered why all the sound that came through ALSA was stuttery, and didn't work with some programs, so today, i finally got to looking at the problem.

Now, heres the interesting part. I was cheap, so i got a neomagic 256 for my soundcard. 
I looked all over the place for the problem. THen, in desperation, i looked in /etc/modules.

and there was the problem. no snd-nm256 in that file
as far as i was concerned, i had to run modprobe snd-nm256 to get my sound working.

why didn't ubuntu set up my soundcard properly?
or is that specific driver blacklisted?

---

