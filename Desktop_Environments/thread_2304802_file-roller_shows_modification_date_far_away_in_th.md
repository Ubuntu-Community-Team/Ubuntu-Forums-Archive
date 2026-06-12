---
title: "file-roller shows modification date far away in the future w/RAR archives"
date: 2015-11-30
forum: Desktop Environments
---

### Post by syntaxerror74 on 2015-11-30
Hey folks,

this is getting on my nerves. file-roller v3.16.4.
For nearly every RAR archive opened with file-roller, the application will show dates of the files contained within in the far future, e. g. 27 March 2028 or similar nonsense.
Am I the only one to experience this?

Already tried to report this bug "upstream" (like it's commonly called so euphemistically) but got no reply after quite some time of waiting.

My patience is about to come to an end now.
In the meantime, I simply tried to start file-roller on console, locale-independent, ( LC_ALL=C file-roller & ) but it didn't fix the problem.
Archives are all 100% ok and not corrupt anywhere, since the real dates do show up when doing 'rar lv somearchive.rar'.

---

