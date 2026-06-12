---
title: "Can't find ximagesrc when installing istanbul"
date: 2006-08-02
forum: Desktop Environments
---

### Post by RyanTMulligan on 2006-08-02
I'm having a problem when compiling the latest version of Istanbul. When I finish compiling it and I run it, I get this error in a dialog box: You do not have the ximagesrc GStreamer plugin installed    .: 

I am using ubuntu dapper

---

### Post by RyanTMulligan on 2006-08-02
I fixed it with this fix....

```
sudo cp /usr/local/lib/gstreamer-0.10/libistximagesrc.so to /usr/lib/gstreamer-0.10/
```

[http://zaheer.merali.org/articles/2006/07/28/istanbul-0-2-1-freedom-to-record-speech-released](http://zaheer.merali.org/articles/2006/07/28/istanbul-0-2-1-freedom-to-record-speech-released)

---

### Post by ToneDispenser on 2006-09-16
Thanks for the hint!
Worked for me, too.

---

