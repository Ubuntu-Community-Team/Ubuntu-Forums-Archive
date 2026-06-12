---
title: "Firefox occasionally borks itself"
date: 2011-11-04
forum: Desktop Environments
---

### Post by isecore on 2011-11-04
Every so often Firefox will decide it doesn't want to start. Even though it was shut down properly, all it does when I try to start it again is show a broken Session Manager window. After killing and restarting it for a random amount of times (usually around 40-50 times) it tends to go away.

But it's still annoying, and I need it to go away. Any hints?

Affix a screenshot of what it looks like.

---

### Post by lovinglinux on 2011-11-04
Try to delete *sessionstore.js* file from your Firefox profile, located under ~/.mozilla/firefox/<profilefolder>.

If that doesn't help, you could [change the session properties in about:config](http://kb.mozillazine.org/Session_Restore), but that would reduce the browser functionality. I would try [Session Manager](https://addons.mozilla.org/en-US/firefox/addon/session-manager/) extension.

---

