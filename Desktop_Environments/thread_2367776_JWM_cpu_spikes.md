---
title: "JWM cpu spikes"
date: 2017-08-03
forum: Desktop Environments
---

### Post by eztoastmacrowoosh on 2017-08-03
Anyone else having large cpu spikes using JWM on Ubuntu? It seems moving windows or mouse spikes the cpu very high. I'm not sure if its the latest nvidia hardware or a Xorg update possibly causing it. I have tried compiling newer JWM code with different flags and its still having the same glitch as the copy in the repository.

Openbox seems entirely unaffected. I'm not sure how such a small footprint of code can be glitching up so bad. Could it possibly be an error with 2d rendering? Does this have to do with framebuffers or some old X server black magic?


Possibly Related:
I read a bug report about cpu spikes on a Xubuntu system caused by Xmodmap: [https://askubuntu.com/questions/914148/xorg-high-100-cpu-on-xubuntu-17-04](https://askubuntu.com/questions/914148/xorg-high-100-cpu-on-xubuntu-17-04)

---

