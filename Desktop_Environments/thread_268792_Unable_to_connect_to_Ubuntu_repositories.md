---
title: "Unable to connect to Ubuntu repositories"
date: 2006-09-30
forum: Desktop Environments
---

### Post by CJK on 2006-09-30
I've just recently encountered some trouble with Synaptic. When downloading packages from repositories once functional, I get an error message; 

> W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/g/gst-ffmpeg/gstreamer0.8-ffmpeg_0.8.7-5ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/g/gst-ffmpeg/gstreamer0.8-ffmpeg_0.8.7-5ubuntu1_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

This happens when trying to download from any repository available to Synaptic. 

Any help would be greatly appreciated.

---

### Post by Kateikyoushi on 2006-09-30
Do you have anon-proxy installed ? Check it with synaptic.

---

### Post by CJK on 2006-09-30
Yes, I do have anon-proxy installed.

Is that why it is refusing my connection?

---

### Post by Kateikyoushi on 2006-09-30
Yes, if you do not use it just remove it and it should work.

---

### Post by CJK on 2006-09-30
Thank you one-thousand times!

---

### Post by CJK on 2006-09-30
Edit

---

