---
title: "how can I patch nautilus?"
date: 2008-04-29
forum: Desktop Environments
---

### Post by ryu kun on 2008-04-29
Hi! I use Ubuntu 8.04. I want to install [this patch]("http://mail.gnome.org/archives/nautilus-list/2008-February/msg00082.html") to my Nautilus file manager to have multi-column view as explained [here]("http://blogs.gnome.org/cneumair/2008/02/17/new-column-wise-nautilus-view-user-data-backup-replay/").

Can you tell me how can I install a patch file (like "something.diff") to the Nautilus file manager?

---

### Post by Talorgan on 2008-05-18
I think I am in the same boat as ryu kun. If you download and unpack the proferred archive you are left with a file called:

nautilus-compact-icon-non-core.diff

... but what to do next is unclear.

---

### Post by gnivler on 2008-05-19
I'm no expert, but I think what you are looking for is 'patch', try 'man patch'.  You will likely need the source code and to figure out which source file(s) are to be patched, and on that note I'm not much help.

---

### Post by Talorgan on 2008-05-19
I'm even less of an expert but the contents of nautilus-compact-icon-non-core.diff look like what I'd imaging source code to look like!

---

### Post by aroch1 on 2008-05-20
It is source code, specifically, a *.diff file contains the difference between the original version of the source code and the version witht the feature you're looking for.  To patch nautilus you'd have to download the source code and recompile it.  Before compiling use ```
patch
``` to apply the patch you have.

---

