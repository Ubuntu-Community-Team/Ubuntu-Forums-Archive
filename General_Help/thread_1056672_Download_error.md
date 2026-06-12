---
title: "Download error"
date: 2009-02-01
forum: General Help
---

### Post by Uubnewb on 2009-02-01
Every time I try to download something via the Add/Remove Applications feature I get these type of messages:


W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/pool/main/f/ffmpeg-debian/libavformat52_0.svn20080206-12ubuntu3_amd64.deb](http://za.archive.ubuntu.com/ubuntu/pool/main/f/ffmpeg-debian/libavformat52_0.svn20080206-12ubuntu3_amd64.deb)
  Could not resolve 'za.archive.ubuntu.com'

W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/pool/universe/g/gstreamer0.10-ffmpeg/gstreamer0.10-ffmpeg_0.10.5-1_amd64.deb](http://za.archive.ubuntu.com/ubuntu/pool/universe/g/gstreamer0.10-ffmpeg/gstreamer0.10-ffmpeg_0.10.5-1_amd64.deb)
  Could not resolve 'za.archive.ubuntu.com'


How can I work around this?

---

### Post by taurus on 2009-02-01
You can try another server.

---

### Post by JJ500 on 2009-02-01
> **taurus said:**
> You can try another server.

How does one specify the server to download from?

---

### Post by Uubnewb on 2009-02-01
>  You can try another server. 

I did think about it, but I have absolutely no idea how to.  Can you tell me how, please?

Also, and I should probably have mentioned it earlier, it was only after I downloaded the latest security updates.  Could that have messed something up?

---

### Post by Uubnewb on 2009-02-01
OK it looks like I found out where to change the download server.  For anyone else that want to switch to a different server go to:

System>Administration>Software Sources.  Under the "Ubuntu Software" tab (first one) go to "Download from:" and choose your prevered server.

So far it appears to be working fine once more.

Thanks for the help.

---

