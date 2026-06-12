---
title: "64bit or 32bit? How can you tell?"
date: 2009-01-12
forum: General Help
---

### Post by ZweeK on 2009-01-12
how do you know if you are running the 32bit or the 64 bit version of linux?

---

### Post by iaculallad on 2009-01-12
> **ZweeK said:**
> how do you know if you are running the 32bit or the 64 bit version of linux?

Open your terminal and issue the command below:

```
uname -m
```

i686 = 32-Bit
i86_64 = 64-Bit

---

### Post by bodhi.zazen on 2009-01-13
```
grep --color=always ' lm ' /proc/cpuinfo
```

Output == you have a 64 bit cpu

To see your OS,  use uname -a as above.

---

### Post by Slim Odds on 2009-01-13
> **ZweeK said:**
> how do you know if you are running the 32bit or the 64 bit version of linux?

You don't know which version you installed?

How do you get through the day?   :)

---

### Post by LoneWolfJack on 2009-01-13
> **Slim Odds said:**
> You don't know which version you installed?

How do you get through the day?   :)

Fair question. ;)

BTW, if you don't want to tangle with the command line, you can also open firefox, click help->about and look for the string where it says something like

> Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.0.5) Gecko/2008121623 Ubuntu/8.10 (intrepid) Firefox/3.0.5

x86_64 indicates a 64bit version

---

### Post by hivelocitydd on 2009-01-14
You need to use uname command, which prints system information including kernel version and whether kernel is 32 bit or 64 bit. You can also use less /proc/cpuinfo command determine if it is 64 bit cpu or not.

---

