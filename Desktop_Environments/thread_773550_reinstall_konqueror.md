---
title: "reinstall konqueror"
date: 2008-04-28
forum: Desktop Environments
---

### Post by Xiong Chiamiov on 2008-04-28
So, shortly ago, my konqueror installed got screwed up somehow, so that I can open it, but trying to view any folders crashes it. I ended up just using dolphin instead, but now I'm having problems with amarok that I'm pretty sure are tied to konqueror (since it embeds it). Reinstalling konqueror doesn't help, and I'd really prefer to not --purge it, since that will remove my kubuntu-desktop package. I tried renaming the konqueror binary and making a soft link to konqeror 4 (I have all the KDE 4 packages installed, but I'm using 3), but that doesn't fix the problem. Moreover, when I launch konqueror from the terminal, it launches 4, but from the run dialog, 3, which makes no sense whatsoever.

---

### Post by Xiong Chiamiov on 2008-04-29
Ok, so I deleted the files that related to konqueror in ~/.kde/share/apps and it works now.  However, the original problem remains, which is that amarok cannot submit to last.fm, fetch covers from amazon, or get artist info from wikipedia.  I was pretty sure that it had to do with konqueror, but I'm no longer sure.  Debating about moving this to main support.

---

### Post by Xiong Chiamiov on 2008-04-29
Since I couldn't find anyone to help anywhere on the net, and I capped the 500 queued tracks in amarok, I decided to figure it out myself.  Created a new user, tested config, then started narrowing down folders and files 'til I found it, kio_httprc in ~/.kde/share/config.  These were the contents:
```

MaxCacheSize=5120
UseCache=true
cache=CacheOnly

[$Version]
update_info=kioslave.upd:kde2.2/r1,kioslave.upd:kde2.2/r2


```
I'm guessing it's somehow related to [this]("https://bugs.launchpad.net/ubuntu/+source/kdelibs/+bug/208872").  I moved it elsewhere, and now things work again.  Yay.

---

