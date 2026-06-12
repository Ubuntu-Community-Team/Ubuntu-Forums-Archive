---
title: "Complete removal of Mythbuntu"
date: 2009-08-09
forum: Desktop Environments
---

### Post by linuxus95 on 2009-08-09
Hi,

I recently installed the Mythbuntu desktop environment on top of my Jaunty distribution. I would like to remove Mythbuntu completely, along with all the software that got installed with the mythbuntu-desktop package. When I try to remove mythbuntu-desktop from the terminal, I don't get a list of all the other packages I can autoremove. Is there a short way to do this or do I just have to go into Synaptic and remove the packages one by one? Any help would be greatly appreciaed.

---

### Post by .nedberg on 2009-08-09
You _should_ be able to do
```

sudo apt-get autoremove mythbuntu-desktop

```
in terminal.

---

