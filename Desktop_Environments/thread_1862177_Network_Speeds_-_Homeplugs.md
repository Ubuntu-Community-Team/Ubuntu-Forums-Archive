---
title: "Network Speeds - Homeplugs"
date: 2011-10-16
forum: Desktop Environments
---

### Post by Geffers on 2011-10-16
I've got some 200mbps homeplugs, two Devolo and one 7dayshop.

Now I appreciate g should give 54mbps, I've never got anywhere near but I was expecting better with the homeplugs.

Using a dd command as follows;

```
dd if=/dev/zero bs=256 count=1048576 | pv | ssh username@localIP 'cat > /dev/null'
```  

I got 2.7MB per second and marginally better, around 2.9MB per second with the homeplug so that relates to about 0.5 expected speed from the wifi and 0.25 expected speed from the homeplug.

Anyone else had similar experience.

Geffers

---

