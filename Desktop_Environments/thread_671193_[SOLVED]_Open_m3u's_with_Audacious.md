---
title: "[SOLVED] Open m3u's with Audacious"
date: 2008-01-18
forum: Desktop Environments
---

### Post by sceo on 2008-01-18
Whenever I double-click an m3u file, it asks me to 'run' or 'run in terminal' (or cancel, or display).  Neither of the "run's" actually cause it to open Audacious and play the playlist.  When I right-click an m3u and go to "properties" and pick the "open with" tab it's already set to Audacious.  How can I set Nautilus to fire Audacious with this m3u as a command-line param (presumably?) instead of prompting.  Do I need to chmod -x the m3u file(s)?

---

### Post by logos34 on 2008-01-18
> **sceo said:**
> Do I need to chmod -x the m3u file(s)?

mine's not and it opens directly (w/o prompt) in audacious.  I have 'open with' set to latter.  If I set it to 'text editor' it opens fine with that too.

---

### Post by sceo on 2008-01-18
Well, chmod -x wasn't it.  But apparently "display" actually causes it to "run" with its associated application.  So, I set Nautilus (preferences -> behavior tab) to always "view" the file and not ask, and so it works (opens with audacious).  Go figure.

---

