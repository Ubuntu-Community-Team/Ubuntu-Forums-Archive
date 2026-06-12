---
title: "lpr/cups corrupted output for plain text"
date: 2009-11-11
forum: Desktop Environments
---

### Post by cw1035 on 2009-11-11
I am having a problem using lpr to print plain text files. If the text file has a tab or underscore, the following text is shifted left and overprinted the previous text. Examples:

9876543210_xxxxxxx,   _xxxxx is shifted left 4 positions, overwriting 3210

6543210\txxxxx,    xxxxxx is shifted left 5 positions, overwriting 10

I have a fresh install of 9.10, and am using a Brother HL-2140 printer. Any help would be appreciated.

---

### Post by jnorthr on 2009-11-11
i'd try to create a new document in open office with some tabs and try to print from there, just to see if's it's an lpr issue or a faulty printer driver.

---

### Post by cw1035 on 2009-11-11
> **jnorthr said:**
> i'd try to create a new document in open office with some tabs and try to print from there, just to see if's it's an lpr issue or a faulty printer driver.
These same text lines print fine from gedit, and I don't have any problems with printouts from any other programs. Also, if I use the "prettyprint" option, the underscored line prints out OK, but the tabs are still shifted. When I use "prettyprint" to print source code, the automatic bold text causes other overwrite problems.

---

### Post by cw1035 on 2009-11-11
Discovered that this is a know bug #365239 in launchpad.net for an HP laser printer. The work around is:
cat foo.txt | mpage -1 | lp

---

