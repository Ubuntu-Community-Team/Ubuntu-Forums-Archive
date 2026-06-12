---
title: "Dependency question...."
date: 2005-06-18
forum: Desktop Environments
---

### Post by escobar on 2005-06-18
I normally use Aptitude, but noticed when I removed a Nessus, the dependcies that were installed with it were not removed. Is there anyway to find out what these are and remove them? I did use "aptitude purge" if that matters any. 


Thanks.

---

### Post by Xian on 2005-06-18
If I'm not mistaken doesn't aptitude list the deps of packages?

---

### Post by intangible on 2005-06-18
Have you tried out **deborphan**?  It seems to do a pretty good job helping you find out which libraries aren't required by installed packages.

---

### Post by escobar on 2005-06-18
[QUOTE=intangible]Have you tried out **deborphan**?  It seems to do a pretty good job helping you find out which libraries aren't required by installed packages.[/QUOTE]

I installed deborphan, and it did appear to find a few packages that were no longer needed. I wasn't able to find anything in Synaptic that tells me what was installed with a specific app. I was able to find what the dependencies are though. Either way, no big deal. Think I'm good to go. Thanks.

---

