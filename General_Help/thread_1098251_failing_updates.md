---
title: "failing updates"
date: 2009-03-16
forum: General Help
---

### Post by jras20 on 2009-03-16
Here is my error:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libavutil1d_0.cvs20070307-5ubuntu7.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libavutil1d_0.cvs20070307-5ubuntu7.2_i386.deb)
  Size mismatch


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libavcodec1d_0.cvs20070307-5ubuntu7.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libavcodec1d_0.cvs20070307-5ubuntu7.2_i386.deb)
  Size mismatch


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libavformat1d_0.cvs20070307-5ubuntu7.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libavformat1d_0.cvs20070307-5ubuntu7.2_i386.deb)
  Size mismatch


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libpostproc1d_0.cvs20070307-5ubuntu7.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libpostproc1d_0.cvs20070307-5ubuntu7.2_i386.deb)
  Size mismatch

???????????

---

### Post by zvacet on 2009-03-17
I checked links and they are looking O.K.Try with 

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by jras20 on 2009-03-17
That fixed the update, thanks, but will I half to do that on every update now?  Or was that just one error?

---

### Post by Nano_ext3 on 2009-03-17
You shouldn't have to no, this happens sometimes when the sources are not current, so when you go to update, it cant find the source of the package files or source files.

Cheers!

-Nano

---

