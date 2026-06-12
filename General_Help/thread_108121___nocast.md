---
title: "__nocast"
date: 2005-12-25
forum: General Help
---

### Post by khateeb on 2005-12-25
hi all

I am trying to compile a program i downloaded but it keeps giving me errors. I checked the source and I found that all errors occur at variables declaired after __nocast.

I think __nocast is a kernel directive of some sort. Can anyone tell me how to make the compiler understand __nocast?

---

### Post by kaamos on 2005-12-25
What's the program?
Try installing the build-essential and linux-headers-$(uname -r) packages.

---

### Post by khateeb on 2005-12-25
[QUOTE=kaamos]Try installing the build-essential and linux-headers-$(uname -r) packages.[/QUOTE]

I have both build essential and linux headers of my kernel installed. the program is IEEE80211 driver

---

