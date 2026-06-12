---
title: "Xfmedia Codecs"
date: 2006-09-26
forum: Desktop Environments
---

### Post by heydabop on 2006-09-26
Where can I get more Xfmedia codecs?

---

### Post by croak77 on 2006-09-26
It uses xine. So you do you have libxine-extracodecs and the w32codecs installed? libxine-extracodecs is in multiverse and for w32codecs, open a terminal and type;
```

wget -c http://packages.freecontrib.org/ubuntu/plf/pool/dapper/non-free/w32codecs_20060611-1plf1_i386.deb
sudo dpkg -i w32codecs_20060611-1plf1_i386.deb
```

---

### Post by heydabop on 2006-09-26
K, installed the codecs, but it still doesn't play .mp4 or .oma and I'd like it to play those. Are there any codecs for that?

---

### Post by croak77 on 2006-09-27
Are these DRM protected files?

---

### Post by DirtDawg on 2006-09-27
> **heydabop said:**
> K, installed the codecs, but it still doesn't play .mp4 or .oma and I'd like it to play those. Are there any codecs for that?

XMMS plays Mp4's. XMMS can be found in the repos and then look for a package called xmms-mp4 (I believe). I'm not too sure about .oma.

Sorry I have no suggestions for xfmedia.

---

### Post by heydabop on 2006-09-27
Ok, I'll look for the xmms. Thanks.

---

### Post by pseudonym on 2006-09-27
I play mp4s with xfmedia (dunno about .oma). You may need to point the xine config file to the right location of the codecs. Instructions on doing so can be found [here]("http://nongeeksight.blogspot.com/2006/07/multimedia-in-xubuntu-made-easy.html").

---

