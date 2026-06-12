---
title: "can't install packages"
date: 2006-01-22
forum: Desktop Environments
---

### Post by Aramil on 2006-01-22
When I try to install a .tar.gz package I do ./configure but when i do make it pops the message

make: *** No targets specified and no makefile found.  Stop.

Any ideas?

---

### Post by public_void on 2006-01-22
That is cause by the ./configure not completing. When you go ./configure look at the last couple of lines of output, it will be listing reasons it couldn't complete. Its possible that the program your installing needs some dependencies (possibly up dating old ones). Post back with the output if you need help.

---

### Post by aysiu on 2006-01-22
1. Any reason you're installing a .tar.gz? Are you sure you can't just apt-get install it?

2. Do you have *build-essential* already installed?

3. What's the name of the package?

---

### Post by Aramil on 2006-01-24
Well i found the problem.There were some dependencies missing!thx

---

