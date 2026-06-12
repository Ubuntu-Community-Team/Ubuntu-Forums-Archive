---
title: "Apt-get update: Hash sum mismatch - Help!!"
date: 2016-11-21
forum: Debian
---

### Post by eduardowoj on 2016-11-21
I'm encountering some problems with apt-get. This morning, after upgrading Firefox to the most up to date version, I decided to check if there were updates for the other packages, so I ran an "apt-get update". However, for some odd reason, it's precisely Mozilla's repository that isn't behaving well:

```

Ign http://repo.linrunner.de jessie/main Translation-en_US                     
Ign http://repo.linrunner.de jessie/main Translation-en                        
Fetched 106 kB in 7s (14.0 kB/s)                                               
W: Failed to fetch http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/dists/all/main/binary-amd64/Packages  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

Disclaimer: I'm actually running Debian 8, but since Ubuntu and Debian are almost conjoined twins, I'm trying this forum because I know the people here are really awesome from the time I used Ubuntu on the past!

I tried to remove and reinstall Ubuntuzilla repository (that's valid for Debian too, despite the name). Tried an "apt-get clean" but no dice. I'm still getting this error.

Any ideas?

---

### Post by howefield on 2016-11-21
Thread moved to the "*Debian*" forum.

---

