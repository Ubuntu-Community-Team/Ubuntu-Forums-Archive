---
title: "was nautilus wouldn't start, now error message"
date: 2009-12-18
forum: Desktop Environments
---

### Post by rebeltaz on 2009-12-18
After plugging in a Sansa media player, Nautilus shutdown and would not come back up, unless I rebooted. Every time. So I ran Nautilus from the terminal to see what was going on. I got this message:

```

(nautilus:2282): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed

** (nautilus:2282): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:2282): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:2282): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Initializing nautilus-gdu extension
Segmentation fault

```

So, following the advice of SEVERAL posts, I removed the ~/.local/share/gvfs-metadata directory. Now when I run Nautilus, it comes up, but I still get the warning about the preferences. 

Any way to fix this... and what is causing it? Thanks.

---

