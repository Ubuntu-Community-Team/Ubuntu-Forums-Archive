---
title: "bug with changing screen resolutions &amp; gdm"
date: 2005-01-09
forum: General Help
---

### Post by mjb on 2005-01-09
Hello, I have no question but more of a bug report (I don't know where to post else and there might be a simple solution yet) 

I have multiple users on my system, one is using another resolution than I am (1024x768 instead of 1280x1024). GDM runs at 1280x1024 without any problem, if the user logs in the resolution is automaticly changed to 1024x768 (neat!). however, if he logs out, gdm is displayed at 1024x768 (incorrectly because it assumes the resolution is 1280x1024).

So I think the resolution should be changed back if the user logs out.

---

