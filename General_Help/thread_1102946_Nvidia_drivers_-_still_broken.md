---
title: "Nvidia drivers - still broken"
date: 2009-03-22
forum: General Help
---

### Post by gersoid on 2009-03-22
I have a dell inspiron 1520 + nvidia 8600M GT. I upgraded to 8.10 / 26.13; the nvidia drivers broke and I had no desktop. Installed nvidia-glx-180 via the official package, desktop now OK but can't use Bibble 5 (digital camera RAW software) . I then tried to roll back to nvidia 1.73 but apt-get refused saying that there was an unresolved dependency on linux-restricted-modules.  OK not great but can live with it; I have my desktop.

Got upgraded to 26.14 yesterday, nvidia driver broken again, will only boot in lo-res, already had 1.80 installed so wouldn't upgrade. I still can't roll back to nvidia 1.73. I cannot be bothered messing around with manual nvidia upgrades, I don't want to waste all afternoon worrying about which runlevel I'm in. 

solution : I installed Fedora 10, works fine with nvidia 1.8+, I was able to roll back happily to 1.73, now have Gnome desktop + Bibble 5 working too, which for whatever reason I could not do under ubuntu. I should not be in the situation where a packaged install of the video driver is broken by a kernel update, and if it is broken, I should be in a position where I can roll back (I don't give a toss about the "latest & greatest" nvidia driver version). 

I'm off now. Suggest you guys focus on the testing/packaging of nvidia drivers.

---

