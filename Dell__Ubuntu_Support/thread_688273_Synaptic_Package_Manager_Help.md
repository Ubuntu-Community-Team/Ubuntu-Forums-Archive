---
title: "Synaptic Package Manager Help"
date: 2008-02-05
forum: Dell  Ubuntu Support
---

### Post by dhedrick on 2008-02-05
I'm trying to open Synaptic Package Manager, which has worked for me plenty of times in the past (every time until this morning), and now I'm getting this error:

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

I'm completely new to Linux (2 weeks or so), and really don't know what this error means, how to fix it, or how to report it like it is requesting.  Can someone please walk me through what to do here?

Thanks in advance for your help!

~ Dale

---

### Post by agim on 2008-02-05
Open a terminal and enter this command:

dpkg --configure -a

This usually happens when an install is not completed and synaptic is exited. Usually its no more than that.

---

### Post by dhedrick on 2008-02-05
That worked - took me a minute to figure out that I needed to use sudo to make it work, but once I did, it worked.

Thanks for your help!

---

### Post by agim on 2008-02-05
Glad to hear it went well. Welcome to Ubuntu.

---

