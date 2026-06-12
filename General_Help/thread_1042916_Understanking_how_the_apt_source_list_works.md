---
title: "Understanking how the apt source list works"
date: 2009-01-18
forum: General Help
---

### Post by moyam01 on 2009-01-18
As I get more and more used to Ubuntu, I started a lot of stuff on the command list. Anyway, I was adding the medibuntu repositories that I found in the How to's 

sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) --output-document=/etc/apt/sources.list.d/medibuntu.list

One thing that I notice is that it makes a new sources.list.d directory and then adds another list. It was my understanding that all repositories that were used for apt were in /etc/apt/sources.list, and I find no refrence to the new file in that file. So how does apt now to look in the newly created directory?

---

### Post by itix on 2009-01-19
I don't know... Have yoou tried *sudo apt-get update*. If is lists reading from medibuntu, you have succeded.

If you have suceeded, I suppose that apt-get reads the apt directoy recursively.

---

