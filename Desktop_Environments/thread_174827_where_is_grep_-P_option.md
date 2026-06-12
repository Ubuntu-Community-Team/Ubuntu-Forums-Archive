---
title: "where is grep -P option?"
date: 2006-05-12
forum: Desktop Environments
---

### Post by hsp90 on 2006-05-12
I am new to Ubuntu and I installed the dapper beta2 on my laptop. However the grep -P option for perl style regex, although appear in man pages, is not supported by the command itself. When type grep -P pattern file, it says the "grep: The -P option is not supported". Is this a bug or grep in Ubuntu never has -P option? The option seems to be supported by almost all the other distributions I tried.

Hsp90

---

### Post by jrib on 2006-05-12
A bug is already on malone about it, [https://launchpad.net/distros/ubuntu/+source/grep/+bug/15051](https://launchpad.net/distros/ubuntu/+source/grep/+bug/15051)

---

### Post by hsp90 on 2006-05-12
After some digging into the grep source code, the problem is caused by compiling grep without installing the libpcre-dev package, after I install the package and recompile grep, the -P begin to work.

---

### Post by xinelo on 2006-10-23
hsp90, could you explain how you recompiled grep? 

thank you very much, xinelo

---

