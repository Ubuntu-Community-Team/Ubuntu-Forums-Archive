---
title: "Terminal + SHIFT_JIS + less = crashing"
date: 2009-01-06
forum: Desktop Environments
---

### Post by ralphmerridew on 2009-01-06
Be sure to save any open work before attempting this.

1) Open two Terminal windows.
2) Set the character encoding of one of them to SHIFT_JIS.
3) On that Terminal, type ```
perl -e 'print "\xec\x98\x8c";' > /tmp/bug; less /tmp/bug
```

All Terminal windows, and any program started by a Terminal window, will now crash.

The bug only seems to appear when running less from a file; if output of the program is piped directly to less, the bug won't manifest.

---

