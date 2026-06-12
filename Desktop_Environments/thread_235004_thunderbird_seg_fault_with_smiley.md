---
title: "thunderbird seg fault with smiley"
date: 2006-08-12
forum: Desktop Environments
---

### Post by &amp;)ky#)^ on 2006-08-12
I'm using Thunderbird and whenever I'm composing an e-mail, if I put in a smiley in the message via the smiley drop down menu and then hit the spacebar twice, I get a segfault.  What's up?  Anybody else have this?

Here are some different instances:

/usr/lib/mozilla-thunderbird/run-mozilla.sh: line 131: 11038 Segmentation fault      "$prog" ${1+"$@"}

DOUBLE-CLICK: 400 --> -1 THRESHOLD: 8 --> -1 /usr/lib/mozilla-thunderbird/run-mozilla.sh: line 131: 11285 Segmentation fault      "$prog" ${1+"$@"}

DOUBLE-CLICK: 400 --> -1 THRESHOLD: 8 --> -1 DOUBLE-CLICK: 400 --> -1 THRESHOLD: 8 --> -1 DOUBLE-CLICK: 400 --> -1 THRESHOLD: 8 --> -1 /usr/lib/mozilla-thunderbird/run-mozilla.sh: line 131: 11365 Segmentation fault      "$prog" ${1+"$@"}

Try it at home and see if you can do it, too.

I've already tried removing my profile (.mozilla-thunderbird) and I've already tried reinstalling the package.

---

### Post by &amp;)ky#)^ on 2006-08-12
I figured out exactly where the problem is occuring.  I ran
mozilla-thunderbird -g to use gdb to debug it.  I reproduced the error
and it gave me this:

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread 46912549399280 (LWP 12036)]
0x00002aaab539e34f in NSGetModule ()
   from /usr/lib/mozilla-thunderbird/components/libspellchecker.so

That surprised me.  So, I went into thunderbird and I turned off the
spell check option "check as you type" and sure enough, I couldn't
reproduce the error.  I could spell check it by clicking the spell
check button with a problem.  So, the bug is effectively due to the
check as you type feature.

---

