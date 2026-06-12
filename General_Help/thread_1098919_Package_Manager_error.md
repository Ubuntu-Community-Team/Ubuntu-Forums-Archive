---
title: "Package Manager error"
date: 2009-03-17
forum: General Help
---

### Post by sinamorawej on 2009-03-17
Hey
is it me or the new updates are really unreachable??
here is what i get when trying to install:

```
W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libavutil1d_0.cvs20070307-5ubuntu7.2_amd64.deb
  Size mismatch


W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libavcodec1d_0.cvs20070307-5ubuntu7.2_amd64.deb
  Size mismatch


W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libavformat1d_0.cvs20070307-5ubuntu7.2_amd64.deb
  Size mismatch


W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libpostproc1d_0.cvs20070307-5ubuntu7.2_amd64.deb
  Size mismatch



```

---

### Post by LegendofTom on 2009-03-17
Looks like a corrupted partial download.  Try:
```
sudo apt-get clean
sudo apt-get update
```

---

