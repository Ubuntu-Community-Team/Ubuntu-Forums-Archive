---
title: "Evince failing to open links in Chromium"
date: 2014-01-26
forum: Desktop Environments
---

### Post by kathrync on 2014-01-26
When I click on a link in Evince, it won't open in Chromium (my default browser).  The error at the terminal is:

```
/usr/lib/chromium-browser/chrome-sandbox: error while loading shared libraries: libstdc++.so.6: failed to map segment from shared object: Permission denied
```

This is occurring on two computers that are both running 13.04, but not on my desktop which is running 12.10.

I have seen the thread here describing a similar bug: [http://askubuntu.com/questions/317928/hyperlinks-clicked-in-evince-document-viewer-are-not-opening-any-ideas-on-how-t](http://askubuntu.com/questions/317928/hyperlinks-clicked-in-evince-document-viewer-are-not-opening-any-ideas-on-how-t) 

I followed the instructions in this thread, but the lines it suggested adding to /etc/apparmor.d/abstractions/ubuntu-helpers were already there and running apparmor-parser didn't make any difference, so I can only assume this is something else.

Anyone have any ideas?

---

### Post by kathrync on 2014-01-28
No-one??

---

