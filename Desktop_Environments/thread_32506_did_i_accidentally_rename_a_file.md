---
title: "did i accidentally rename a file?"
date: 2005-05-08
forum: Desktop Environments
---

### Post by GOwin on 2005-05-08
I have a file named "[" in /usr

File properties contents indicate...

"ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV) for GNU/Linux 2.2.0, dynamically linked (uses shared libs), stripped"

---

### Post by JonahRowley on 2005-05-08
No.  [ is the **test** command in disguise.  Look in shell scripts and you'll see things like **if [ -e /some/file ]; then**, well that [ is not a syntax element, it's the [ command.

---

