---
title: "Source code for yes, true, false, etc."
date: 2009-05-14
forum: General Help
---

### Post by camper365 on 2009-05-14
Where can I find the source code to simple programs such as true, false, yes, ls, etc.
I have tried to find it in the coreutils source code, but that didn't have what I wanted.

---

### Post by mb_webguy on 2009-05-14
Many of those you name are shell functions, not programs.  So to see the source code, you'd have to look in the source of the shell.  You can get the bash source code [here]("http://www.gnu.org/software/bash/bash.html").

---

### Post by bab1 on 2009-05-15
Here is a guide to scripting in bash:
 [http://tldp.org/LDP/abs/html/]("http://tldp.org/LDP/abs/html/")

Or you can use perl.  Here is a guide for that:
[http://www.lies.com/begperl/]("http://www.lies.com/begperl/")

---

### Post by lloyd_b on 2009-05-15
> **camper365 said:**
> Where can I find the source code to simple programs such as true, false, yes, ls, etc.
I have tried to find it in the coreutils source code, but that didn't have what I wanted.

In a terminal window:```
apt-get source coreutils
cd coreutils*
tar -zxvf *.gz
cd coreutils*
cd src
```and "ls" should show you "true.c", "false.c", "yes.c", etc.

Note that "false.c" includes "true.c", just passes a #define to tell it to build differently.

Lloyd B.

---

### Post by camper365 on 2009-05-17
thx

---

