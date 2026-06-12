---
title: "OOM killer"
date: 2005-11-10
forum: Desktop Environments
---

### Post by Knitter on 2005-11-10
Hello!
I was reading the man page of malloc function and found some reference to "OOM Killer".
Can anyone explain how does the OOM Killer work on ubuntu, does it has any diferent implementation or when it may happen.
Thanks.

---

### Post by Kyral on 2005-11-10
I vote this be moved to the Programming Forums

---

### Post by slux on 2005-11-10
Well, it's a kernel feature and works  the same across distros I believe. Basically when the system runs out of memory, the kernel tries to fix the situation by killing a process and chooses it on grounds that are less clear to me but memory usage is certainly one factor. It often misses and manages to kill processes that aren't relly related to the memory issue but eventually gets it right. :P

that's the simple, rather non-technical explanation, I don't know the exact details.

---

### Post by Kyral on 2005-11-10
Or that.

In a word: Don't worry about it

---

