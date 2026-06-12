---
title: "krandrtray for debugging does not work."
date: 2009-02-06
forum: General Help
---

### Post by lagigliaivan on 2009-02-06
Hi All,

A few days ago I reported a bug in the kde application krandrtray. The executable file is stripped, so I had to install its version with debugging information which is included in kdebase-workspace-dbg_4.1.2-0ubuntu12_i386.deb package in order to send a backtrace.   

The new file is installed in /usr/lib/debug/usr/bin/krandrtray and although it seems to be an executable (according to the output of file command) it does not work. The error that I receive is:

bash: /usr/lib/debug/usr/bin/krandrtray: cannot execute binary file.

I have checked out the file permissions, but nothing seems to be wrong.

Somebody know something about it????

Thanks!!!

---

