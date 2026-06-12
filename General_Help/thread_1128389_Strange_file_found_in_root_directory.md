---
title: "Strange file found in root directory"
date: 2009-04-17
forum: General Help
---

### Post by richrock on 2009-04-17
I logged into my Ubuntu install (after a while with windows playing games) and found this:

-rw-------   1 root root 31903 2009-02-23 19:35 sqlsl5il4

No idea what this is, so can anyone shed any light on it?  I find it extremely suspicious as there are usually no files apart from some vmlinuz, etc...

I managed to open it as root using a text editor, and found it to be a mysql file, setting up some user privileges.  So my next question is, what is it for?

Perplexed,

Rich :(

---

### Post by danwood76 on 2009-04-17
It can probably be safely removed.
It could be a leftover from an install gone wrong or something, it may have been destined for the /tmp dir and so was not cleaned up after the install.

---

