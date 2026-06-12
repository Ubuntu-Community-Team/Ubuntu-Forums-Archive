---
title: "How to change default forum font?"
date: 2007-09-27
forum: Forum Feedback &amp; Help
---

### Post by mysticmatrix on 2007-09-27
Can I change how the default forum fonts look?
There is a setting in Firefox but that changes fonts of all websites.

Part of problem started when I installed core fonts.

Any Help?

---

### Post by mysticmatrix on 2007-09-28
Bump, although if someone can tell me how to display core fonts with normal style rather than clear types, it would greatly help me.
I just checked in windows that if I use cleartypes, the fonts become as unreadable as they are now in ubuntu.

---

### Post by RAV TUX on 2007-09-30
> **mysticmatrix said:**
> Can I change how the default forum fonts look?
There is a setting in Firefox but that changes fonts of all websites.

Part of problem started when I installed core fonts.

Any Help?This might help you:

```
sudo dpkg-reconfigure fontconfig-config
```

disable bitmap font's

---

