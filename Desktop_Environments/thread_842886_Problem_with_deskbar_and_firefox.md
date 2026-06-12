---
title: "Problem with deskbar and firefox"
date: 2008-06-27
forum: Desktop Environments
---

### Post by rabusmar on 2008-06-27
Hello. I'm a little new to linux. I installed hardy x64 a while ago, and installed both firefox 2 and 3 with different profiles and no problems. However, recently a found the deskbar applet, but in the "extensions with errors" tab it appears the web bookmarks, web search and web history, with the error "Firefox version must be between 2.0.0.0 and 3.0.0.0". I have firefox 2.0.0.14, and 3.0 as my default browser. Any help is appreciated.

---

### Post by rod40cool on 2008-07-26
> **rabusmar said:**
> Hello. I'm a little new to linux. I installed hardy x64 a while ago, and installed both firefox 2 and 3 with different profiles and no problems. However, recently a found the deskbar applet, but in the "extensions with errors" tab it appears the web bookmarks, web search and web history, with the error "Firefox version must be between 2.0.0.0 and 3.0.0.0". I have firefox 2.0.0.14, and 3.0 as my default browser. Any help is appreciated.

Try editing this file
```
$ sudo gedit /usr/lib/deskbar-applet/modules-2.20-compatible/mozilla.py
```
Change line 36 to :
MAX_FF_VERSION = [3, 1, 0, 0]

You'll have to hit reload in the deskbar preferences then re-enable the Web Searches (Mozilla) extension.

This work around is documented [here.]("https://bugs.launchpad.net/ubuntu/+source/deskbar-applet/+bug/205018")

It works for me.

---

