---
title: "Hard drive full with nothing on it"
date: 2008-04-12
forum: Desktop Environments
---

### Post by geert.vansintjan on 2008-04-12
I run Kubuntu 7.10 on an Everex Gpc. 

My main partition tells me there is only 500 Mb left of the 17 Gb. However, analyzing with Kdirstats and other programs it shows only some 5 Gb of data. I have a separate partition with /home. 

I have run all the found  cleanup possibilities: clean, orphan, locale, cache, and empty basket cleanups 

I wanted to upgrade, hoping I could bypass in some elegant way, but nope. 

Any reason why I might have run into this? Any solution? 

Thanks

---

### Post by bingoUV on 2008-04-13
Having no knowledge of amount of your experience with linux, we have to ask for some basic diagnostics. Please report the output of the following commands. The third one might take a while (expect not more than 10 minutes on 17GB hard disk, but I could be wrong)
```

mount
df -h
sudo du -h / --max-depth=1

```

---

